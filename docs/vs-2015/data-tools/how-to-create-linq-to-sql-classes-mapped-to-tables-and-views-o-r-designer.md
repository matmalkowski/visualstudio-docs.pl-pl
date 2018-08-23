---
title: 'Porady: Tworzenie typu LINQ do klas SQL zamapowanych na tabele i widoki (Projektant O-R) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1d9cebc980b62a5676ee4e65e5554086a273fa73
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42673731"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Porady: Tworzenie typu LINQ do klas SQL zamapowanych na tabele i widoki (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: Tworzenie klasy programu LINQ to SQL zamapowanych na tabele i widoki (Projektant O-R)](https://docs.microsoft.com/visualstudio/data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer).

Klasy LINQ do SQL, które są mapowane na bazę danych, tabele i widoki są nazywane *klas jednostek*. Klasa jednostki mapuje rekord, podczas gdy poszczególne właściwości klasy jednostki mapują do poszczególnych kolumn, które tworzą rekord. Tworzenie klas jednostek, które są oparte na bazy danych tabel lub widoków, przeciągając tabele lub widoki z **Eksploratora serwera**/**Eksplorator bazy danych** na [narzędzi LINQ to SQL w Program Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Generuje klasy, a następnie stosuje konkretne [! LINQ do SQL atrybutów umożliwiające [! LINQ do SQL funkcji (łączności danych i możliwości edytowania <xref:System.Data.Linq.DataContext>). Aby uzyskać szczegółowe informacje o [! Klasy LINQ do SQL, zobacz [LINQ to SQL Model obiektów](http://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810).

> [!NOTE]
> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Jest mapowania relacyjnych prostego obiektu, ponieważ obsługuje on tylko relacji mapowanie 1:1. Innymi słowy klasa jednostka może mieć tylko relacji mapowanie 1:1 z tabeli bazy danych lub widoku. Mapowanie złożonych, takie jak mapowanie klasę jednostki z wieloma tabelami, nie jest obsługiwane. Jednak można mapować klasę jednostki, do widoku, który łączy się wieloma powiązanymi tabelami.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Tworzenie klasy LINQ do SQL, które są mapowane do bazy danych tabel lub widoków
 Przeciąganie tabele lub widoki z **Eksploratora serwera**/**Eksplorator bazy danych** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tworzy klas jednostek oprócz <xref:System.Data.Linq.DataContext> metod, które są używane do wykonywanie aktualizacji.

 Domyślnie [! LINQ do SQL środowiska uruchomieniowego tworzy logiki, aby zapisać zmiany z klasy można aktualizować jednostek w bazie danych. Tę logikę opiera się na schemat tabeli (definicje kolumn i informacje o kluczu podstawowym). Jeśli nie chcesz tego zachowania, można skonfigurować klasę jednostki, aby użyć procedur składowanych do wykonywania operacji wstawiania, aktualizacji i usuwa zamiast przy użyciu domyślnego [! LINQ do SQL zachowania w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Aby tworzyć LINQ do klas SQL, które są mapowane do bazy danych tabel lub widoków

1.  W **serwera**/**Eksplorator bazy danych**, rozwiń węzeł **tabel** lub **widoków** i Znajdź w tabeli bazy danych lub widok Aby użyć w aplikacji.

2.  Przeciągnij tabelę lub wyświetlić na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Klasa jednostki zostanie utworzony i wyświetlony na powierzchni projektowej. Klasa jednostki ma właściwości, które mapują do kolumn w wybranej tabeli lub widoku.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Tworzenie obiektu źródła danych i wyświetlić dane w formularzu
 Po utworzeniu klas jednostek za pomocą [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], można utworzyć źródło danych obiektu i wypełnić [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) przy użyciu klas jednostek.

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Aby utworzyć źródło danych obiektu opartego na LINQ do SQL klas jednostek

1.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie** do kompilowania projektu.

2.  Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.

3.  W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.

4.  Kliknij przycisk **obiektu** na **wybierz typ źródła danych** strony, a następnie kliknij przycisk **dalej**.

5.  Rozwiń węzły, a następnie znajdź i wybierz klasy.

    > [!NOTE]
    > Jeśli **klienta** klasy nie jest dostępna, Anuluj kreatora, skompiluj projekt i uruchom ponownie kreatora.

6.  Kliknij przycisk **Zakończ** Utwórz źródło danych i dodać **klienta** klasy jednostki **źródeł danych** okna.

7.  Przeciągnij elementy z **źródeł danych** okna w formularzu.

## <a name="see-also"></a>Zobacz także

- [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Wskazówki: Tworzenie składnika LINQ to SQL klas (Projektant O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Porady: Tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Model obiektu LINQ to SQL](http://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [Wskazówki: Dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Wskazówki: Dodawanie walidacji do klas jednostek](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [Porady: Tworzenie skojarzenia (Relacja) między LINQ to SQL klas (Projektant O/R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)