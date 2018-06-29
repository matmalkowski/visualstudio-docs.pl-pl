---
title: 'Porady: tworzenie LINQ w klasach SQL zamapowane do tabel i widoków (Projektant O-R)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 11fb4265047387e30327bbbe17c9babf1f23ec61
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089328"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Porady: tworzenie LINQ w klasach SQL zamapowane do tabel i widoków (Projektanta obiektów relacyjnych)
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klasy, które są mapowane na bazę danych, tabele i widoki są nazywane *klas jednostek*. Mapuje klasy jednostka rekordu, natomiast poszczególne właściwości klasy jednostki mapowania poszczególnych kolumn, które tworzą rekord. Tworzenie klas jednostek, które są oparte na tabele lub widoki przeciągając tabele lub widoki z **Eksploratora serwera** lub **Eksploratora bazy danych** na [narzędzi LINQ do SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). **Projektanta obiektów relacyjnych** generuje klas i stosuje konkretnym [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] atrybutów w celu włączenia [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] funkcji (przesyłanie danych i możliwości edycji <xref:System.Data.Linq.DataContext>). Aby uzyskać szczegółowe informacje o [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klas, zobacz [LINQ w modelu obiektu SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
>  **Projektanta obiektów relacyjnych** jest mapowania relacyjnego prostego obiektu, ponieważ obsługuje on tylko relacje 1:1 mapowania. Innymi słowy Klasa jednostki może mieć tylko relacji mapowania 1:1 z tabeli bazy danych lub widoku. Mapowanie złożonych, takie jak mapowania klasy jednostki z wieloma tabelami, nie jest obsługiwana. Jednak możesz mapować klasę jednostki do widoku, który łączy wiele powiązanych tabel.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Utwórz LINQ w klasach SQL, które są mapowane na bazę danych, tabel lub widoków
 Przeciąganie tabele lub widoki z **Eksploratora serwera** lub **Eksploratora bazy danych** na **Projektanta obiektów relacyjnych** tworzy klas jednostek oprócz <xref:System.Data.Linq.DataContext> metody który są używane do przeprowadzania aktualizacji.

 Domyślnie [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] środowiska uruchomieniowego tworzy logiki, aby zapisać zmiany z klasy jednostki nadaje się do aktualizacji w bazie danych. Istotą takiej logiki jest oparta na schemat tabeli (definicje kolumn i informacje o kluczu podstawowym). Jeśli nie chcesz, aby ten problem, można skonfigurować klasę jednostki używają procedur składowanych do wykonywania operacji wstawiania, aktualizacji i usunięć zamiast przy użyciu domyślnego [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] zachowania w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Aby utworzyć LINQ w klasach SQL, które są mapowane na bazę danych, tabel lub widoków

1.  W **serwera** lub **Eksploratora bazy danych**, rozwiń węzeł **tabel** lub **widoków** i Znajdź w tabeli bazy danych lub widok do użycia w sieci aplikacja.

2.  Przeciągnij tabeli lub widoku na **Projektanta obiektów relacyjnych**.

     Klasa jednostki jest tworzony i wyświetlany na powierzchni projektu. Klasa jednostki ma właściwości, które mapują kolumny w wybranej tabeli lub widoku.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Utwórz źródło danych obiektu i wyświetlić dane w formularzu
 Po utworzeniu klas jednostek przy użyciu **Projektanta obiektów relacyjnych**, można utworzyć obiektu źródła danych i wypełnić [okna źródeł danych](add-new-data-sources.md) z klas jednostek.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Aby utworzyć źródło danych obiektu oparte na LINQ w klasach SQL jednostki

1.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie** Aby skompilować projekt.

2.  Na **danych** menu, kliknij przycisk **Pokaż źródeł danych**.

3.  W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.

4.  Kliknij przycisk **obiektu** na **wybierz typ źródła danych** a następnie kliknij przycisk **dalej**.

5.  Rozwiń węzły i Znajdź i zaznacz klasy.

    > [!NOTE]
    >  Jeśli **klienta** klasa nie jest dostępna, Anuluj wychodząc kreatora skompilować projekt i ponownie uruchom kreatora.

6.  Kliknij przycisk **Zakończ** utworzyć źródło danych i dodać **klienta** klasy jednostki **źródeł danych** okna.

7.  Przeciągnij elementy z **źródeł danych** okna w formularzu.

## <a name="see-also"></a>Zobacz także

- [LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Wskazówki: Tworzenie LINQ w klasach SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Metody DataContext (Projektanta obiektów relacyjnych)](../data-tools/datacontext-methods-o-r-designer.md)
- [Porady: tworzenie metodę DataContext mapowane na procedury składowane i funkcje (Projektanta obiektów relacyjnych)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ do SQL modelu obiektów](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [Wskazówki: Dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Porady: Tworzenie skojarzenia (Relacja) między klasy LINQ do SQL (Projektanta obiektów relacyjnych)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)