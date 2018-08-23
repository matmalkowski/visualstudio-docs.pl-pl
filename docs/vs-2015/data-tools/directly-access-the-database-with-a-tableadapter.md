---
title: Bezpośrednio dostęp do bazy danych za pomocą TableAdapter | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 689bc12129df82fb57bd0247ffa7f1e896aa4c92
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676748"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Bezpośredni dostęp do bazy danych za pomocą adaptera TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [bezpośrednio dostęp do bazy danych za pomocą TableAdapter](https://docs.microsoft.com/visualstudio/data-tools/directly-access-the-database-with-a-tableadapter).  
  
  
Oprócz `InsertCommand`, `UpdateCommand`, i `DeleteCommand`, TableAdapters są tworzone za pomocą metod, które można uruchamiać bezpośrednio w bazie danych. Te metody (`TableAdapter.Insert`, `TableAdapter.Update`, i `TableAdapter.Delete`) może być wywoływana można manipulować danymi bezpośrednio w bazie danych.  
  
 Jeśli nie chcesz utworzyć te metody bezpośrednie, ustaw TableAdapter `GenerateDbDirectMethods` właściwości `false` w **właściwości** okna. Wszelkie zapytania są dodawane do TableAdapter oprócz zapytanietableadapter głównym, są zapytania autonomicznych, które nie Generuj te dbdirect — metody.  
  
## <a name="sendcommandsdirectly-to-a-database"></a>Sendcommandsdirectly do bazy danych  
 Wywołaj metodę TableAdapter DbDirect, która wykonuje zadanie, które mają być osiągnięte.  
  
#### <a name="to-insert-new-records-directly-into-a-database"></a>Aby wstawić nowe rekordy bezpośrednio do bazy danych  
  
-   Wywołaj TableAdapter `Insert` jest metoda wartości dla każdej kolumny jako parametry. W poniższej procedurze użyto `Region` tabelę Northwind databaseas przykładem.  
  
    > [!NOTE]
    >  Jeśli nie masz dostępne wystąpienia, należy utworzyć wystąpienie TableAdapter, którego chcesz używać.  
  
     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]  
  
#### <a name="to-update-records-directly-in-a-database"></a>Do aktualizowania rekordów bezpośrednio w bazie danych  
  
-   Wywołaj TableAdapter `Update` jest metoda nowymi i oryginalnymi wartości dla każdej kolumny jako parametry.  
  
    > [!NOTE]
    >  Jeśli nie masz dostępne wystąpienia, należy utworzyć wystąpienie TableAdapter, którego chcesz używać.  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
#### <a name="to-delete-records-directly-from-a-database"></a>Do usuwania rekordów bezpośrednio z bazy danych  
  
-   Wywołaj TableAdapter `Delete` jest metoda wartości dla każdej kolumny jako parametry `Delete` metody. W poniższej procedurze użyto `Region` tabelę Northwind databaseas przykładem.  
  
    > [!NOTE]
    >  Jeśli nie masz dostępne wystąpienia, należy utworzyć wystąpienie TableAdapter, którego chcesz używać.  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wypełnij zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)

