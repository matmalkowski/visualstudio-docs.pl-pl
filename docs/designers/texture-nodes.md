---
title: "Texture węzłów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7df5ef3-dd4f-4964-9d96-34e0e180515e
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 97962debc24b9e8bff3d4daaa7b632db775c2476
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="texture-nodes"></a>Węzły tekstury
W projektancie programu do cieniowania węzłów tekstury przykładowe różne typy tekstury i mają geometrię i utworzyć lub Przekształć współrzędnych tekstury. Tekstury Podaj kolorów i oświetlenia szczegółów w obiektach.  
  
## <a name="texture-node-reference"></a>Odwołanie do węzła tekstury  
  
|Węzeł|Szczegóły|Właściwości|  
|----------|-------------|----------------|  
|**Próbki mapy Sześciennej**|Pobiera próbkę koloru z mapy sześciennej na określonych współrzędnych.<br /><br /> Można użyć mapy sześciennej, aby udostępnić szczegóły koloru na potrzeby efektów odbicia lub aby zastosować dla kulistego obiektu z mniejszymi zniekształceniami niż tekstury 2-D tekstury.<br /><br /> **Dane wejściowe:**<br /><br /> `UVW`: `float3`<br /> Wektor określający lokalizację w module tekstury, gdzie próbki. Gdzie to wektor przecina modułu pobraniu próbki.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Przykład kolorów.|**Tekstury**<br /> Rejestr tekstury skojarzony z próbnikiem.|  
|**Próbki mapy normalnej**|Pobiera próbkę normalną z mapy normalnej 2-D na określonych współrzędnych<br /><br /> Można użyć mapy normalnej do symulowania wyglądu dodatkowych szczegółów geometrycznych na powierzchni obiektu. Mapy normalne zawierają spakowane dane, które reprezentują wektor jednostki, a nie dane koloru<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne, w którym próbki.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float3`<br /> Przykład normalnego.|**Dostosowanie osi**<br /> Współczynnik używany do dostosowania skrętności dla próbki mapy normalnej.<br /><br /> **Tekstury**<br /> Rejestr tekstury skojarzony z próbnikiem.|  
|**Przesuwanie UV**|Miednice określonego tekstury koordynuje w funkcji czasu.<br /><br /> Służy to do przesunięcia tekstury lub mapy normalnej po powierzchni obiektu.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne, aby kadrować.<br /><br /> `Time`: `float`<br /> Długość czasu, aby kadrować, w sekundach.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float2`<br /> Współrzędne panned.|**Szybkość X**<br /> Liczba tekseli przesuwanych wzdłuż osi x na sekundę.<br /><br /> **Szybkość Y**<br /> Liczba tekseli przesuwanych wzdłuż osi y na sekundę.|  
|**Paralaksy UV**|Powoduje przemieszczenie współrzędnych tekstury określona w funkcji wysokości i kąta widzenia.<br /><br /> Spowoduje to utworzenie efekt nosi nazwę *mapowanie równoległe*, lub mapowanie przemieszczenia wirtualnego. Można go użyć do utworzenia iluzji głębi w przypadku płaskiej powierzchni.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne się przemieścić.<br /><br /> `Height`: `float`<br /> Wartość heightmap, z którym skojarzony jest `UV` współrzędnych.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float2`<br /> Współrzędne przesuniętej.|**Głębokość płaszczyzny**<br /> Głębokość odniesienia dla efektu paralaksy. Domyślna wartość to 0,5. Mniejsze wartości powodują podniesienie tekstury; większe jej zapadanie w powierzchnię.<br /><br /> **Głębokość skali**<br /> Skala efekt paralaksy. Dzięki temu bardziej lub mniej wyraźnego głębi. Typowe wartości z zakresu od 0,02 do 0,1.|  
|**Obróć UV**|Obraca współrzędnych tekstury określonego wokół punktu centralnego w funkcji czasu.<br /><br /> Służy to do obrócenia tekstury lub mapy normalnej na powierzchni obiektu.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne obrotu.<br /><br /> `Time`: `float`<br /> Długość czasu, aby kadrować, w sekundach.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float2`<br /> Obrócony współrzędnych.|**Centrum X**<br /> Współrzędna x definiująca środek obrotu.<br /><br /> **Centrum Y**<br /> Współrzędna y definiująca środek obrotu.<br /><br /> **Szybkość**<br /> Kąt w radianach, przez który Tekstura obraca się w ciągu sekundy.|  
|**Współrzędnej tekstury**|Współrzędne tekstury bieżącego piksela.<br /><br /> Współrzędne tekstury są określane przez interpolacji między atrybutów współrzędnych tekstury pobliskich wierzchołków. Można je traktować jako pozycję bieżącego piksela w przestrzeni tekstury.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float2`<br /> Współrzędne tekstury.|Brak|  
|**Wymiarów tekstury**|Wyprowadza wysokość i szerokość mapy tekstury 2-D.<br /><br /> Należy wziąć pod uwagę wysokość i szerokość tekstury w programu do cieniowania umożliwia wymiarów tekstury.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float2`<br /> Szerokość i wysokość tekstury, wyrażony jako wektora. Szerokość znajduje się w pierwszym elementem wektora. Wysokość jest przechowywany w drugiego elementu.|**Tekstury**<br /> Rejestr tekstury skojarzony z wymiarów tekstury.|  
|**Deltę Teksela**|Generuje delta (odległość) między tekseli mapy tekstury 2-D.<br /><br /> Deltę teksela służy do próbkowania sąsiadujących wartości teksela programu do cieniowania.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float2`<br /> Delta (odległość) z teksela do następnego teksela (przenoszenie przekątnej, w tym kierunku dodatnią), wyrażone jako wektor przestrzeni tekstury znormalizowana. Pochodzi z pozycji wszystkich tekseli sąsiednich, selektywnie ignorowanie lub Negacja współrzędne U lub V różnicowej.|**Tekstury**<br /> Rejestr tekstury skojarzony z delty teksela.|  
|**Przykładowe tekstury**|Pobiera próbkę koloru z mapy tekstury 2-D na określonych współrzędnych.<br /><br /> Można użyć mapy tekstury, aby udostępnić szczegóły koloru na powierzchni obiektu.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne, w którym próbki.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Przykład kolorów.|**Tekstury**<br /> Rejestr tekstury skojarzony z próbnikiem.|