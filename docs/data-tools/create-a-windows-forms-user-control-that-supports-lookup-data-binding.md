---
title: W powiązaniu danych - formanty formularzy systemu Windows przy użyciu tabel odnośników | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 560d19c8efeaa6c1cf206bcb40fa0b11347b4217
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746523"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Tworzenie formantu użytkownika formularzy systemu Windows, który obsługuje powiązanie danych wyszukiwania
Wyświetlanie danych w formularzach systemu Windows, można wybrać istniejących formantów z **przybornika**, lub jeśli aplikacja wymaga funkcji niedostępnych w standardowych kontrolek, mogą tworzyć niestandardowe kontrolki. W tym przewodniku przedstawiono sposób tworzenia formant, który implementuje <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Określa, które implementują <xref:System.ComponentModel.LookupBindingPropertiesAttribute> może zawierać trzech właściwości, które można powiązać z danymi. Takie kontrolki są podobne do <xref:System.Windows.Forms.ComboBox>.

 Aby uzyskać więcej informacji o kontroli, zobacz [opracowywanie formantów formularzy systemu Windows w czasie projektowania](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

 Podczas tworzenia formantów w scenariuszach wiązania danych należy implementować jeden z następujących atrybutów wiązania z danymi:

|Użycie atrybutu powiązanie danych|
|-----------------------------------|
|Wdrożenie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> prostych kontrolek, takich jak <xref:System.Windows.Forms.TextBox>, który jednej kolumny (lub wyświetlić właściwości) danych. Aby uzyskać więcej informacji, zobacz [Tworzenie formantu użytkownika formularzy systemu Windows obsługującego proste powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Wdrożenie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> formantów, takich jak <xref:System.Windows.Forms.DataGridView>, który wyświetlenia listy (lub tabele) danych. Aby uzyskać więcej informacji, zobacz [Tworzenie formantu użytkownika formularzy systemu Windows obsługującego złożone powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementowanie <xref:System.ComponentModel.LookupBindingPropertiesAttribute> formantów, takich jak <xref:System.Windows.Forms.ComboBox>, wyświetlania list lub tabele danych, ale również musi przedstawiać pojedyncza kolumna lub właściwości. (Ten proces jest opisany na tej stronie wskazówki).|

 W tym przewodniku tworzy kontrolkę wyszukiwania, która tworzy powiązanie z danymi z dwóch tabel. W tym przykładzie użyto `Customers` i `Orders` tabele w bazie danych Northwind. Formant wyszukiwania zostanie powiązany `CustomerID` pola `Orders` tabeli. Ta wartość zostanie użyty do wyszukania `CompanyName` z `Customers` tabeli.

 W tym przewodniku przedstawiono sposób:

-   Utwórz nową **aplikacji Windows Forms**.

-   Dodaj nową **kontrolki użytkownika** do projektu.

-   Wizualne projektowanie kontrolki użytkownika.

-   Implementowanie `LookupBindingProperty` atrybutu.

-   Utwórz zestaw danych o **konfiguracji źródła danych** kreatora.

-   Ustaw **CustomerID** kolumny na **zamówień** tabeli w **źródeł danych** okno, aby użyć nowego formantu.

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

2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, następnie wybierz **Windows Desktop**.

3. W środkowym okienku wybierz **aplikacji formularzy systemu Windows** typu projektu.

4. Nazwij projekt **LookupControlWalkthrough**, a następnie wybierz pozycję **OK**.

     **LookupControlWalkthrough** projektu jest tworzony i dodane do **Eksploratora rozwiązań**.

## <a name="add-a-user-control-to-the-project"></a>Dodaj kontrolkę użytkownika do projektu
 Ten przewodnik utworzy formant wyszukiwania z **kontrolki użytkownika**, dodać **kontrolki użytkownika** elementu do **LookupControlWalkthrough** projektu.

#### <a name="to-add-a-user-control-to-the-project"></a>Aby dodać kontrolkę użytkownika do projektu

1.  Z **projektu** menu, wybierz opcję **Dodaj kontrolkę użytkownika**.

2.  Typ `LookupBox` w **nazwa** obszaru, a następnie kliknij przycisk **Dodaj**.

     **LookupBox** formant został dodany do **Eksploratora rozwiązań**i zostanie otwarty w projektancie.

## <a name="design-the-lookupbox-control"></a>Projekt kontroli LookupBox

#### <a name="to-design-the-lookupbox-control"></a>Projekt kontroli LookupBox

-   Przeciągnij <xref:System.Windows.Forms.ComboBox> z **przybornika** na powierzchnię projektu kontrolki użytkownika.

## <a name="add-the-required-data-binding-attribute"></a>Dodaj wymagany atrybut wiązania danych
 Wyszukiwanie formantów tego wiązania danych pomocy technicznej, można zaimplementować <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.

#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>Aby zaimplementować atrybutu LookupBindingProperties

1.  Przełącznik **LookupBox** formantu do widoku kodu. (Na **widoku** menu, wybierz **kodu**.)

2.  Zastąp kod w `LookupBox` następującym kodem:

     [!code-vb[VbRaddataDisplaying#5](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.vb)]
     [!code-csharp[VbRaddataDisplaying#5](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-lookup-data-binding_1.cs)]

3.  Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

## <a name="create-a-data-source-from-your-database"></a>Utwórz źródło danych z bazy danych
Spowoduje to utworzenie źródła danych przy użyciu **konfiguracji źródła danych**kreatora, na podstawie `Customers` i `Orders` tabele w bazie danych Northwind.

#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1.  Na **danych** menu, kliknij przycisk **Pokaż źródeł danych**.

2.  W **źródeł danych** wybierz **Dodaj nowe źródło danych** uruchomić **konfiguracji źródła danych** kreatora.

3.  Wybierz **bazy danych** na **wybierz typ źródła danych** , a następnie kliknij przycisk **dalej**.

4.  Na **wybierz połączenie danych** wykonaj jedną z następujących czynności:

    -   Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

    -   Wybierz **nowe połączenie** można uruchomić **połączenia Dodawanie i modyfikowanie** okno dialogowe.

5.  Jeśli baza danych wymaga hasła, wybierz opcję, aby obejmować dane poufne, a następnie kliknij przycisk **dalej**.

6.  Na **zapisać parametry połączenia w pliku konfiguracji aplikacji** kliknij przycisk **dalej**.

7.  Na **wybierz obiekty bazy danych** rozwiń pozycję **tabel** węzła.

8.  Wybierz `Customers` i `Orders` tabel, a następnie kliknij przycisk **Zakończ**.

     **NorthwindDataSet** zostanie dodany do projektu i `Customers` i `Orders` tabele są wyświetlane w **źródeł danych** okna.

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Zestawu kolumn CustomerID tabeli zamówienia, aby używać formantu LookupBox
 W ramach **źródeł danych** okna, można ustawić formantu do utworzenia przed przeciąganie elementów na formularzu.

#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>Aby ustawić kolumny CustomerID, aby powiązać z formantem LookupBox

1.  Otwórz **Form1** w projektancie.

2.  Rozwiń węzeł **klientów** w węźle **źródeł danych** okna.

3.  Rozwiń węzeł **zamówień** węzeł (w **klientów** poniżej węzła **faksów** kolumny).

4.  Kliknij strzałkę listy rozwijanej w **zamówień** węzeł i wybierz polecenie **szczegóły** z listy kontroli.

5.  Kliknij strzałkę listy rozwijanej w **CustomerID** kolumny (w **zamówień** węzła) i wybierz polecenie **Dostosuj**.

6.  Wybierz **LookupBox** z listy **skojarzonych formantów** w **opcji dostosowania danych interfejsu użytkownika** okno dialogowe.

7.  Kliknij przycisk **OK**.

8.  Kliknij strzałkę listy rozwijanej w **CustomerID** kolumny i wybierz polecenie **LookupBox**.

## <a name="add-controls-to-the-form"></a>Dodawanie formantów do formularza
 Formanty powiązane z danymi można utworzyć, przeciągając elementy z **źródeł danych** okna na **Form1**.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Aby utworzyć formantów powiązanych z danymi w formularzu systemu Windows

-   Przeciągnij **zamówień** węzła z **źródeł danych** okna na formularzu systemu Windows i sprawdź, czy **LookupBox** kontroli jest używana do wyświetlania danych w `CustomerID` kolumna.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Powiązywanie formantu do odszukania NazwaFirmy z tabeli Klienci

#### <a name="to-setup-the-lookup-bindings"></a>Można skonfigurować powiązania wyszukiwania

-   Wybierz główny **klientów** w węźle **źródeł danych** okna, a następnie przeciągnij pole na pole kombi w **CustomerIDLookupBox** na **Form1** .

     Powoduje to skonfigurowanie wiązania danych do wyświetlenia `CompanyName` z `Customers` tabeli przy zachowaniu `CustomerID` wartość z `Orders` tabeli.

## <a name="running-the-application"></a>Uruchamianie aplikacji

#### <a name="to-run-the-application"></a>Aby uruchomić aplikację

-   Naciśnij klawisz F5, aby uruchomić aplikację.

-   Przejdź przez niektóre rekordy i sprawdź, czy `CompanyName` pojawia się w `LookupBox` formantu.

## <a name="see-also"></a>Zobacz też

- [Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)