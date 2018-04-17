---
title: Tworzenie formantu użytkownika obsługującego proste powiązanie danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: edfa94a6ca1bdc4fc8a5e9353505da4354b126ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Tworzenie formantu użytkownika formularzy systemu Windows obsługującego proste powiązanie danych
Wyświetlanie danych w formularzach w aplikacjach systemu Windows, można wybrać istniejących formantów z **przybornika**, lub jeśli aplikacja wymaga funkcji, które nie jest dostępna w standardowych kontrolek, mogą tworzyć niestandardowe kontrolki. W tym przewodniku przedstawiono sposób tworzenia formant, który implementuje <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Określa, które implementują <xref:System.ComponentModel.DefaultBindingPropertyAttribute> może zawierać jedną właściwość, która może być powiązana z danymi. Takie kontrolki są podobne do <xref:System.Windows.Forms.TextBox> lub <xref:System.Windows.Forms.CheckBox>.  
  
 Aby uzyskać więcej informacji o kontroli, zobacz [opracowywanie formantów formularzy systemu Windows w czasie projektowania](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).  
  
 Podczas tworzenia formantów w scenariuszach wiązania danych, powinny implementować jeden z następujących atrybutów wiązania z danymi:  
  
|Użycie atrybutu powiązanie danych|  
|-----------------------------------|  
|Wdrożenie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> prostych kontrolek, takich jak <xref:System.Windows.Forms.TextBox>, który jednej kolumny (lub wyświetlić właściwości) danych. (Ten proces jest opisany na tej stronie wskazówki).|  
|Wdrożenie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> formantów, takich jak <xref:System.Windows.Forms.DataGridView>, który wyświetlenia listy (lub tabele) danych. Aby uzyskać więcej informacji, zobacz [Tworzenie formantu użytkownika formularzy systemu Windows obsługującego złożone powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementowanie <xref:System.ComponentModel.LookupBindingPropertiesAttribute> formantów, takich jak <xref:System.Windows.Forms.ComboBox>, który wyświetlenia listy lub tabele danych, ale również musi przedstawiać pojedyncza kolumna lub właściwości. Aby uzyskać więcej informacji, zobacz [Tworzenie formantu użytkownika formularzy systemu Windows, który obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 W tym przewodniku tworzy prosty formant, który wyświetla dane z pojedynczej kolumny w tabeli. W tym przykładzie użyto `Phone` kolumny `Customers` tabeli na podstawie przykładowej bazy danych Northwind. Proste użytkownika kontrolka będzie wyświetlać numery telefonów klientów w standardowym formacie numeru telefonu, za pomocą <xref:System.Windows.Forms.MaskedTextBox> i ustawienie maski numeru telefonu.  
  
 W tym przewodniku przedstawiono sposób:  
  
-   Utwórz nową **aplikacji Windows Forms**.  
  
-   Dodaj nową **kontrolki użytkownika** do projektu.  
  
-   Wizualne projektowanie kontrolki użytkownika.  
  
-   Implementowanie `DefaultBindingProperty` atrybutu.  
  
-   Utwórz zestaw danych o **konfiguracji źródła danych** kreatora.  
  
-   Ustaw **Phone** kolumny w **źródeł danych** okno, aby użyć nowego formantu.  
  
-   Tworzenie formularza do wyświetlania danych w nowej kontrolki.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
W tym przewodniku zastosowano programu SQL Server Express LocalDB i przykładowej bazy danych Northwind.  
  
1.  Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [strony pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalator programu Visual Studio**. W Instalatorze programu Visual Studio, można zainstalować jako część programu SQL Server Express LocalDB **magazynu danych i przetwarzania** obciążenia, lub jako poszczególnych składników.  
  
2.  Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:  

    1. W programie Visual Studio Otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **magazynu danych i przetwarzania** obciążenia w Instalatorze programu Visual Studio.) Rozwiń węzeł **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w wystąpieniu bazy danych LocalDB, a następnie wybierz **nowej kwerendy...** .  

       Zostanie otwarte okno edytora zapytań.  

    2. Kopiuj [skryptu języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL utworzy bazę danych Northwind od początku i wypełnia danych.  

    3. Wkleić skryptu T-SQL w edytorze zapytań, a następnie wybierz pozycję **Execute** przycisku.  

       Po pewnym czasie zapytanie kończy wykonywanie i utworzeniu bazy danych Northwind.  
  
## <a name="create-a-windows-forms-application"></a>Tworzenie aplikacji Windows Forms  
 Pierwszym krokiem jest utworzenie **aplikacji Windows Forms**.  
  
#### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt dla systemu Windows  
  
1. W programie Visual Studio na **pliku** menu, wybierz opcję **nowy**, **projektu...** .  
  
2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, następnie wybierz **Windows Desktop klasycznego**.  

3. W środkowym okienku wybierz **aplikacji formularzy systemu Windows** typu projektu.  

4. Nazwij projekt **SimpleControlWalkthrough**, a następnie wybierz pozycję **OK**. 
  
     **SimpleControlWalkthrough** projektu jest tworzony i dodane do **Eksploratora rozwiązań**.  
  
## <a name="add-a-user-control-to-the-project"></a>Dodaj kontrolkę użytkownika do projektu  
 W tym przewodniku tworzy proste powiązania danych formantu **kontrolki użytkownika**, dodać **kontrolki użytkownika** elementu do **SimpleControlWalkthrough** projektu.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Aby dodać kontrolkę użytkownika do projektu  
  
1.  Z **projektu** menu, wybierz **Dodaj kontrolkę użytkownika**.  
  
2.  Typ `PhoneNumberBox` obszaru nazw, a następnie kliknij polecenie **Dodaj**.  
  
     **PhoneNumberBox** formant został dodany do **Eksploratora rozwiązań**i zostanie otwarty w projektancie.  
  
## <a name="design-the-phonenumberbox-control"></a>Projekt kontroli PhoneNumberBox  
 W tym przewodniku rozszerza istniejący <xref:System.Windows.Forms.MaskedTextBox> utworzyć `PhoneNumberBox` formantu.  
  
#### <a name="to-design-the-phonenumberbox-control"></a>Projekt kontroli PhoneNumberBox  
  
1.  Przeciągnij <xref:System.Windows.Forms.MaskedTextBox> z **przybornika** na powierzchnię projektu kontrolki użytkownika.  
  
2.  Wybierz tagów inteligentnych na <xref:System.Windows.Forms.MaskedTextBox> możesz po prostu przeciągnąć i wybierz polecenie **ustawić maski**.  
  
3.  Wybierz **numer telefonu** w **maska wprowadzania** okno dialogowe, a następnie kliknij przycisk **OK** można ustawić maski.  
  
## <a name="add-the-required-data-binding-attribute"></a>Dodaj wymagany atrybut wiązania danych  
 Implementowanie prostego formantów tego wiązania z danymi pomocy technicznej, <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  
  
#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>Aby zaimplementować atrybutu DefaultBindingProperty  
  
1.  Przełącznik `PhoneNumberBox` formantu do widoku kodu. (Na **widoku** menu, wybierz **kodu**.)  
  
2.  Zastąp kod w `PhoneNumberBox` następującym kodem:  
  
     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]  
  
3.  Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
## <a name="create-a-data-source-from-your-database"></a>Utwórz źródło danych z bazy danych  
 Ten krok używa **konfiguracji źródła danych**kreatora, aby utworzyć źródło danych na podstawie `Customers` tabeli w bazie danych Northwind. Musi mieć dostęp do przykładowej bazy danych Northwind do utworzenia połączenia. Aby uzyskać informacje na temat konfigurowania przykładowej bazy danych Northwind, zobacz [porady: Instalowanie przykładowe bazy danych](../data-tools/installing-database-systems-tools-and-samples.md).  
  
#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych  
  
1.  Na **danych** menu, kliknij przycisk **Pokaż źródeł danych**.  
  
2.  W **źródeł danych** wybierz **Dodaj nowe źródło danych** uruchomić **konfiguracji źródła danych** kreatora.  
  
3.  Na **wybierz typ źródła danych** wybierz pozycję **bazy danych**, a następnie kliknij przycisk **dalej**.  
  
4.  Na **wybierz połączenie danych** wykonaj jedną z następujących czynności:  
  
    -   Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.  
  
    -   Wybierz **nowe połączenie** można uruchomić **połączenia Dodawanie i modyfikowanie** okno dialogowe.  
  
5.  Jeśli baza danych wymaga hasła, wybierz opcję, aby obejmować dane poufne, a następnie kliknij przycisk **dalej**.  
  
6.  Na **zapisać parametry połączenia w pliku konfiguracji aplikacji** kliknij przycisk **dalej**.  
  
7.  Na **wybierz obiekty bazy danych** rozwiń pozycję **tabel** węzła.  
  
8.  Wybierz `Customers` tabeli, a następnie kliknij przycisk **Zakończ**.  
  
     **NorthwindDataSet** zostanie dodany do projektu i `Customers` tabela pojawi się w **źródeł danych** okna.  
  
## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Ustaw kolumnę phone formantu PhoneNumberBox  
 W ramach **źródeł danych** okna, można ustawić formantu do utworzenia przed przeciąganie elementów na formularzu.  
  
#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>Aby ustawić kolumny telefonu, aby powiązać z formantem PhoneNumberBox  
  
1.  Otwórz **Form1** w projektancie.  
  
2.  Rozwiń węzeł **klientów** w węźle **źródeł danych** okna.  
  
3.  Kliknij strzałkę listy rozwijanej w **klientów** węzeł i wybierz polecenie **szczegóły** z listy kontroli.  
  
4.  Kliknij strzałkę listy rozwijanej w **Phone** kolumny i wybierz polecenie **Dostosuj**.  
  
5.  Wybierz **PhoneNumberBox** z listy **skojarzonych formantów** w **opcji dostosowania danych interfejsu użytkownika** okno dialogowe.  
  
6.  Kliknij strzałkę listy rozwijanej w **Phone** kolumny i wybierz polecenie **PhoneNumberBox**.  
  
## <a name="add-controls-to-the-form"></a>Dodawanie formantów do formularza  
 Formanty powiązane z danymi można utworzyć, przeciągając elementy z **źródeł danych** okna na formularzu.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Aby utworzyć formantów powiązanych z danymi  
  
-   Przeciągnij głównym **klientów** węzła z **źródeł danych** okna na formularzu i sprawdź, czy `PhoneNumberBox` kontroli jest używana do wyświetlania danych w `Phone` kolumny.  
  
     Formanty powiązane z danymi z opisowe etykiety są wyświetlane w formularzu, wraz z paska narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania rekordów. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane na pasku składnika.  
  
## <a name="run-the-application"></a>Uruchamianie aplikacji  
  
#### <a name="to-run-the-application"></a>Aby uruchomić aplikację  
  
-   Naciśnij klawisz F5, aby uruchomić aplikację.  
  
## <a name="next-steps"></a>Następne kroki  
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po Tworzenie formantu, który obsługuje powiązanie danych. Niektóre typowe następne kroki obejmują:  
  
-   Umieszczanie Kontrolki niestandardowe w bibliotece kontroli, więc można używać ich w innych aplikacjach.  
  
-   Tworzenie formantów, które obsługują bardziej złożonymi scenariuszami powiązania danych. Aby uzyskać więcej informacji, zobacz [Tworzenie formantu użytkownika formularzy systemu Windows obsługującego złożone powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) i [Tworzenie formantu użytkownika formularzy systemu Windows, który obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
