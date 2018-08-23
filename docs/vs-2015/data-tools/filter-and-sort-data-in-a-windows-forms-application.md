---
title: Filtrowanie i sortowanie danych w aplikacji Windows Forms | Dokumentacja firmy Microsoft
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
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e32e64672fc01f328643e78e572e12d57b751f39
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42685237"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrowanie i sortowanie danych w aplikacji Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [filtrowania i sortowania danych w aplikacji Windows Forms](https://docs.microsoft.com/visualstudio/data-tools/filter-and-sort-data-in-a-windows-forms-application).  
  
  
Filtrowanie danych przez ustawienie <xref:System.Windows.Forms.BindingSource.Filter%2A> właściwość wyrażeniem, które zwraca żądane rekordy.  
  
 Sortowanie danych przez ustawienie <xref:System.Windows.Forms.BindingSource.Sort%2A> właściwość na nazwę kolumny należy do sortowania; Dołącz `DESC` można sortować w kolejności malejącej lub dołączyć `ASC` sortowanie w kolejności rosnącej.  
  
> [!NOTE]
>  Jeśli aplikacja nie korzysta z <xref:System.Windows.Forms.BindingSource> składników, można filtrować i sortować dane przy użyciu <xref:System.Data.DataView> obiektów. Aby uzyskać więcej informacji, zobacz [DataView](http://msdn.microsoft.com/library/0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b).  
  
## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Aby filtrować dane za pomocą składnika BindingSource  
  
-   Ustaw <xref:System.Windows.Forms.BindingSource.Filter%2A> właściwość na wyrażenie, które mają być zwracane. Na przykład, poniższy kod zwraca klientom `CompanyName` który zaczyna się od "B":  
  
     [!code-csharp[VbRaddataDisplaying#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDisplaying#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#6)]  
  
## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Aby posortować dane za pomocą składnika BindingSource  
  
-   Ustaw <xref:System.Windows.Forms.BindingSource.Sort%2A> właściwość kolumnę, która ma zostać wykonane sortowanie. Na przykład, poniższy kod sortuje klientom na `CompanyName` kolumny w kolejności malejącej:  
  
     [!code-csharp[VbRaddataDisplaying#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDisplaying#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#7)]  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

