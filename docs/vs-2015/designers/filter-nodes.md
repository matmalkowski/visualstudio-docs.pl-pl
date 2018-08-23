---
title: Filtrując węzły | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2789676505588c2041abfd876a228fc456ee3607
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682123"
---
# <a name="filter-nodes"></a>Węzły filtrów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [węzły filtru](https://docs.microsoft.com/visualstudio/designers/filter-nodes).  
  
W projektancie programu do cieniowania węzły filtru przekształcania danych wejściowych — na przykład próbkę koloru lub tekstury — na wartość koloru symboli. Te wartości kolorów symboli są często używane w innych — gdy chodzi o fotorealistyczne renderowanie, lub jako składników w innych efektów wizualnych.  
  
## <a name="filter-node-reference"></a>Odwołanie do węzła filtru  
  
|Węzeł|Szczegóły|Właściwości|  
|----------|-------------|----------------|  
|**Rozmycie**|Rozmywa pikseli tekstury za pomocą funkcji Gaussa.<br /><br /> Możesz użyć tego zmniejszenie szczegóły koloru lub szumu tekstury.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne texel do testowania.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Wartość koloru rozmyte.|**Tekstury**<br /> Rejestr tekstury skojarzony z próbnikiem używany podczas Rozmycie.|  
|**Zmniejszanie nasycenia**|Zmniejsza ilość koloru w określony kolor.<br /><br /> Usunięcia koloru wartość koloru zbliża się odpowiadającą jej równoważnika na skali.<br /><br /> **Dane wejściowe:**<br /><br /> `RGB`: `float3`<br /> Zmniejsz nasycenie koloru.<br /><br /> `Percent`: `float`<br /> Procent kolor, aby usunąć, wyrażone jako znormalizowaną wartość z zakresu [0, 1].<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float3`<br /> Nasycony kolor.|**Jasności**<br /> Wagi, które są określone dla składników koloru czerwonego, zielonego i niebieskiego.|  
|**Wykrywanie krawędzi**|Wykrywa krawędzie tekstury za pomocą wykrywanie krawędzi Canny'ego. Pikseli na krawędzi są wyświetlane jako biały; pikseli na krawędzi nie są wyświetlane jako czarny.<br /><br /> Służy to do określenia krawędzi tekstury, dzięki czemu można użyć dodatkowych efektów traktowanie pikseli na krawędzi.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne texel do testowania.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Białe, jeśli teksela znajduje się na krawędzi; w przeciwnym razie czarny.|**Tekstury**<br /> Rejestr tekstury skojarzony z próbnikiem używany podczas wykrywania krawędzi.|  
|**Doskonalenie**|Wyostrza teksturę.<br /><br /> Możesz użyć tego, aby wyróżnić szczegółów tekstury.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne texel do testowania.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Wartość koloru rozmyte.|**Tekstury**<br /> Rejestr tekstury skojarzony z próbnikiem używany podczas wyostrzania.|



