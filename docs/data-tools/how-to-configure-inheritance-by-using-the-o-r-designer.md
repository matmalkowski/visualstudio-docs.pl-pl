---
title: 'Porady: Konfigurowanie dziedziczenia przy użyciu narzędzia Projektant O-R'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8808100d2576a4b14b02975d49606ef5b215c216
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Porady: Konfigurowanie dziedziczenia za pomocą Projektanta obiektów relacyjnych
[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) Obsługuje koncepcja dziedziczenia pojedynczej tabeli, jak często jest zaimplementowana w systemach relacyjnych. W dziedziczeniu pojedynczej tabeli Brak tabeli pojedynczej bazy danych, która zawiera pola zarówno informacje nadrzędnego, jak i podrzędnych. Z danych relacyjnych kolumny rozróżniacza zawiera wartość, która określa, która klasa należy każdy rekord.

Rozważmy na przykład tabeli osoby, która zawiera wszystkich stosowanych przez firmę. Niektórzy użytkownicy są pracownikami i niektórzy użytkownicy są menedżerów. Tabela osób zawiera kolumny o nazwie `EmployeeType` mający wartość 1 dla menedżerów i wartość 2 dla pracowników, co jest kolumny rozróżniacza. W tym scenariuszu można utworzyć podklasy pracowników i wypełnienie klasy tylko te rekordy, które mają `EmployeeType` wartość 2. Można również usunąć kolumny, których nie można zastosować z klas.

Tworzenie modelu obiektów, która korzysta z dziedziczenia (i odpowiada danych relacyjnych) może być nieco trudne. Poniższa procedura przedstawia kroki wymagane do skonfigurowania dziedziczenia za pomocą Projektanta obiektów relacyjnych. Wykonaj następujące kroki, ogólnego bez odwołujących się do istniejącej tabeli i kolumny może być trudne, więc podano wskazówki, która korzysta z danych. Szczegółowe informacje krok po kroku dotyczące konfigurowania dziedziczenia przy użyciu [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], zobacz [wskazówki: Tworzenie klasy LINQ do SQL za pomocą pojedynczej tabeli dziedziczenie (Projektanta obiektów relacyjnych)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

## <a name="to-create-inherited-data-classes"></a>Aby utworzyć dziedziczone klas danych

1.  Otwórz [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] przez dodanie **klasy LINQ do SQL** element do istniejącego projektu Visual Basic lub C#.

2.  Przeciągnij tabeli ma być używany jako klasa bazowa na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

3.  Przeciągnij drugiej kopii tabeli do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] i zmień jego nazwę. Jest to klasa pochodna lub podklasy.

4.  Kliknij przycisk **dziedziczenia** w **Projektant obiektów relacyjnych** karcie **przybornika**, a następnie kliknij podklasy (można zmienić nazwy tabeli) i połącz go z klasy podstawowej.

    > [!NOTE]
    >  Kliknij przycisk **dziedziczenia** elementu **przybornika** i zwolnij przycisk myszy, kliknij drugiej kopii klasy utworzonego w kroku 3, a następnie kliknij to pierwsza klasa utworzony w kroku 2. Pierwsza klasa wskaże strzałkę na linii dziedziczenia.

5.  W każdej klasie Usuń wszystkie właściwości obiektu, które nie mają być wyświetlane i które nie są używane dla skojarzenia. Zostanie wyświetlony błąd, jeśli próba usunięcia używany do skojarzenia właściwości obiektu: [właściwość \<właściwość name > nie można usunąć, ponieważ uczestniczy ona w skojarzeniu \<Nazwa skojarzenia >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    >  Ponieważ klasa pochodna dziedziczy właściwości zdefiniowane w swojej klasie podstawowej, te same kolumny nie można zdefiniować w każdej klasie. (Kolumny są zaimplementowane jako właściwości). Tworzenie kolumn w klasie pochodnej można włączyć, ustawiając dla właściwości w klasie podstawowej modyfikator dziedziczenia. Aby uzyskać więcej informacji, zobacz [podstawowe informacje o dziedziczeniu (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).

6.  Wybierz linii dziedziczenia w [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

7.  W **właściwości** ustaw **właściwość rozróżniacza** na nazwę kolumny, która służy do rozróżnienia rekordów w klas.

8.  Ustaw **wartość dyskryminatora klasy pochodnej** na wartość w bazie danych, który wyznacza dziedziczony typ rekordu. (Jest to wartość jest przechowywana w kolumnie rozróżniacza i który służy do oznaczania dziedziczonej klasie).

9. Ustaw **wartość dyskryminatora klasy podstawowej** właściwości na wartość, która określa rekord jako typu podstawowego. (Jest to wartość jest przechowywana w kolumnie rozróżniacza i który służy do oznaczania klasy podstawowej).

10. Opcjonalnie można również ustawić **domyślnej dziedziczenia** właściwość, aby wskazać typ w hierarchii dziedziczenia, który jest używany podczas ładowania wierszy, które nie pasują zdefiniowany kod dziedziczenia. Innymi słowy, jeśli rekord ma wartość w kolumnie jego rozróżniacza który nie pasuje do wartości w albo **wartość dyskryminatora klasy pochodnej** lub **wartość dyskryminatora klasy podstawowej** właściwości, rekord zostanie załadowany do typu wyznaczony jako **domyślnej dziedziczenia**.

## <a name="see-also"></a>Zobacz także

- [LINQ do SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Wskazówki: Tworzenie klasy LINQ do SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Wskazówki: Tworzenie klasy LINQ do SQL za pomocą pojedynczej tabeli dziedziczenia (Projektanta obiektów relacyjnych)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Podstawowe informacje o dziedziczeniu (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Dziedziczenie](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)