---
title: Metody DataContext (Projektant O-R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3d8e3a39c79b5dee339c8835c78143277f3015f6
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756132"
---
# <a name="datacontext-methods-or-designer"></a>Metody DataContext (Projektanta obiektów relacyjnych)

<xref:System.Data.Linq.DataContext> metody (w kontekście [składnika LINQ to SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) są metody <xref:System.Data.Linq.DataContext> klasy, która uruchamianie procedury składowane i funkcje w bazie danych.

<xref:System.Data.Linq.DataContext> Jest klasa [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klasy, która działa jako kanał między bazą danych programu SQL Server i [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klas jednostek zamapowane na tę bazę danych. <xref:System.Data.Linq.DataContext> Klasa zawiera informacje o parametrach połączenia i metody połączenia z bazą danych i manipulowania danymi w bazie danych. Domyślnie <xref:System.Data.Linq.DataContext> klasa zawiera kilka metod, które można wywoływać, takich jak <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metodę, która wysyła zaktualizowane dane z [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klasy do bazy danych. Można również utworzyć dodatkowe <xref:System.Data.Linq.DataContext> metod, które mapują na procedury składowane i funkcje. Innymi słowy, wywołanie metody te niestandardowe jest uruchamiana procedura składowana lub funkcja w bazie danych do której <xref:System.Data.Linq.DataContext> metody jest zamapowany. Można dodać nowych metod <xref:System.Data.Linq.DataContext> klasy tak samo, jak należy dodać metody umożliwiające rozszerzenie dowolnej klasy. Jednak w dyskusjach na temat <xref:System.Data.Linq.DataContext> metod w kontekście **Projektanta obiektów relacyjnych**, jest <xref:System.Data.Linq.DataContext> metod, które mapują na procedury składowane i funkcje, które są omawiana.

## <a name="methods-pane"></a>Okienko metody

<xref:System.Data.Linq.DataContext> metody, które mapują na procedury składowane i funkcje są wyświetlane w **metody** okienku **Projektanta obiektów relacyjnych**. **Metody** okienko to okienko po stronie **jednostek** okienka (powierzchni projektu głównego). **Metody** okienko zawiera wszystkie <xref:System.Data.Linq.DataContext> metod, które zostały utworzone przy użyciu **Projektanta obiektów relacyjnych**. Domyślnie **metody** okienko jest pusty; przeciągnij przechowywane procedury lub funkcji z **Eksploratora serwera** lub **Eksploratora bazy danych** na **Projektanta obiektów relacyjnych**  utworzyć <xref:System.Data.Linq.DataContext> metod i wypełnić **metody** okienka. Aby uzyskać więcej informacji, zobacz [porady: metody tworzenia DataContext mapowane na procedury składowane i funkcje (Projektanta obiektów relacyjnych)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Otwieranie i zamykanie okienko metody, klikając prawym przyciskiem myszy **Projektanta obiektów relacyjnych** , a następnie klikając polecenie **ukryć okienko metody** lub **Pokaż okienko metody**, lub użyj skrótu klawiaturowego  **CTRL**+**1**.

## <a name="two-types-of-datacontext-methods"></a>Dwa typy metod DataContext

Metody DataContext są tych metod, które mapują na procedury składowane i funkcje w bazie danych. Możesz utworzyć i Dodaj metodę DataContext na **metody** okienku **Projektanta obiektów relacyjnych**. Istnieją dwa różne typy <xref:System.Data.Linq.DataContext> metod; takich, które zwracają jeden lub więcej zestawów wyników i tych, które nie zawierają:

-   <xref:System.Data.Linq.DataContext> metody, które zwracają jeden lub więcej zestawów wyników:

     Utworzyć ten rodzaj <xref:System.Data.Linq.DataContext> metody, gdy aplikacja wystarczy do uruchamiania procedury składowane i funkcje w bazie danych i zwracają wyniki. Aby uzyskać więcej informacji, zobacz [jak: metody tworzenia DataContext mapowane na procedury składowane i funkcje (Projektanta obiektów relacyjnych)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, a <xref:System.Data.Linq.IMultipleResults>.

-   <xref:System.Data.Linq.DataContext> metody, które nie zwracają zestawów wyników: takie jak wstawia, aktualizacje i usuwa dla klasy określonej jednostki.

     Utworzyć ten rodzaj <xref:System.Data.Linq.DataContext> metody po aplikacji do uruchamiania procedur składowanych zamiast przy użyciu domyślnego [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] zachowanie zapisywanie zmodyfikowanych danych między klasami jednostki oraz bazy danych. Aby uzyskać więcej informacji, zobacz [porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Zwracane typy metodę DataContext

Przeciągnięcie procedury składowane i funkcje z **Eksploratora serwera** lub **Eksploratora bazy danych** na **Projektanta obiektów relacyjnych**, zwracany typ wygenerowany <xref:System.Data.Linq.DataContext> metoda różni się w zależności od tego, gdzie upuścić element. Usunięcie elementów bezpośrednio na istniejącej klasy jednostki tworzy <xref:System.Data.Linq.DataContext> metody z typem zwracanym klasy jednostki; upuszczanie elementów na pustym obszarem **Projektanta obiektów relacyjnych** (w okienku albo) tworzy <xref:System.Data.Linq.DataContext> — metoda który zwraca typ wygenerowanej automatycznie. Automatycznie wygenerowany typ ma nazwę, która odpowiada procedura składowana lub funkcja nazwę i właściwości, które są mapowane na pola zwrócone przez procedurę składowaną lub funkcję.

> [!NOTE]
> Można zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody po dodaniu do okienka metody. Aby sprawdzić lub zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody, zaznacz go i sprawdzić **typu zwracanego** właściwości w **właściwości** okna. Aby uzyskać więcej informacji, zobacz [porady: Zmienianie zwracanego typu metody DataContext (Projektanta obiektów relacyjnych)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Obiekty, które przeciągnij z bazy danych na powierzchnię Projektanta obiektów relacyjnych są nazywane automatycznie, na podstawie nazwy obiektów w bazie danych. Jeśli ten sam obiekt zostanie przeciągnięty więcej niż raz, numer jest dodawany na końcu nową nazwę, która odróżnia nazwy. Nazwy obiektów bazy danych zawierają spacje lub znaki nieobsługiwane w języku Visual Basic lub C#, zostanie zastąpiony miejsca lub nieprawidłowy znak podkreślenia.

## <a name="see-also"></a>Zobacz także

- [LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Procedury składowane](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Porady: tworzenie metodę DataContext mapowane na procedury składowane i funkcje (Projektanta obiektów relacyjnych)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Wskazówki: Dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Wskazówki: Tworzenie LINQ w klasach SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)