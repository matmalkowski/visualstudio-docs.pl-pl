---
title: Tworzenie formantu użytkownika formularzy systemu Windows z powiązanie danych
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4a1922c3b79a718b3a239280561bf954165332e6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Tworzenie formantu użytkownika formularzy systemu Windows obsługującego złożone powiązanie danych

Wyświetlanie danych w formularzach w aplikacjach systemu Windows, można wybrać istniejących formantów z **przybornika**, lub jeśli aplikacja wymaga funkcji, które nie jest dostępna w standardowych kontrolek, mogą tworzyć niestandardowe kontrolki. W tym przewodniku przedstawiono sposób tworzenia formant, który implementuje <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Określa, które implementują <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> zawierają `DataSource` i `DataMember` właściwości, które mogą być powiązane z danymi. Takie kontrolki są podobne do <xref:System.Windows.Forms.DataGridView> lub <xref:System.Windows.Forms.ListBox>.

Aby uzyskać więcej informacji o kontroli, zobacz [opracowywanie formantów formularzy systemu Windows w czasie projektowania](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Podczas tworzenia formantów w scenariuszach wiązania danych należy implementować jeden z następujących atrybutów wiązania z danymi:

|Użycie atrybutu powiązanie danych|
|-----------------------------------|
|Wdrożenie <xref:System.ComponentModel.DefaultBindingPropertyAttribute> prostych kontrolek, takich jak <xref:System.Windows.Forms.TextBox>, który jednej kolumny (lub wyświetlić właściwości) danych. Aby uzyskać więcej informacji, zobacz [Tworzenie formantu użytkownika formularzy systemu Windows obsługującego proste powiązanie danych](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Wdrożenie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> formantów, takich jak <xref:System.Windows.Forms.DataGridView>, który wyświetlenia listy (lub tabele) danych. (Ten proces jest opisany na tej stronie wskazówki).|
|Implementowanie <xref:System.ComponentModel.LookupBindingPropertiesAttribute> formantów, takich jak <xref:System.Windows.Forms.ComboBox>, który wyświetlenia listy lub tabele danych, ale również musi przedstawiać pojedyncza kolumna lub właściwości. Aby uzyskać więcej informacji, zobacz [Tworzenie formantu użytkownika formularzy systemu Windows, który obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 W tym przewodniku tworzy złożonych formant, który wyświetla wiersze danych z tabeli. W tym przykładzie użyto `Customers` tabeli na podstawie przykładowej bazy danych Northwind. Kontrola użytkownika złożonych wyświetli tabeli Klienci w <xref:System.Windows.Forms.DataGridView> w kontrolki niestandardowej.

W tym przewodniku przedstawiono sposób:

- Utwórz nową **aplikacji Windows Forms**.

- Dodaj nową **kontrolki użytkownika** do projektu.

- Wizualne projektowanie kontrolki użytkownika.

- Implementowanie `ComplexBindingProperty` atrybutu.

- Utwórz zestaw danych o [Kreator konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png).

- Ustaw **klientów** tabeli w [Data Sources — okno](add-new-data-sources.md) do użycia nowego formantu złożonego.

- Dodaj nowy formant przeciągając je z **Data Sources — okno** na **Form1**.

## <a name="prerequisites"></a>Wymagania wstępne

W tym przewodniku zastosowano programu SQL Server Express LocalDB i przykładowej bazy danych Northwind.

1. Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [strony pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalator programu Visual Studio**. W Instalatorze programu Visual Studio, można zainstalować jako część programu SQL Server Express LocalDB **magazynu danych i przetwarzania** obciążenia, lub jako poszczególnych składników.

1. Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio Otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **magazynu danych i przetwarzania** obciążenia w Instalatorze programu Visual Studio.) Rozwiń węzeł **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w wystąpieniu bazy danych LocalDB, a następnie wybierz **nowej kwerendy...** .

       Zostanie otwarte okno edytora zapytań.

    1. Kopiuj [skryptu języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL utworzy bazę danych Northwind od początku i wypełnia danych.

    1. Wkleić skryptu T-SQL w edytorze zapytań, a następnie wybierz pozycję **Execute** przycisku.

       Po pewnym czasie zapytanie kończy wykonywanie i utworzeniu bazy danych Northwind.

## <a name="create-a-windows-forms-application"></a>Tworzenie aplikacji formularzy systemu Windows

 Pierwszym krokiem jest utworzenie **aplikacji Windows Forms**.

### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt dla systemu Windows

1. W programie Visual Studio na **pliku** menu, wybierz opcję **nowy**, **projektu...** .

1. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, następnie wybierz **Windows Desktop klasycznego**.

1. W środkowym okienku wybierz **aplikacji formularzy systemu Windows** typu projektu.

1. Nazwij projekt **ComplexControlWalkthrough**, a następnie wybierz pozycję **OK**.

    **ComplexControlWalkthrough** projektu jest tworzony i dodane do **Eksploratora rozwiązań**.

## <a name="add-a-user-control-to-the-project"></a>Dodaj kontrolkę użytkownika do projektu

Ponieważ w tym przewodniku tworzy kontrolkę można powiązać danych złożonych z **kontrolki użytkownika**, należy dodać **kontrolki użytkownika** elementu do projektu.

### <a name="to-add-a-user-control-to-the-project"></a>Aby dodać kontrolkę użytkownika do projektu

1. Z **projektu** menu, wybierz **Dodaj kontrolkę użytkownika**.

1. Typ **ComplexDataGridView** w **nazwa** obszaru, a następnie kliknij przycisk **Dodaj**.

    **ComplexDataGridView** formant został dodany do **Eksploratora rozwiązań**i zostanie otwarty w projektancie.

## <a name="design-the-complexdatagridview-control"></a>Projekt kontroli ComplexDataGridView

Ten krok powoduje dodanie <xref:System.Windows.Forms.DataGridView> do kontrolki użytkownika.

### <a name="to-design-the-complexdatagridview-control"></a>Projekt kontroli ComplexDataGridView

- Przeciągnij <xref:System.Windows.Forms.DataGridView> z **przybornika** na powierzchnię projektu kontrolki użytkownika.

## <a name="add-the-required-data-binding-attribute"></a>Dodaj wymagany atrybut wiązania danych

Złożone formantów tego wiązania danych pomocy technicznej, można zaimplementować <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.

### <a name="to-implement-the-complexbindingproperties-attribute"></a>Aby zaimplementować atrybutu ComplexBindingProperties

1. Przełącznik **ComplexDataGridView** formantu do widoku kodu. (Na **widoku** menu, wybierz opcję **kodu**.)

1. Zastąp kod w `ComplexDataGridView` następującym kodem:

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. Z **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

## <a name="creating-a-data-source-from-your-database"></a>Tworzenie źródła danych z bazy danych

Ten krok używa **konfiguracji źródła danych** kreatora, aby utworzyć źródło danych na podstawie `Customers` tabeli w bazie danych Northwind.

### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1.  Na **danych** menu, kliknij przycisk **Pokaż źródeł danych**.

2.  W **źródeł danych** wybierz **Dodaj nowe źródło danych** uruchomić **konfiguracji źródła danych** kreatora.

3.  Wybierz **bazy danych** na **wybierz typ źródła danych** , a następnie kliknij przycisk **dalej**.

4.  Na **wybierz połączenie danych** wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

    - Wybierz **nowe połączenie** można uruchomić **połączenia Dodawanie i modyfikowanie** okno dialogowe.

5.  Jeśli baza danych wymaga hasła, wybierz opcję, aby obejmować dane poufne, a następnie kliknij przycisk **dalej**.

6.  Na **zapisać parametry połączenia w pliku konfiguracji aplikacji** kliknij przycisk **dalej**.

7.  Na **wybierz obiekty bazy danych** rozwiń pozycję **tabel** węzła.

8.  Wybierz `Customers` tabeli, a następnie kliknij przycisk **Zakończ**.

    **NorthwindDataSet** zostanie dodany do projektu i `Customers` tabela pojawi się w **źródeł danych** okna.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Ustaw tabeli klientów do korzystania z formantu ComplexDataGridView

W ramach **źródeł danych** okna, można ustawić formantu do utworzenia przed przeciąganie elementów na formularzu.

### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Aby ustawić tabeli klientów, aby powiązać z formantem ComplexDataGridView

1. Otwórz **Form1** w projektancie.

1. Rozwiń węzeł **klientów** w węźle **źródeł danych** okna.

1. Kliknij strzałkę listy rozwijanej w **klientów** węzeł i wybierz polecenie **Dostosuj**.

1. Wybierz **ComplexDataGridView** z listy **skojarzonych formantów** w **opcji dostosowania danych interfejsu użytkownika** okno dialogowe.

1. Kliknij strzałkę listy rozwijanej w `Customers` tabeli, a następnie wybierz pozycję **ComplexDataGridView** z listy kontroli.

## <a name="add-controls-to-the-form"></a>Dodawanie formantów do formularza

Formanty powiązane z danymi można utworzyć, przeciągając elementy z **źródeł danych** okna na formularzu.

### <a name="to-create-data-bound-controls-on-the-form"></a>Aby utworzyć formantów powiązanych z danymi

Przeciągnij głównym **klientów** węzła z **źródeł danych** okna na formularzu. Sprawdź, czy **ComplexDataGridView** kontroli jest używana do wyświetlania danych tabeli.

## <a name="running-the-application"></a>Uruchamianie aplikacji

### <a name="to-run-the-application"></a>Aby uruchomić aplikację

Naciśnij klawisz F5, aby uruchomić aplikację.

## <a name="next-steps"></a>Następne kroki

Istnieje kilka kroków, które można wykonać po Tworzenie formantu, który obsługuje wiązania danych, w zależności od wymagań aplikacji. Niektóre typowe następne kroki obejmują:

- Umieszczanie Kontrolki niestandardowe w bibliotece kontroli, więc można używać ich w innych aplikacjach.

- Tworzenie formantów, które obsługują scenariusze wyszukiwania. Aby uzyskać więcej informacji, zobacz [Tworzenie formantu użytkownika formularzy systemu Windows, który obsługuje powiązanie danych wyszukiwania](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Zobacz także

- [Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Kontrolki formularzy Windows Forms](/dotnet/framework/winforms/controls/index)