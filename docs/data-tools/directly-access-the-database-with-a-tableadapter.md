---
title: Bezpośredni dostęp do bazy danych za pomocą adaptera TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 53d4b2e75be288422300122d5ef9f523068dd9fc
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756457"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Bezpośredni dostęp do bazy danych za pomocą adaptera TableAdapter
Oprócz `InsertCommand`, `UpdateCommand`, i `DeleteCommand`, TableAdapters są tworzone za pomocą metod, które mogą być uruchamiane bezpośrednio w bazie danych. Te metody można wywołać (`TableAdapter.Insert`, `TableAdapter.Update`, i `TableAdapter.Delete`) do manipulowania bezpośrednio w bazie danych.

 Jeśli nie chcesz utworzyć te metody bezpośredniego, należy ustawić element TableAdapter `GenerateDbDirectMethods` właściwości `false` w **właściwości** okna. Wszelkie zapytania są dodawane do TableAdapter oprócz zapytanietableadapter głównym, są autonomiczne zapytań, które nie generują one `DbDirect` metody.

## <a name="send-commands-directly-to-a-database"></a>Wysyłanie poleceń, bezpośrednio do bazy danych
 Wywołaj element TableAdapter `DbDirect` metodę, która wykonuje zadanie próbujesz osiągnąć.

#### <a name="to-insert-new-records-directly-into-a-database"></a>Aby wstawić nowe rekordy bezpośrednio do bazy danych

-   Wywołaj element TableAdapter `Insert` metody przekazywanie wartości dla każdej kolumny jako parametrów. W poniższej procedurze użyto `Region` tabeli w bazie danych Northwind jako przykład.

    > [!NOTE]
    >  Jeśli nie masz wystąpienie, które są dostępne, można utworzyć wystąpienia TableAdapter, którego chcesz używać.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

#### <a name="to-update-records-directly-in-a-database"></a>Do aktualizowania rekordów bezpośrednio w bazie danych

-   Wywołaj element TableAdapter `Update` metody, przekazując nowy i oryginalne wartości dla każdej kolumny jako parametry.

    > [!NOTE]
    >  Jeśli nie masz wystąpienie, które są dostępne, można utworzyć wystąpienia TableAdapter, którego chcesz używać.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

#### <a name="to-delete-records-directly-from-a-database"></a>Aby usunąć rekordy bezpośrednio z bazy danych

-   Wywołaj element TableAdapter `Delete` metody przekazywanie wartości dla każdej kolumny jako parametry `Delete` metody. W poniższej procedurze użyto `Region` tabeli w bazie danych Northwind jako przykład.

    > [!NOTE]
    >  Jeśli nie masz wystąpienie, które są dostępne, można utworzyć wystąpienia TableAdapter, którego chcesz używać.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>Zobacz także

- [Wypełnianie zbiorów danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)