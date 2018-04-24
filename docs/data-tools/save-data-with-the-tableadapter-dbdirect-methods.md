---
title: Zapisz dane z TableAdapter DBDirect metody
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: aae296898bfcddfa451875fe78b29f2ae95fc9df
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Zapisz dane z TableAdapter DBDirect metody
Ten przewodnik zawiera szczegółowe instrukcje na temat uruchamiania instrukcji SQL bezpośrednio na bazie danych za pomocą metod TableAdapter DBDirect. Metody TableAdapter DBDirect Podaj poprawnie poziom kontroli nad aktualizacje bazy danych. Można je do uruchomienia określonej instrukcji SQL i zapisanych procedur wywołując poszczególne `Insert`, `Update`, i `Delete` metody odpowiednio do potrzeb aplikacji (zamiast zastąpionej `Update` metodę, która wykonuje AKTUALIZACJĘ INSERT i DELETE instrukcje wszystko w jednym wywołaniu).

 W tym przewodniku przedstawiono sposób:

-   Utwórz nową **aplikacji Windows Forms**.

-   Tworzenie i konfigurowanie zestaw danych o [Kreator konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png).

-   Wybierz kontrolkę, która ma zostać utworzony w formularzu, gdy przeciąganie elementów z **źródeł danych** okna. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Tworzenie formularza powiązane z danymi, przeciągając elementy z **źródeł danych** okna na formularzu.

-   Dodaj metody bezpośrednio dostęp do bazy danych i wykonywać operacji wstawiania, aktualizacji i usunięć.

## <a name="prerequisites"></a>Wymagania wstępne
W tym przewodniku zastosowano programu SQL Server Express LocalDB i przykładowej bazy danych Northwind.

1.  Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [strony pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalator programu Visual Studio**. W Instalatorze programu Visual Studio, można zainstalować jako część programu SQL Server Express LocalDB **magazynu danych i przetwarzania** obciążenia, lub jako poszczególnych składników.

2.  Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio Otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **magazynu danych i przetwarzania** obciążenia w Instalatorze programu Visual Studio.) Rozwiń węzeł **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w wystąpieniu bazy danych LocalDB, a następnie wybierz **nowej kwerendy...** .

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptu języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL utworzy bazę danych Northwind od początku i wypełnia danych.

    3. Wkleić skryptu T-SQL w edytorze zapytań, a następnie wybierz pozycję **Execute** przycisku.

       Po pewnym czasie zapytanie kończy wykonywanie i utworzeniu bazy danych Northwind.

## <a name="create-a-windows-forms-application"></a>Tworzenie aplikacji formularzy systemu Windows
 Pierwszym krokiem jest utworzenie **aplikacji Windows Forms**.

#### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt dla systemu Windows

1. W programie Visual Studio na **pliku** menu, wybierz opcję **nowy**, **projektu...** .

2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, następnie wybierz **Windows Desktop klasycznego**.

3. W środkowym okienku wybierz **aplikacji formularzy systemu Windows** typu projektu.

4. Nazwij projekt **TableAdapterDbDirectMethodsWalkthrough**, a następnie wybierz pozycję **OK**.

     **TableAdapterDbDirectMethodsWalkthrough** projektu jest tworzony i dodawany do **Eksploratora rozwiązań**.

## <a name="create-a-data-source-from-your-database"></a>Utwórz źródło danych z bazy danych
 Ten krok używa **Kreator konfiguracji źródła danych** tworzenia źródła danych na podstawie `Region` tabeli w bazie danych Northwind. Musi mieć dostęp do przykładowej bazy danych Northwind do utworzenia połączenia. Aby uzyskać informacje dotyczące konfigurowania przykładowej bazy danych Northwind, zobacz [porady: Instalowanie przykładowe bazy danych](../data-tools/installing-database-systems-tools-and-samples.md).

#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1.  Na **danych** menu, wybierz opcję **Pokaż źródeł danych**.

2.  W **źródeł danych** wybierz **Dodaj nowe źródło danych** uruchomić **Kreator konfiguracji źródła danych**.

3.  Na **wybierz typ źródła danych** ekranu wybierz **bazy danych**, a następnie wybierz **dalej**.

4.  Na **wybierz połączenie danych** ekranu, wykonaj jedną z następujących czynności:

    -   Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

         —lub—

    -   Wybierz **nowe połączenie** można uruchomić **połączenia Dodawanie i modyfikowanie** okno dialogowe.

5.  Jeśli baza danych wymaga hasła, wybierz opcję, aby obejmować dane poufne, a następnie wybierz **dalej**.

6.  Na **zapisać parametry połączenia w pliku konfiguracji aplikacji** ekranu wybierz **dalej**.

7.  Na **wybierz obiekty bazy danych** ekranu, a następnie rozwiń **tabel** węzła.

8.  Wybierz `Region` tabeli, a następnie wybierz **Zakończ**.

     **NorthwindDataSet** zostanie dodany do projektu i `Region` tabela pojawi się w **źródeł danych** okna.

## <a name="add-controls-to-the-form-to-display-the-data"></a>Dodawanie formantów do formularza w celu wyświetlania danych
 Tworzenie formantów powiązanych z danymi przez przeciąganie elementów z **źródeł danych** okna na formularzu.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Aby utworzyć dane powiązane formantów w formularzu systemu Windows

-   Przeciągnij głównym **Region** węzła z **źródeł danych** okna na formularzu.

     A <xref:System.Windows.Forms.DataGridView> kontroli i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania rekordy są wyświetlane w formularzu. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter`, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane na pasku składnika.

#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Aby dodać przyciski, który wywoła poszczególnych TableAdapter DbDirect metody

1.  Przeciągnij trzy <xref:System.Windows.Forms.Button> formantów **przybornika** na **Form1** (poniżej **RegionDataGridView**).

2.  Ustaw następujące **nazwa** i **tekst** właściwości na każdym przycisku.

    |Nazwa|Tekst|
    |----------|----------|
    |`InsertButton`|**Wstaw**|
    |`UpdateButton`|**Aktualizacja**|
    |`DeleteButton`|**Usuwanie**|

#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Aby dodać kod, aby wstawianie nowych rekordów do bazy danych

1.  Wybierz **InsertButton** Aby utworzyć program obsługi zdarzeń dla zdarzenia kliknij i otworzyć formularz w edytorze kodu.

2.  Zastąp `InsertButton_Click` obsługi zdarzeń z następującym kodem:

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

#### <a name="to-add-code-to-update-records-in-the-database"></a>Aby dodać kod do aktualizowania rekordów w bazie danych

1.  Kliknij dwukrotnie **UpdateButton** Aby utworzyć program obsługi zdarzeń dla zdarzenia kliknij i otworzyć formularz w edytorze kodu.

2.  Zastąp `UpdateButton_Click` obsługi zdarzeń z następującym kodem:

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

#### <a name="to-add-code-to-delete-records-from-the-database"></a>Aby dodać kod, aby usunąć rekordy z bazy danych

1.  Wybierz **DeleteButton** Aby utworzyć program obsługi zdarzeń dla zdarzenia kliknij i otworzyć formularz w edytorze kodu.

2.  Zastąp `DeleteButton_Click` obsługi zdarzeń z następującym kodem:

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>Uruchamianie aplikacji

#### <a name="to-run-the-application"></a>Aby uruchomić aplikację

-   Wybierz **F5** do uruchomienia aplikacji.

-   Wybierz **Wstaw** przycisk, a następnie sprawdź, czy nowy rekord jest widoczny w siatce.

-   Wybierz **aktualizacji** przycisk, a następnie sprawdź, czy rekord jest aktualizowany w siatce.

-   Wybierz **usunąć** przycisk, a następnie sprawdź, czy rekord jest usuwany z siatki.

## <a name="next-steps"></a>Następne kroki
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu formularza powiązane z danymi. Niektóre udoskonalenia, których można dokonać w tym instruktażu obejmują:

-   Dodawanie funkcji wyszukiwania w formularzu.

-   Dodawanie dodatkowych tabel do zestawu danych, wybierając **skonfigurować zestawu danych za pomocą kreatora** z poziomu **źródeł danych** okna. Można dodawać formanty, które wyświetlanie powiązanych danych przeciągając pokrewne węzłów na formularzu. Aby uzyskać więcej informacji, zobacz [relacje w zestawach danych](relationships-in-datasets.md).

## <a name="see-also"></a>Zobacz także

- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)