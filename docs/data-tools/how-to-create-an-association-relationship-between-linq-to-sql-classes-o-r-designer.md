---
title: Tworzenie relacji między klasy LINQ do SQL za pomocą Projektanta obiektów relacyjnych
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9eb6237af696dc1f56ae82bd99a1ddfc54851484
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Porady: Tworzenie skojarzenia między klasy LINQ do SQL (Projektanta obiektów relacyjnych)
Skojarzenia między klasami jednostki w [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] są podobne do relacji między tabelami w bazie danych. Można utworzyć skojarzenia między klasami jednostki przy użyciu **Edytor skojarzenia** okno dialogowe.

Korzystając z należy wybrać klasy nadrzędnej i podrzędnej klasy **Edytor skojarzenia** okno dialogowe, aby utworzyć skojarzenie. Klasa nadrzędna jest klasa jednostki, która zawiera klucz podstawowy; klasy podrzędnej jest klasa jednostki, która zawiera klucz obcy. Na przykład jeśli klas jednostek zostały utworzone, które są mapowane na tabeli klientów Northwind i zleceń, klasa klienta będzie klasy nadrzędnej i klasa kolejności byłoby klasy podrzędnej.

> [!NOTE]
>  Przeciągnięcie tabel z **Eksploratora serwera**/**Eksploratora bazy danych** na [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]), skojarzenia są tworzone automatycznie na podstawie na istniejące relacje klucza obcego w bazie danych.

## <a name="association-properties"></a>Właściwości skojarzenia
Po utworzeniu skojarzenia, po wybraniu skojarzenie w Projektancie obiektów relacyjnych, są niektóre właściwości można skonfigurować w **właściwości** okna. (Skojarzenie jest linii między powiązanymi klasami). Poniższa tabela zawiera opisy właściwości skojarzenia.

|Właściwość|Opis|
|--------------|-----------------|
|**Kardynalność**|Określa, czy skojarzenie jest jeden do wielu lub jeden do jednego.|
|**Właściwość elementu podrzędnego**|Określa, czy można utworzyć właściwości nadrzędnej, czy jest kolekcja lub odwołanie do rekordów podrzędnych po stronie klucza obcego skojarzenia. Na przykład w przypadku skojarzenia między klientem a kolejności Jeśli **właściwość podrzędna** ustawiono **True**, właściwość o nazwie zamówienia jest tworzony w klasie nadrzędnej.|
|**Właściwość nadrzędna**|Właściwość klasy podrzędnej, który odwołuje się do skojarzoną klasę nadrzędną. Na przykład skojarzenia między klientem a kolejność właściwości o nazwie klienta, który odwołuje się do skojarzonego odbiorcy w celu jest tworzona w klasie kolejności.|
|**Właściwości uczestniczących**|Wyświetla właściwości skojarzenia oraz **wielokropka** przycisku (...), który otwiera ponownie **Edytor skojarzenia** okno dialogowe.|
|**Unikatowe**|Określa, czy obce kolumny docelowe mają ograniczenie unikatowości.|

## <a name="to-create-an-association-between-entity-classes"></a>Aby utworzyć skojarzenie między klasami jednostki

1.  Kliknij prawym przyciskiem myszy klasę jednostki, która reprezentuje klasy nadrzędnej skojarzenia, wskaż pozycję **Dodaj**, a następnie kliknij przycisk **skojarzenia**.

2.  Upewnij się, że zostały prawidłowo **klasy nadrzędnej** wybrano w **Edytor skojarzenia** okno dialogowe.

3.  Wybierz **klasy podrzędnej** w polu kombi.

4.  Wybierz **właściwości skojarzenia** dotyczących klas. Zwykle to mapuje relacji klucza obcego w bazie danych. Na przykład w powiązaniu klienci i zamówienia **właściwości skojarzenia** są CustomerID dla każdej klasy.

5.  Kliknij przycisk **OK** można utworzyć skojarzenia.

## <a name="see-also"></a>Zobacz także

- [LINQ do SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Wskazówki: Tworzenie klasy LINQ do SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metody DataContext (Projektanta obiektów relacyjnych)](../data-tools/datacontext-methods-o-r-designer.md)
- [Instrukcje: Reprezentacja kluczy podstawowych](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)