---
title: Tworzenie formularza Windows Forms na potrzeby wyszukiwania danych
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d4fe1106556e94155a0d01d3d7c9983d5ed122ad
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746731"
---
# <a name="create-a-windows-form-to-search-data"></a>Tworzenie formularza Windows Forms na potrzeby wyszukiwania danych
Typowy scenariusz aplikacji jest wyświetlanie wybranych danych w formularzu. Można na przykład wyświetlanie zleceń dla określonych odbiorców lub szczegóły określonej kolejności. W tym scenariuszu użytkownik wprowadza informacje w formularzu, a następnie zapytanie jest wykonywane przy użyciu danych wejściowych użytkownika jako parametr; oznacza to, że jest wybrane dane na podstawie zapytania parametrycznego. Zapytanie zwraca tylko dane, które spełnia kryteria wprowadzony przez użytkownika. W tym przewodniku pokazano, jak utworzyć kwerendę, która zwraca klientów w określonym mieście i zmodyfikować interfejsu użytkownika, dzięki czemu użytkownicy mogą wprowadzać nazwę miejscowości i naciśnij przycisk, aby wykonać zapytanie.

 Użycie zapytań sparametryzowanych ułatwia aplikacji wydajne, umożliwiając pracę, najlepiej na bazy danych — szybkie filtrowanie rekordów. Z kolei żądania tabeli całą bazę danych, przenieść go za pośrednictwem sieci, a następnie użyj logiki aplikacji można znaleźć żądanego rekordów, aplikacja może być powolne i nieefektywne.

 Można dodać zapytania parametrycznego do TableAdapter (i formantów aby zaakceptować wartości parametrów i wykonać zapytanie), za pomocą **kompilator kryteriów wyszukiwania** okno dialogowe. Otwórz okno dialogowe, wybierając **Dodaj zapytanie** na **danych** menu (lub na dowolnym tagów inteligentnych TableAdapter).

 Zadania przedstawione w tym przewodniku obejmują:

-   Tworzenie nowego projektu aplikacji Windows Forms.

-   Tworzenie i konfigurowanie źródła danych do aplikacji z **konfiguracji źródła danych** kreatora.

-   Ustawienie typu listy elementów w **źródeł danych**okna.

-   Tworzenie formantów wyświetlających dane przez przeciąganie elementów z **źródeł danych** okna w formularzu.

-   Dodawanie formantów do wyświetlania danych w formularzu.

-   Kończenie pracy **kompilator kryteriów wyszukiwania** okno dialogowe.

-   Wprowadzanie parametrów do formularza i wykonywania zapytania parametrycznego.

## <a name="prerequisites"></a>Wymagania wstępne

W tym przewodniku zastosowano programu SQL Server Express LocalDB i przykładowej bazy danych Northwind.

1.  Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [strony pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalator programu Visual Studio**. W Instalatorze programu Visual Studio, można zainstalować jako część programu SQL Server Express LocalDB **magazynu danych i przetwarzania** obciążenia, lub jako poszczególnych składników.

2.  Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio Otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **magazynu danych i przetwarzania** obciążenia w Instalatorze programu Visual Studio.) Rozwiń węzeł **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w wystąpieniu bazy danych LocalDB, a następnie wybierz **nowej kwerendy...** .

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptu języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL utworzy bazę danych Northwind od początku i wypełnia danych.

    3. Wkleić skryptu T-SQL w edytorze zapytań, a następnie wybierz pozycję **Execute** przycisku.

       Po pewnym czasie zapytanie kończy wykonywanie i utworzeniu bazy danych Northwind.

## <a name="create-the-windows-forms-application"></a>Tworzenie aplikacji formularzy systemu Windows
 Pierwszym krokiem jest utworzenie **aplikacji Windows Forms**. Przypisanie nazwy do projektu jest opcjonalne w tym kroku, ale można będzie nadaj mu nazwę w tym miejscu, ponieważ projekt będzie zapisać później.

#### <a name="to-create-the-new-windows-forms-application-project"></a>Aby utworzyć nowy projekt aplikacji Windows Forms

1. W programie Visual Studio na **pliku** menu, wybierz opcję **nowy**, **projektu...** .

2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, następnie wybierz **Windows Desktop**.

3. W środkowym okienku wybierz **aplikacji formularzy systemu Windows** typu projektu.

4. Nazwij projekt **WindowsSearchForm**, a następnie wybierz pozycję **OK**.

     **WindowsSearchForm** projektu jest tworzony i dodawany do **Eksploratora rozwiązań**.

## <a name="create-the-data-source"></a>Utwórz źródło danych
Spowoduje to utworzenie źródła danych z bazy danych przy użyciu **konfiguracji źródła danych** kreatora.

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

8.  Wybierz **klientów** tabeli, a następnie kliknij przycisk **Zakończ**.

     **NorthwindDataSet** zostanie dodany do projektu i **klientów** tabela pojawi się w **źródeł danych** okna.

## <a name="create-the-form"></a>Tworzenie formularza
 Formanty powiązane z danymi można utworzyć, przeciągając elementy z **źródeł danych** okna na formularzu.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Aby utworzyć formantów powiązanych z danymi

1.  Rozwiń węzeł **klientów** w węźle **źródeł danych** okna.

2.  Przeciągnij **klientów** węzła z **źródeł danych** okna do formularza.

     A <xref:System.Windows.Forms.DataGridView> i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania rekordy są wyświetlane w formularzu. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane na pasku składnika.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Dodawanie do zapytania parametryzacja (funkcji wyszukiwania)
 Klauzula WHERE można dodać do oryginalnego zapytania za pomocą **kompilator kryteriów wyszukiwania** okno dialogowe.

#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>Tworzenie zapytania parametrycznego i kontroli w celu wprowadź parametry

1.  Wybierz <xref:System.Windows.Forms.DataGridView> kontroli, a następnie wybierz pozycję **Dodaj zapytanie** na **danych** menu.

2.  Typ `FillByCity` w **nową nazwę zapytania** obszar na **kompilator kryteriów wyszukiwania** okno dialogowe.

3.  Dodaj `WHERE City = @City` kwerendy w **tekst zapytania** obszaru.

     Zapytanie powinny być podobne do następujących:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    >  Dostęp i OLE DB źródeł danych użyj znak zapytania ("?") do oznaczania parametry, dlatego w klauzuli WHERE będzie wyglądać następująco: `WHERE City = ?`.

4.  Kliknij przycisk **OK** zamknąć **kompilator kryteriów wyszukiwania** okno dialogowe.

     A **FillByCityToolStrip** zostanie dodany do formularza.

## <a name="testing-the-application"></a>Testowanie aplikacji
 Uruchamianie aplikacji otwiera gotowa do sporządzenia parametr jako dane wejściowe formularza.

#### <a name="to-test-the-application"></a>Aby przetestować aplikację

1.  Naciśnij klawisz F5, aby uruchomić aplikację.

2.  Typ **Londyn** do **miasta** polu tekstowym, a następnie kliknij przycisk **FillByCity**.

     Siatki danych jest wypełniana klientów, które spełniają kryteria. W tym przykładzie Siatka danych są wyświetlane tylko klientów, którzy mają wartość **Londyn** w ich **miasta** kolumny.

## <a name="next-steps"></a>Następne kroki
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po utworzeniu formularza sparametryzowanego. Niektóre udoskonalenia, których można dokonać w tym instruktażu obejmują:

-   Dodawanie formantów, które wyświetlanie powiązanych danych. Aby uzyskać więcej informacji, zobacz [relacje w zestawach danych](relationships-in-datasets.md).

-   Edytowanie zestawu danych, aby dodać lub usunąć obiekty bazy danych. Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie zestawów danych](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też

- [Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)