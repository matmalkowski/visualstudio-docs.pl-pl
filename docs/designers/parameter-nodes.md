---
title: "Parametr węzłów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: da54db0b-3a3d-48dc-858c-7ac43aa04b13
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6c93a889ca1bfa911a9f0934302450f6c1ec5413
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="parameter-nodes"></a>Węzły parametrów
W projektancie programu do cieniowania parametru węzły reprezentują wejścia do programu do cieniowania, które są poza kontrolą aplikacji na podstawie na rysunku, na przykład, właściwości materiału, światła kierunkowe, pozycja kamery i czasu. Nie może zmienić te parametry z każdego wywołania rysunku, można użyć tego samego programu do cieniowania umożliwiają inny wygląd obiektu.  
  
## <a name="parameter-node-reference"></a>Węzeł odwołania do parametru  
  
|Węzeł|Szczegóły|Właściwości|  
|----------|-------------|----------------|  
|**Pozycja World aparatu**|Pozycja kamery w przestrzeni świata.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Pozycja kamery.|Brak|  
|**Kierunek światła**|Wektor definiujący kierunek padania światła ze źródła światła w przestrzeni świata.<br /><br /> Służy to do obliczenia udziału oświetlenia i odblasków w przestrzeni świata.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float3`<br /> Wektor od bieżącego piksela do źródła światła.|Brak|  
|**Materiał otoczenia**|Udział koloru rozpraszania bieżącego piksela przypisana do oświetlenia pośredniego.<br /><br /> Kolor rozpraszania piksel symuluje współdziałania oświetlenia nierównej powierzchni. Można użyć parametru materiałów otoczenia zbliżenie jak wspiera oświetlenia pośredniego w wyglądzie obiektów w świecie rzeczywistym.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Kolor rozpraszania bieżącego piksela, który jest z powodu pośredniego — to znaczy otoczenia — oświetlenia.|**Dostęp**<br /> **Publiczny** Aby włączyć właściwość należy ustawić w edytorze modeli; w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**<br /> Kolor rozpraszania bieżącego piksela, który jest z powodu pośredniego — to znaczy otoczenia — oświetlenia.|  
|**Rozpraszania materiału**|Kolor opisujący sposób rozpraszania przez bieżący piksel oświetlenia bezpośredniego.<br /><br /> Kolor rozpraszania piksel symuluje współdziałania oświetlenia nierównej powierzchni. Można użyć parametru rozproszone materiałów Aby zmienić sposób rozpraszania przez bieżący piksel oświetlenia bezpośredniego — to znaczy kierunkowe, punktowe i reflektor.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Kolor opisujący sposób rozpraszania przez bieżący piksel oświetlenia bezpośredniego.|**Dostęp**<br /> **Publiczny** Aby włączyć właściwość należy ustawić w edytorze modeli; w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**<br /> Kolor opisujący sposób rozpraszania przez bieżący piksel oświetlenia bezpośredniego.|  
|**Materiał emisji**|Udział koloru materiału bieżącego piksela przypisana do oświetlenia dostarczającego do samej siebie.<br /><br /> Służy to do symulowania świecącego obiektu; oznacza to, że obiekt, który sam wydziela światło. Powyższe nie ma wpływu na inne obiekty.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Udział koloru materiału bieżącego piksela, który jest wymagany do samodzielnie emitowanego oświetlenia.|**Dostęp**<br /> **Publiczny** Aby włączyć właściwość należy ustawić w edytorze modeli; w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**<br /> Udział koloru materiału bieżącego piksela, który jest wymagany do samodzielnie emitowanego oświetlenia.|  
|**Materiał odblasków**|Kolor opisujący sposób odbijania przez bieżący piksel oświetlenia bezpośredniego.<br /><br /> Koloru odblasków piksela symuluje współdziałania oświetlenia gładkiej, lustrzanej powierzchni. Można użyć parametru materiałów odblasków Aby zmienić sposób odbijania przez bieżący piksel oświetlenia bezpośredniego — to znaczy kierunkowe, punktowe i reflektor.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Kolor opisujący sposób odbijania przez bieżący piksel oświetlenia bezpośredniego.|**Dostęp**<br /> **Publiczny** umożliwia właściwości należy ustawić w edytorze modeli; w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**<br /> Kolor opisujący sposób odbijania przez bieżący piksel oświetlenia bezpośredniego.|  
|**Materiał odblasków zasilania**|Wartość skalarna opisująca intensywność światła odblasków.<br /><br /> Im większa odblasków zasilania, bardziej intensywny i dalekosiężną stają się światła odblasków.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float`<br /> Termin wykładniczej opisujący intensywność światła odblasków na bieżącego piksela.|**Dostęp**<br /> **Publiczny** Aby włączyć właściwość należy ustawić w edytorze modeli; w przeciwnym razie **prywatnej**.<br /><br /> **Wartość**<br /> Wykładnik definiujący intensywność światła odblasków na bieżącego piksela.|  
|**Czas znormalizowane**|Czas w sekundach znormalizowany do zakresu [0, 1], taki sposób, że osiągnięcie wartości 1, następuje zresetowanie na 0.<br /><br /> Służy to jako parametru w obliczeniach cieniowania, na przykład do animowania współrzędnych tekstury, wartości kolorów lub innych atrybutów.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float`<br /> Znormalizowany czas w sekundach.|Brak|  
|**Czas**|Czas w sekundach.<br /><br /> Służy to jako parametru w obliczeniach cieniowania, na przykład do animowania współrzędnych tekstury, wartości kolorów lub innych atrybutów.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float`<br /> Czas w sekundach.|Brak|