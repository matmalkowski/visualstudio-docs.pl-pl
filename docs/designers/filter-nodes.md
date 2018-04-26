---
title: Węzły filtrów
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0cf0902847899f8796ac34765c66c79530248e81
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="filter-nodes"></a>Węzły filtru

W projektancie programu do cieniowania węzły filtru przekształcania danych wejściowych — na przykład próbkę koloru lub tekstury — w wartości koloru symboli. Wartości symboli kolorów te są często używane w przypadku renderowania photorealistic lub jako składników we inne efekty wizualne.

## <a name="filter-node-reference"></a>Odwołanie do węzła filtru

|Węzeł|Szczegóły|Właściwości|
|----------|-------------|----------------|
|**Rozmywa**|Rozmywa pikseli tekstury za pomocą funkcji Gaussa.<br /><br /> To umożliwia obniżenie szczegóły koloru lub szumu tekstury.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne teksela do testowania.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Wartość koloru rozmyty.|**tekstury**<br /> Rejestr tekstury skojarzony z próbnikiem używany podczas rozmycia.|
|**Zmniejsz nasycenie**|Zmniejsza ilość koloru w określonym kolorów.<br /><br /> Usunięcia koloru wartość koloru zbliża się do jego równoważnika na skali szarości.<br /><br /> **Dane wejściowe:**<br /><br /> `RGB`: `float3`<br /> Kolor Zmniejsz nasycenie.<br /><br /> `Percent`: `float`<br /> Procent koloru, aby usunąć, przeliczeniu na znormalizowaną wartość z zakresu [0, 1].<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float3`<br /> Kolor zmniejszonym.|**Jasności**<br /> Wagi nadawane składniki kolor czerwony, zielonemu i niebieskiemu.|
|**Wykrywanie krawędzi**|Wykrywa krawędzie tekstury za pomocą algorytmu krawędzi canny'ego. Krawędziach są wyświetlane jako białe; krawędziach — są wyświetlane jako czarne.<br /><br /> Możesz użyć tego do określenia krawędzi tekstury, dzięki czemu może używać dodatkowych efektów traktować pikseli na krawędzi.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne teksela do testowania.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Białe, jeśli teksela znajduje się na krawędzi; w przeciwnym razie czarny.|**tekstury**<br /> Rejestr tekstury skojarzony z próbnikiem używany podczas wykrywania krawędzi.|
|**Wyostrzania**|Wyostrza teksturę.<br /><br /> Możesz użyć tego, aby wyróżnić szczegółów tekstury.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne teksela do testowania.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Wartość koloru rozmyty.|**tekstury**<br /> Rejestr tekstury skojarzony z próbnikiem używany podczas wyostrzania.|