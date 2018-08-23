---
title: 'Porady: Zatwierdź zmiany w zestawie danych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataSet.AcceptChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], committing changes
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 40acd2a706ef7bc00ea1f90e51e90705be5658c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681338"
---
# <a name="how-to-commit-changes-in-a-dataset"></a>Porady: wykonywanie zmiany w zestawie danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po wprowadzeniu zmian do rekordów w zestawie danych, aktualizowania, wstawiania i usuwania rekordów zestawu danych obsługuje wersje pierwotnym i bieżącym rekordów. Ponadto, każdy wiersz w <xref:System.Data.DataRow.RowState%2A> przechowuje informacje o właściwości, czy rekordy są w stanie lub zostały zaktualizowane, wstawić lub usunięte. Informacje te są przydatne, gdy trzeba znaleźć określonej wersji wiersza. Zwykle otrzymamy podzbiór wszystkich zmienionych rekordów do wysłania do innego procesu. Aby uzyskać więcej informacji, zobacz [porady: pobieranie zmienione wiersze](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9). Po przetworzeniu zmienionych wierszy można zatwierdzić zmiany przez wywołanie metody `AcceptChanges` metody <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, lub <xref:System.Data.DataRow>. `AcceptChanges` Metoda jest wywoływana automatycznie podczas wywoływania metody aktualizacji [TableAdapter](../data-tools/tableadapter-overview.md) lub danych adaptera. Wywołaj `AcceptChanges` po przesłaniu zmiany w bazie danych.  
  
 Gdy wywołujesz <xref:System.Data.DataSet.AcceptChanges%2A> na <xref:System.Data.DataSet>, any <xref:System.Data.DataRow> obiekty nadal w trybie edycji pomyślnie zakończyć swoje zmiany. <xref:System.Data.DataRow.RowState%2A> Właściwości każdego <xref:System.Data.DataRow> zmienia także; <xref:System.Data.DataRowState> i <xref:System.Data.DataRowState> wierszy stają się <xref:System.Data.DataRowState>, i <xref:System.Data.DataRowState> wiersze zostaną usunięte.  
  
 Jeśli <xref:System.Data.DataSet> zawiera <xref:System.Data.ForeignKeyConstraint> obiektów i wywoływania <xref:System.Data.DataSet.AcceptChanges%2A> metoda również powoduje, że <xref:System.Data.AcceptRejectRule> zostaną wymuszone.  
  
### <a name="to-commit-changes-in-a-dataset"></a>Aby zatwierdzić zmiany w zestawie danych  
  
-   Wywołaj `AcceptChanges` metodę na jedną <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, lub <xref:System.Data.DataRow> do zatwierdzania zmian w tych obiektach.  
  
     Poniższy przykład pokazuje sposób wywoływania `AcceptChanges` metodę, aby zatwierdzić zmiany w `Customers` tabeli po zaktualizowaniu źródła danych:  
  
     [!code-csharp[VbRaddataEditing#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#11)]
     [!code-vb[VbRaddataEditing#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#11)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [Zapisywanie danych](../data-tools/saving-data.md)   
 [Porady: Pobieranie zmienionych wierszy](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9)