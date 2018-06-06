---
title: Utwórz plik bazy danych i za pomocą projektanta tabeli w programie Visual Studio
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 53f34fbed4a2067836c5f2c7a8d4bf8aa6c09d29
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747043"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>Utwórz bazę danych i dodawanie tabel w programie Visual Studio
Visual Studio umożliwia tworzenie i aktualizowanie pliku lokalnej bazy danych w programu SQL Server Express LocalDB. Można również utworzyć bazę danych, wykonując instrukcje języka Transact-SQL w **Eksplorator obiektów SQL Server** okna narzędzia w programie Visual Studio. W tym temacie firma Microsoft Tworzenie pliku MDF i dodać tabelami i kluczami przy użyciu projektanta tabel.

## <a name="prerequisites"></a>Wymagania wstępne
W tym przewodniku, musi mieć opcjonalny **magazynu danych i przetwarzania** obciążenia zainstalowane w programie Visual Studio. Aby go zainstalować, otwórz **Instalator programu Visual Studio** i wybierz polecenie **obciążeń** kartę. W obszarze **sieci Web & chmurze**, wybierz **magazynu danych i przetwarzania**. Wybierz **Modyfikuj** przycisk, aby dodać obciążenia do programu Visual Studio.

## <a name="create-a-project-and-a-local-database-file"></a>Tworzenie projektu i pliku lokalnej bazy danych

### <a name="to-create-a-project-and-a-database-file"></a>Aby utworzyć projekt i plik bazy danych
1.  Tworzenie projektu formularzy systemu Windows o nazwie `SampleDatabaseWalkthrough`.

2.  Na pasku menu wybierz **projektu**, **Dodaj nowy element**.

3.  Na liście szablony elementów, przewiń w dół i wybierz **bazy danych opartej na usługi**.

     ![Okno dialogowe Szablony elementu](../data-tools/media/raddata-vsitemtemplates.png)

4.  Nazwa bazy danych **SampleDatabase**, a następnie wybierz **Dodaj** przycisku.

### <a name="to-add-a-data-source"></a>Aby dodać źródła danych
5.  Jeśli **źródeł danych** okno nie jest otwarty, otwórz go, wybierając **Shift + Alt + D** kluczy lub z menu, wybierając **widoku**, **inne okna**, **Źródeł danych**.

6.  W **źródeł danych** wybierz **Dodaj nowe źródło danych** łącza.

    **Kreator konfiguracji źródła danych** otwiera.

7. Na **wybierz typ źródła danych** wybierz pozycję **bazy danych** , a następnie wybierz **dalej**.

8. Na **wybierz Model bazy danych** wybierz pozycję **dalej** aby zaakceptować wybór domyślny (zestawu danych).

9. Na **wybierz połączenie danych** wybierz pozycję **SampleDatabase.mdf** pliku na liście rozwijanej, a następnie wybierz pozycję **dalej**.

10. Na **zapisać parametry połączenia do pliku konfiguracji aplikacji** wybierz pozycję **dalej**.

11. Jeden **wybierz obiekty bazy danych** strony, zostanie wyświetlony komunikat z informacją bazy danych nie zawiera żadnych obiektów. Wybierz **Zakończ**.

### <a name="to-view-properties-of-the-data-connection"></a>Aby wyświetlić właściwości połączenia danych
Parametry połączenia dla pliku SampleDatabase.mdf można wyświetlić, otwierając okno właściwości połączenia danych:

-   W programie Visual Studio, wybierz **widoku**, **Eksplorator obiektów SQL Server** Jeśli okno nie jest jeszcze otwarty. Otwórz okno właściwości rozwijając **połączenia danych** węzła, otwieranie menu skrótów dla SampleDatabase.mdf, a następnie wybierając **właściwości**.

-   Alternatywnie można wybrać **widoku**, **Eksploratora serwera**, jeśli to okno nie jest jeszcze otwarty. Otwórz okno właściwości rozwijając **połączenia danych** węzła. Otwórz menu skrótów dla SampleDatabase.mdf, a następnie wybierz **właściwości**.

## <a name="create-tables-and-keys-by-using-table-designer"></a>Tworzenie tabel i klucze przy użyciu projektanta tabeli
W tej sekcji utworzysz dwie tabele, klucz podstawowy w każdej tabeli i kilka wierszy przykładowych danych. Zostanie również utworzony klucz obcy, aby określić, jak odpowiadają rekordów w drugiej tabeli rekordów w jednej tabeli.

### <a name="to-create-the-customers-table"></a>Aby utworzyć tabelę Customers
1.  W **Eksploratora serwera** lub **Eksplorator obiektów SQL Server**, rozwiń węzeł **połączenia danych** węzeł, a następnie rozwiń węzeł **SampleDatabase.mdf**węzła.

2.  Otwórz menu skrótów **tabel**, a następnie wybierz **Dodaj nową tabelę**.

     **Projektanta tabel** otwiera i przedstawia siatkę z wiersza jeden domyślny, który reprezentuje jednej kolumny w tabeli, które tworzysz. Przez dodawanie wierszy do siatki dodajesz kolumny w tabeli.

3.  W siatce dodaj wiersz dla każdego z poniższych wpisów:

    |Nazwa kolumny|Typ danych|Zezwalaj na wartości null|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|False (usunięty)|
    |`CompanyName`|`nvarchar(50)`|False (usunięty)|
    |`ContactName`|`nvarchar (50)`|True (wybrane)|
    |`Phone`|`nvarchar (24)`|True (wybrane)|

4.  Otwórz menu skrótów `CustomerID` wiersza, a następnie wybierz **klucz podstawowy**.

5.  Otwórz menu skrótów wiersza domyślne, a następnie wybierz **usunąć**.

6.  Nadaj tabeli nazwę Customers, aktualizując pierwszy wiersz w okienku skryptu, aby dopasować następujący przykład:

    ```sql
    CREATE TABLE [dbo].[Customers]
    ```

    Powinny pojawić się dane podobne do poniższych:

    ![Projektant tabel](../data-tools/media/raddata-table-designer.png)

7.  W lewym górnym rogu **projektanta tabel**, wybierz pozycję **aktualizacji** przycisku.

8.  W **aktualizacje bazy danych w wersji zapoznawczej** okno dialogowe, wybierz opcję **aktualizacji bazy danych** przycisku.

    Wprowadzone zmiany są zapisywane w lokalnym pliku bazy danych.

### <a name="to-create-the-orders-table"></a>Aby utworzyć tabelę Orders
1.  Dodaj inną tabelę, a następnie dodaj wiersz dla każdego wpisu w tabeli poniżej:

    |Nazwa kolumny|Typ danych|Zezwalaj na wartości null|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|False (usunięty)|
    |`CustomerID`|`nchar(5)`|False (usunięty)|
    |`OrderDate`|`datetime`|True (wybrane)|
    |`OrderQuantity`|`int`|True (wybrane)|

2.  Ustaw **OrderID** jako klucz podstawowy, a następnie usuń wiersz domyślne.

3.  Nadaj tabeli nazwę Orders, aktualizując pierwszy wiersz w okienku skryptu, aby dopasować następujący przykład:

    ```sql
    CREATE TABLE [dbo].[Orders]
    ```

4.  W lewym górnym rogu **projektanta tabel**, wybierz pozycję **aktualizacji** przycisku.

5.  W **aktualizacje bazy danych w wersji zapoznawczej** okno dialogowe, wybierz opcję **aktualizacji bazy danych** przycisku.

    Wprowadzone zmiany są zapisywane w lokalnym pliku bazy danych.

### <a name="to-create-a-foreign-key"></a>Aby utworzyć obcy klucz
1.  W okienku kontekstu po prawej stronie siatki, otwórz menu skrótów **kluczy obcych**, a następnie wybierz **Dodaj nowy klucz obcy**, jak pokazano na poniższej ilustracji.

     ![Dodawanie klucza obcego w tabeli projektanta](../data-tools/media/foreignkey.png)

2.  W wyświetlonym polu tekstowym Zastąp **ToTable** z `Customers`.

3.  W okienku T-SQL należy zaktualizować ostatni wiersz, aby dopasować w poniższym przykładzie:

    ```sql
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4.  W lewym górnym rogu **projektanta tabel**, wybierz pozycję **aktualizacji** przycisku.

5.  W **aktualizacje bazy danych w wersji zapoznawczej** okno dialogowe, wybierz opcję **aktualizacji bazy danych** przycisku.

    Wprowadzone zmiany są zapisywane w lokalnym pliku bazy danych.

## <a name="populate-the-tables-with-data"></a>Wypełnij tabele z danymi

### <a name="to-populate-the-tables-with-data"></a>Aby wypełnić tabele danymi

1.  W **Eksploratora serwera** lub **Eksplorator obiektów SQL Server**, rozwiń węzeł w przykładowej bazie danych.

2.  Otwórz menu skrótów **tabel** węzła, wybierz opcję **Odśwież**, a następnie rozwiń węzeł **tabel** węzła.

3.  Otwórz menu skrótów dla tabeli klientów, a następnie wybierz **Pokaż dane tabeli**.

4.  Dodaj niezależnie od danych dla niektórych klientów.

    Można określić dowolne pięć znaków jako identyfikatory klienta, ale należy wybrać co najmniej jeden, który można zapamiętać do użycia w dalszej części tej procedury.

5.  Otwórz menu skrótów dla tabeli zamówienia, a następnie wybierz **Pokaż dane tabeli**.

6.  Dodawanie danych dla niektórych zleceń.

    > [!IMPORTANT]
    > Upewnij się, że wszystkie identyfikatory kolejności i ilości kolejności są liczbami całkowitymi i czy każdy identyfikator klienta jest zgodna wartość określoną w kolumnie CustomerID tabeli klientów.

7.  Na pasku menu wybierz **pliku**, **Zapisz wszystko**.

## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do danych w programie Visual Studio](accessing-data-in-visual-studio.md)