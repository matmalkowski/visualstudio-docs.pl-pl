---
title: Wyłączanie ograniczeń w czasie wypełniania zestawu danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e32aecbe10c9c02fec62240977b3f4e3a3338791
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Wyłączanie ograniczeń w czasie wypełniania zestawu danych
Jeśli zestaw danych zawiera ograniczenia (np. ograniczenia foreign key), ich Zgłoś błędy związane z kolejnością operacje wykonywane względem zestawu danych. Na przykład ładowanie podrzędnych rekordów przed załadowaniem związane z rekordów nadrzędnych można narusza ograniczenie i spowodować wystąpienie błędu. Natychmiast po załadowaniu podrzędnego rekordu ograniczenie sprawdza rekord nadrzędny pokrewne i zgłasza błąd.  
  
 Jeśli nie było mechanizm umożliwia tymczasowe ograniczenie zawieszenie, błąd będzie uruchamiany za każdym razem, gdy próba załadowania rekordu do tabeli podrzędnej. Innym sposobem Wstrzymaj wszystkie ograniczenia zestawu danych jest z <xref:System.Data.DataRow.BeginEdit%2A>, i <xref:System.Data.DataRow.EndEdit%2A> właściwości.  
  
> [!NOTE]
>  Zdarzenia walidacji (na przykład <xref:System.Data.DataTable.ColumnChanging> i<xref:System.Data.DataTable.RowChanging>) nie zostanie wygenerowany, gdy ograniczenia są wyłączone.  
  
### <a name="to-suspend-update-constraints-programmatically"></a>Aby wstrzymać programowo ograniczenia aktualizacji  
  
-   Poniższy przykład przedstawia sposób tymczasowo wyłączyć sprawdzanie w zestawie danych ograniczeń:  
  
     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]  
  
### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Aby wstrzymać ograniczenia aktualizacji za pomocą Projektanta obiektów Dataset  
  
1.  Otwórz zestaw danych w **Projektant obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie zestawu danych w Projektancie obiektów Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  W **właściwości** ustaw <xref:System.Data.DataSet.EnforceConstraints%2A> właściwości `false`.  
  
## <a name="see-also"></a>Zobacz też  
 [Wypełnianie zbiorów danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Relacje w zestawach danych](../data-tools/relationships-in-datasets.md)