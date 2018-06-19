---
title: Tworzenie parametrycznych zapytań TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7d3985cc8faf76c5c5767090abd5b87101ddbb45
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924199"
---
# <a name="create-parameterized-tableadapter-queries"></a>Tworzenie parametrycznych zapytań TableAdapter
Uruchamianie zapytania parametrycznego zwraca dane, które spełniają warunki klauzuli WHERE, w ramach zapytania. Na przykład można parametryzacja listę klientów, aby wyświetlić tylko w przypadku klientów z niektórych miasta przez dodanie `WHERE City = @City` na końcu instrukcji SQL, które zwraca listę klientów.

 Tworzenie parametrycznych zapytań TableAdapter w **Projektant obiektów Dataset**. Można je również utworzyć w aplikacji systemu Windows z **parametryzacja źródła danych** na **danych** menu. **Parametryzacja źródła danych** polecenie tworzy formantów w formularzu gdzie wartości parametrów wejściowych i uruchom zapytanie.

> [!NOTE]
> Podczas tworzenia zapytania parametrycznego, Notacja parametru specyficzne dla bazy danych, która jest kodowanie przed. Na przykład dostępu i OleDb źródeł danych, użyj znaku zapytania '?' do oznaczania parametry, dlatego w klauzuli WHERE będzie wyglądać następująco: `WHERE City = ?`.

> [!NOTE]
> Okna dialogowe i dostępne polecenia menu mogą różnić się od opisanych w pomocy, w zależności od ustawienia active lub edition, którego używasz. Aby zmienić ustawienia, przejdź do **narzędzia** menu i wybierz **Import i eksport ustawień**. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-parameterized-tableadapter-query"></a>Tworzenie parametrycznych zapytań TableAdapter

#### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Aby utworzyć zapytania parametrycznego w Projektancie obiektów Dataset

-   Utwórz nowy obiekt TableAdapter, dodając klauzulę WHERE z odpowiednie parametry w instrukcji SQL. Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie TableAdapters](../data-tools/create-and-configure-tableadapters.md).

     —lub—

-   Dodaj zapytanie do istniejących TableAdapter, dodając klauzulę WHERE z odpowiednie parametry w instrukcji SQL.

#### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Aby utworzyć zapytania parametrycznego podczas projektowania formularza powiązane z danymi

1.  Wybierz kontrolkę w formularzu, która jest już powiązany z zestawem danych. Aby uzyskać więcej informacji, zobacz [formanty formularzy systemu Windows powiązać z danymi w Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2.  Na **danych** menu, wybierz opcję **Dodaj zapytanie**.

3.  Zakończenie **kompilator kryteriów wyszukiwania** okno dialogowe, dodając klauzulę WHERE z odpowiednie parametry w instrukcji SQL.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Aby dodać zapytanie do istniejącego formularza z danymi

1.  Otwórz formularz w **Projektant formularzy systemu Windows**.

2.  Na **danych** menu, wybierz opcję **Dodaj zapytanie** lub **danych tagów inteligentnych**.

    > [!NOTE]
    >  Jeśli **Dodaj zapytanie** nie jest dostępny na **danych** menu, zaznacz kontrolkę w formularzu, że wyświetla źródła danych, należy dodać parametry do. Na przykład, jeśli w formularzu są wyświetlane dane w <xref:System.Windows.Forms.DataGridView> sterowania, wybierz go. Jeśli dane są wyświetlane w formularzu w pojedynczych formantów, wybierz wszystkie kontrolki powiązania danych.

3.  W **tabeli źródła danych wybierz** obszaru, wybierz tabelę, który chcesz dodać parametryzacja do.

4.  Wpisz nazwę w **nową nazwę zapytania** Jeśli tworzysz nową kwerendę.

     —lub—

     Wybierz zapytanie w **nazwa zapytania istniejące** pole.

5.  W **tekst zapytania** wpisz kwerendę, która przyjmuje parametry.

6.  Wybierz **OK**.

     Formant parametr wejściowy oraz a **obciążenia** przycisk są dodawane do formularza w <xref:System.Windows.Forms.ToolStrip> formantu.

#### <a name="querying-for-null-values"></a>Uzyskiwanie informacji o wartości null
Gdy chcesz wysyłać zapytania dotyczące rekordów niezawierające bieżącej wartości parametrów TableAdapter można przypisać wartości null. Na przykład, należy wziąć pod uwagę następujące zapytanie, które ma `ShippedDate` parametru w jego `WHERE` klauzuli:

 ```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

 Jeżeli to zapytań w TableAdapter, może wysłać zapytania dla wszystkich zleceń, które nie zostały wysłane z następującym kodem:

 [!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
 [!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

 Aby włączyć kwerendę, aby akceptować wartości null:

1.  W **Projektant obiektów Dataset**, wybierz zapytanie TableAdapter, do którego powinien akceptować wartości null parametrów.

2.  W **właściwości** wybierz **parametry**, następnie kliknij przycisk wielokropka (**...** ) przycisk, aby otworzyć **Edytor kolekcji parametrów**.

3.  Wybierz parametr, który zezwala na wartości null i ustaw **AllowDbNull** właściwości `true`.

## <a name="see-also"></a>Zobacz także

- [Wypełnianie zbiorów danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)