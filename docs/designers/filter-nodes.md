---
title: "Filtruj węzły | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0a2ddcccfb3499be583b4965bd45352b63b0be8e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="filter-nodes"></a>Węzły filtrów
W projektancie programu do cieniowania węzły filtru przekształcania danych wejściowych — na przykład próbkę koloru lub tekstury — w wartości koloru symboli. Wartości symboli kolorów te są często używane w przypadku renderowania photorealistic lub jako składników we inne efekty wizualne.  
  
## <a name="filter-node-reference"></a>Odwołanie do węzła filtru  
  
|Węzeł|Szczegóły|Właściwości|  
|----------|-------------|----------------|  
|**Rozmywa**|Rozmywa pikseli tekstury za pomocą funkcji Gaussa.<br /><br /> To umożliwia obniżenie szczegóły koloru lub szumu tekstury.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne teksela do testowania.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Wartość koloru rozmyty.|**Tekstury**<br /> Rejestr tekstury skojarzony z próbnikiem używany podczas rozmycia.|  
|**Zmniejsz nasycenie**|Zmniejsza ilość koloru w określonym kolorów.<br /><br /> Usunięcia koloru wartość koloru zbliża się do jego równoważnika na skali szarości.<br /><br /> **Dane wejściowe:**<br /><br /> `RGB`: `float3`<br /> Kolor Zmniejsz nasycenie.<br /><br /> `Percent`: `float`<br /> Procent koloru, aby usunąć, przeliczeniu na znormalizowaną wartość z zakresu [0, 1].<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float3`<br /> Kolor zmniejszonym.|**Jasności**<br /> Wagi nadawane składniki kolor czerwony, zielonemu i niebieskiemu.|  
|**Wykrywanie krawędzi**|Wykrywa krawędzie tekstury za pomocą algorytmu krawędzi canny'ego. Krawędziach są wyświetlane jako białe; krawędziach — są wyświetlane jako czarne.<br /><br /> Możesz użyć tego do określenia krawędzi tekstury, dzięki czemu może używać dodatkowych efektów traktować pikseli na krawędzi.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne teksela do testowania.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Białe, jeśli teksela znajduje się na krawędzi; w przeciwnym razie czarny.|**Tekstury**<br /> Rejestr tekstury skojarzony z próbnikiem używany podczas wykrywania krawędzi.|  
|**Wyostrzania**|Wyostrza teksturę.<br /><br /> Możesz użyć tego, aby wyróżnić szczegółów tekstury.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne teksela do testowania.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Wartość koloru rozmyty.|**Tekstury**<br /> Rejestr tekstury skojarzony z próbnikiem używany podczas wyostrzania.|