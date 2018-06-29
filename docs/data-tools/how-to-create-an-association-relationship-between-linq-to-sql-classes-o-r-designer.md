---
title: Tworzenie relacji między klasy LINQ do SQL za pomocą Projektanta obiektów relacyjnych
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d247603e14f431e44aa7c1589ba2ecd7463fac02
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089532"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Porady: Tworzenie skojarzenia między klasy LINQ do SQL (Projektanta obiektów relacyjnych)
Skojarzenia między klasami jednostki w [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] są podobne do relacji między tabelami w bazie danych. Można utworzyć skojarzenia między klasami jednostki przy użyciu **Edytor skojarzenia** okno dialogowe.

Korzystając z należy wybrać klasy nadrzędnej i podrzędnej klasy **Edytor skojarzenia** okno dialogowe, aby utworzyć skojarzenie. Klasa nadrzędna jest klasa jednostki, która zawiera klucz podstawowy; klasy podrzędnej jest klasa jednostki, która zawiera klucz obcy. Na przykład, jeśli klas jednostek zostały utworzone, które są mapowane na `Northwind Customers` i `Orders` tabel, `Customer` klasy będzie klasy nadrzędnej i `Order` klasy będzie klasy podrzędnej.

> [!NOTE]
>  Przeciągnięcie tabel z **Eksploratora serwera** lub **Eksploratora bazy danych** na **Projektant obiektów relacyjnych** (**Projektanta obiektów relacyjnych**), skojarzenia są tworzone automatycznie w oparciu o istniejące relacje klucza obcego w bazie danych.

## <a name="association-properties"></a>Właściwości skojarzenia
Po utworzeniu skojarzenia, po wybraniu skojarzenia w **Projektanta obiektów relacyjnych**, brak niektórych właściwości można skonfigurować w **właściwości** okna. (Skojarzenie jest linii między powiązanymi klasami). Poniższa tabela zawiera opisy właściwości skojarzenia.

|Właściwość|Opis|
|--------------|-----------------|
|**Kardynalność**|Określa, czy skojarzenie jest jeden do wielu lub jeden do jednego.|
|**Właściwość elementu podrzędnego**|Określa, czy można utworzyć właściwości nadrzędnej, czy jest kolekcja lub odwołanie do rekordów podrzędnych po stronie klucza obcego skojarzenia. Na przykład w przypadku skojarzenia między `Customer` i `Order`, jeśli **właściwość podrzędna** ma ustawioną wartość **True**, właściwość o nazwie `Orders` jest tworzony w klasie nadrzędnej.|
|**Właściwość nadrzędna**|Właściwość klasy podrzędnej, który odwołuje się do skojarzoną klasę nadrzędną. Na przykład w przypadku skojarzenia między `Customer` i `Order`, właściwość o nazwie `Customer` odwołującą klienta skojarzone zamówienia jest tworzona na `Order` klasy.|
|**Właściwości uczestniczących**|Wyświetla właściwości skojarzenia oraz **wielokropka** przycisku (...), który otwiera ponownie **Edytor skojarzenia** okno dialogowe.|
|**Unikatowe**|Określa, czy obce kolumny docelowe mają ograniczenie unikatowości.|

## <a name="to-create-an-association-between-entity-classes"></a>Aby utworzyć skojarzenie między klasami jednostki

1.  Kliknij prawym przyciskiem myszy klasę jednostki, która reprezentuje klasy nadrzędnej skojarzenia, wskaż pozycję **Dodaj**, a następnie kliknij przycisk **skojarzenia**.

2.  Upewnij się, że zostały prawidłowo **klasy nadrzędnej** wybrano w **Edytor skojarzenia** okno dialogowe.

3.  Wybierz **klasy podrzędnej** w polu kombi.

4.  Wybierz **właściwości skojarzenia** dotyczących klas. Zwykle to mapuje relacji klucza obcego w bazie danych. Na przykład w `Customers` i `Orders` skojarzenia, **właściwości skojarzenia** są `CustomerID` dla każdej klasy.

5.  Kliknij przycisk **OK** można utworzyć skojarzenia.

## <a name="see-also"></a>Zobacz także

- [LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Wskazówki: Tworzenie LINQ w klasach SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metody DataContext (Projektanta obiektów relacyjnych)](../data-tools/datacontext-methods-o-r-designer.md)
- [Porady: reprezentuje kluczy podstawowych](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)