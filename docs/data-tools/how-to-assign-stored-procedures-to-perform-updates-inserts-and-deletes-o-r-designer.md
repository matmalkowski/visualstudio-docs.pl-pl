---
title: Procedury przechowywane w celu przeprowadzenia aktualizacji, wstawiania i usuwania w składniku Linq to SQL Projektanta obiektów relacyjnych
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a26d3702bcf885e5d8da48144c8f6458392bab4f
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057148"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)

Procedury składowane można dodać do Projektanta obiektów relacyjnych i wykonywane co typowe <xref:System.Data.Linq.DataContext> metody. One również pozwala zastąpić domyślną LINQ do zachowania w czasie wykonywania SQL wykonuje wstawiania, aktualizacji i usuwa podczas zmiany są zapisywane z klasami jednostki bazy danych (na przykład podczas wywoływania metody <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metody).

> [!NOTE]
> Jeśli Twoja procedura składowana zwraca wartości, które muszą zostać odesłany do klienta (na przykład obliczania wartości w procedurze składowanej), utwórz parametry wyjściowe w Twojej procedur składowanych. Jeśli nie możesz użyć parametrów wyjściowych, zapis zastępuje implementację metody częściowej, zdejmując to zadanie wygenerowany przez Projektanta obiektów relacyjnych. Elementy członkowskie, baza danych wygenerowała wartości muszą należy ustawić odpowiednie wartości po pomyślnym ukończeniu operacji INSERT lub UPDATE. Aby uzyskać więcej informacji, zobacz [obowiązki deweloperów w zastępowanie domyślne zachowanie](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).

> [!NOTE]
> LINQ do SQL obsługuje baza danych wygenerowała wartości automatycznie tożsamości (automatycznego przyrostu), rowguidcol (identyfikator GUID generowany przez bazę danych) i kolumn znaczników czasu. Wartości generowanych przez bazę danych w innych typów kolumn spowoduje nieoczekiwane wartości null. Aby zwrócić wartości generowanych przez bazę danych, należy ręcznie ustawić <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> do **true** i <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> do jednej z następujących czynności: [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert ](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>), lub [AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="configure-the-update-behavior-of-an-entity-class"></a>Konfigurowanie zachowania aktualizacji klasy jednostki

Domyślnie logika zaktualizować bazę danych (wstawienia, aktualizacje i usunięcia) ze zmianami, które zostały wprowadzone w danych w LINQ w klasach SQL jednostki znajduje się w składniku LINQ to SQL środowiska wykonawczego. Środowisko uruchomieniowe tworzy domyślne polecenia INSERT, UPDATE i DELETE, które są oparte na schemat tabeli (kolumny i informacje o kluczu podstawowym). Jeśli domyślne zachowanie jest niepożądane, można skonfigurować zachowanie aktualizacji przypisując określonych procedur składowanych do wykonania niezbędnych operacji wstawienia, aktualizacje i usunięcia wymagane do obsługi danych w tabeli. Ponadto można to zrobić, jeśli domyślne zachowanie nie jest generowany, na przykład po z klasami jednostki mapowania do widoków. Ponadto podczas bazy danych wymaga dostępu do tabeli za pomocą procedur składowanych można zastąpić domyślne zachowanie aktualizacji.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Aby przypisać procedur składowanych, aby zastąpić domyślne zachowanie klasę jednostki

1.  Otwórz **LINQ do SQL** pliku w projektancie. (Kliknij dwukrotnie plik .dbml w **Eksploratora rozwiązań**.)

2.  W **Eksploratora serwera** lub **Eksploratora bazy danych**, rozwiń węzeł **procedur składowanych** i Znajdź procedur składowanych, których chcesz użyć dla Insert, Update i/lub usunąć polecenia klasy jednostka.

3.  Przeciągnąć procedurę składowaną do Projektanta obiektów relacyjnych.

     Procedura składowana jest dodawany do okienka metod jako <xref:System.Data.Linq.DataContext> metody. Aby uzyskać więcej informacji, zobacz [metodę DataContext (Projektanta obiektów relacyjnych)](../data-tools/datacontext-methods-o-r-designer.md).

4.  Wybierz klasę jednostki, dla którego chcesz użyć procedury składowanej umożliwiające wykonywanie aktualizacji.

5.  W **właściwości** okna, wybierz polecenie do zastąpienia (**Wstaw**, **aktualizacji**, lub **usunąć**).

6.  Kliknij przycisk wielokropka (...) obok słowa **Użyj środowiska wykonawczego** otworzyć **Konfigurowanie zachowania** okno dialogowe.

7.  Wybierz **dostosować**.

8.  Wybierz odpowiednie procedury składowanej w **Dostosuj** listy.

9. Listę **argumenty metody** i **właściwości klasy** do sprawdzenia, czy **argumenty metody** mapy do odpowiedniego **właściwości klasy**. Mapowanie oryginalnego argumenty metody (Original_*ArgumentName*) do jego początkowych właściwości (*PropertyName* (oryginalny)) dla poleceń Update i Delete.

    > [!NOTE]
    > Domyślnie argumenty metody mapować do właściwości klasy podczas nazwy są zgodne. Po zmianie właściwości nazwy nie jest już zgodne między tabelą i klasy jednostka, może być konieczne wybierz właściwość klasy równoważne do mapowania na, jeśli projektant nie może określić poprawne mapowania.

10. Kliknij przycisk **OK** lub **zastosować**.

    > [!NOTE]
    > Możesz skonfigurować działanie dla każdej kombinacji klasy/zachowanie, pod warunkiem, możesz kliknąć przycisk **Zastosuj** po każdej zmianie. Jeśli zmienisz klasy lub zachowania przed kliknięciem przycisku **Zastosuj**, zapewniając możliwość zastosować zmiany będą wyświetlane okno dialogowe.

Aby przywrócić za pomocą domyślnej środowiska uruchomieniowego logiki aktualizacji, kliknij przycisk wielokropka obok Insert, Update, lub Usuń polecenie w **właściwości** okna, a następnie wybierz **Użyj środowiska wykonawczego** w  **Konfigurowanie zachowania** okno dialogowe.

## <a name="see-also"></a>Zobacz także

- [LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metody DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ do SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Wstawiania, aktualizowania i usuwania działań (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)