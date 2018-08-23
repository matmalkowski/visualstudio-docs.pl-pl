---
title: Operatory logiczne w wyrażeniach wyszukiwania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0cf55bbdc025b4aabd13f7ded72c2ea69386a61b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42630227"
---
# <a name="logical-operators-in-search-expressions"></a>Operatory logiczne w wyrażeniach wyszukiwania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [operatory logiczne w wyrażeniach wyszukiwania](https://docs.microsoft.com/visualstudio/ide/logical-operators-in-search-expressions).  
  
Za pomocą operatorów logicznych, można uściślić wyszukiwanie zawartości, tworząc bardziej złożonych wyszukiwania z tymi prostsze. Jak pokazano w poniższej tabeli, operatory logiczne Określanie wielu warunków wyszukiwania powinny być one łączone w zapytaniu wyszukiwania.  
  
> [!IMPORTANT]
>  Operatory logiczne należy wprowadzić wielkimi literami dla aparatu wyszukiwania, rozpoznawał.  
  
|Aby wyszukać|Zastosowanie|Przykład|Wynik|  
|-------------------|---------|-------------|------------|  
|Oba warianty pojęć w ten sam temat|AND|dib i palety|Tematy, które zawierają "dib" i "palety".|  
|Albo termin w temacie|LUB|rastrowych wektor OR|Tematy, które zawierają "rastrowych" lub "vector".|  
|Pierwszy okres bez drugi warunek w ten sam temat|NIE|"system operacyjny" nie DOS|Tematy, które zawierają "system operacyjny", ale nie "DOS".|  
|Oba warianty pojęć blisko siebie w temacie|W POBLIŻU|użytkownik w pobliżu jądra|Tematy zawierające "user" w pobliżu "jądra".|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady dotyczące wyszukiwania pełnotekstowego](../ide/full-text-search-tips.md)   
 [Lokalizowanie informacji](../ide/locate-information.md)



