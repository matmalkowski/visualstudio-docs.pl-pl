---
title: Wyłączanie ograniczeń podczas zapełniania zestawu danych
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
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d128216f84228c9cd4946f9a38c6c1b7845f92f1
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117241"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Wyłączanie ograniczeń podczas zapełniania zestawu danych

Jeśli zestaw danych zawiera ograniczenia (np. ograniczenia foreign key), ich Zgłoś błędy związane z kolejnością operacje wykonywane względem zestawu danych. Na przykład ładowanie podrzędnych rekordów przed załadowaniem związane z rekordów nadrzędnych można narusza ograniczenie i spowodować wystąpienie błędu. Natychmiast po załadowaniu podrzędnego rekordu ograniczenie sprawdza rekord nadrzędny pokrewne i zgłasza błąd.

Jeśli nie było mechanizm umożliwia tymczasowe ograniczenie zawieszenie, błąd będzie uruchamiany za każdym razem, gdy próba załadowania rekordu do tabeli podrzędnej. Innym sposobem Wstrzymaj wszystkie ograniczenia zestawu danych jest z <xref:System.Data.DataRow.BeginEdit%2A>, i <xref:System.Data.DataRow.EndEdit%2A> właściwości.

> [!NOTE]
> Zdarzenia walidacji (na przykład <xref:System.Data.DataTable.ColumnChanging> i <xref:System.Data.DataTable.RowChanging>) nie zostanie wygenerowany, gdy ograniczenia są wyłączone.

## <a name="to-suspend-update-constraints-programmatically"></a>Aby wstrzymać programowo ograniczenia aktualizacji

-   Poniższy przykład przedstawia sposób tymczasowo wyłączyć sprawdzanie w zestawie danych ograniczeń:

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Aby wstrzymać ograniczenia aktualizacji za pomocą Projektanta obiektów Dataset

1.  Otwórz zestaw danych w **Projektant obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie zestawu danych w Projektancie obiektów Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  W **właściwości** ustaw <xref:System.Data.DataSet.EnforceConstraints%2A> właściwości `false`.

## <a name="see-also"></a>Zobacz także

- [Wypełnianie zbiorów danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Relacje w zestawach danych](../data-tools/relationships-in-datasets.md)