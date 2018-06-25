---
title: Filtrowanie i sortowanie danych w aplikacji Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 21ebae03dd2ba58a751a839f5e3151654faa39e0
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757598"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrowanie i sortowanie danych w aplikacji Windows Forms
Filtrowanie danych przez ustawienie <xref:System.Windows.Forms.BindingSource.Filter%2A> właściwości wyrażenia ciągu, która zwraca odpowiednie rekordy.

 Sortowanie danych przez ustawienie <xref:System.Windows.Forms.BindingSource.Sort%2A> dla właściwości Nazwa kolumny, na którym mają być sortowane; Dołącz `DESC` do sortowania w kolejności malejącej, lub Dołącz `ASC` do sortowania w porządku rosnącym.

> [!NOTE]
>  Jeśli aplikacja nie używać <xref:System.Windows.Forms.BindingSource> składników, można filtrować i sortować dane przy użyciu <xref:System.Data.DataView> obiektów. Aby uzyskać więcej informacji, zobacz [DataViews](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Aby filtrować dane za pomocą składnika BindingSource

-   Ustaw <xref:System.Windows.Forms.BindingSource.Filter%2A> właściwości wyrażenie, które chcesz przywrócić. Na przykład następujący kod zwraca klientów z `CompanyName` zaczynającym się znakiem "B":

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Aby posortować dane za pomocą składnika BindingSource

-   Ustaw <xref:System.Windows.Forms.BindingSource.Sort%2A> właściwości do sortowania na kolumny. Na przykład następujący kod sortuje klientów na `CompanyName` kolumny w kolejności malejącej:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Zobacz także

- [Powiązywanie formantów z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)