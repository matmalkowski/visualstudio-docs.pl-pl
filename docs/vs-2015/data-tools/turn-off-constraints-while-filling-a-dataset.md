---
title: Wyłączanie ograniczeń podczas zapełniania zestawu danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4b14830b7ed4922b4e383ef245c0366c184b606e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680573"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Wyłączanie ograniczeń podczas zapełniania zestawu danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wyłączanie ograniczeń podczas zapełniania zestawu danych](https://docs.microsoft.com/visualstudio/data-tools/turn-off-constraints-while-filling-a-dataset).  
  
  
Jeśli zestaw danych zawiera ograniczenia (np. ograniczenia foreign key), theycan zgłaszać błędy związane z kolejnością operacje, które są wykonywane względem zestawu danych. Na przykład podczas ładowania rekordów podrzędnych przed ich rekordów nadrzędnych loadingrelated można narusza ograniczenie i powodują wystąpienie błędu. Zaraz po załadowaniu podrzędnego rekordu ograniczenie sprawdza, czy rekord nadrzędny powiązane i zgłasza błąd.  
  
 Gdyby żaden mechanizm umożliwia zawieszenia tymczasowe ograniczenie błędu będzie uruchamiany za każdym razem, gdy próba załadowania rekordu do tabeli podrzędnej. Innym sposobem, aby wstrzymać wszystkie ograniczenia w zestawie danych jest <xref:System.Data.DataRow.BeginEdit%2A>, i <xref:System.Data.DataRow.EndEdit%2A> właściwości.  
  
> [!NOTE]
>  Zdarzenia walidacji (na przykład <xref:System.Data.DataTable.ColumnChanging> i<xref:System.Data.DataTable.RowChanging>) nie zostaną wywołane, gdy ograniczenia są wyłączone.  
  
### <a name="to-suspend-update-constraints-programmatically"></a>Aby programowo zawiesić Aktualizuj ograniczenia  
  
-   Poniższy przykład pokazuje, jak tymczasowo wyłączyć sprawdzanie w zestawie danych ograniczeń:  
  
     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]  
  
### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Zawieszenie ograniczenia aktualizacji za pomocą Projektanta obiektów Dataset  
  
1.  Otwórz swój zestaw danych w [tworzenie i edytowanie wpisanych zestawów danych](../data-tools/creating-and-editing-typed-datasets.md). Aby uzyskać więcej informacji, zobacz [porady: otwieranie zestawu w Projektancie obiektów Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  W **właściwości** oknie <xref:System.Data.DataSet.EnforceConstraints%2A> właściwość `false`.  
  
## <a name="see-also"></a>Zobacz też  
 [Wypełnij zestawów danych za pomocą adapterów TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Relacje w zestawach danych](../data-tools/relationships-in-datasets.md)

