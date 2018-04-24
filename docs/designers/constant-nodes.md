---
title: Stałe węzły
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: 2c798a50-a2d7-459b-9879-ad4ad8290c9b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df41815f7f824468babd2fc0bbd9bc97595e3ddb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="constant-nodes"></a>Stałe węzły

W projektancie programu do cieniowania stałych węzły reprezentują wartości literałów i interpolowane atrybuty wierzchołków w obliczeniach cieniowania pikseli. Ponieważ wierzchołek atrybuty są interpolowane — różni się od tak, dla każdego piksela — każde wystąpienie programu do cieniowania pikseli odbiera innej wersji stałej. Dzięki temu każdego piksela unikatowego wyglądu.

## <a name="vertex-attribute-interpolation"></a>Interpolacji atrybutu wierzchołków

Obraz scenę 3D w grę, aplikacji lub zostało utworzone przez ze sobą matematycznie Przekształcanie liczba obiektów — które są definiowane przez wierzchołków wierzchołka i atrybuty pierwotnych definicje — do na ekranie pikseli. Wszystkie informacje, które są wymagane, aby nadać jej unikatowego wyglądu piksel jest dostarczany za pomocą wierzchołka atrybuty, które są ze sobą mieszane zgodnie z bliskości piksela różnych wierzchołki wchodzące w skład jego *pierwotnych*. Podstawowy jest elementem renderowania podstawowego; oznacza to prosty kształtu, takie jak punkt, wiersza lub trójkąt. Piksel jest bardzo bliski co najmniej jeden wierzchołki otrzymuje stałe, które są niemal identyczne z tym wierzchołków, ale pikseli, który ma równomiernie między wierzchołki podstawowy otrzymuje stałe, które są średnią tych wierzchołków. W programowaniu grafiki, stałe, które odbierają pikseli są określane jako *interpolowane*. Dostarcza dane stałej do pikseli w ten sposób tworzy bardzo wysokiej jakości wizualnej i w tym samym czasie powoduje zmniejszenie ilości miejsca i przepustowości.

Mimo że każde wystąpienie programu do cieniowania pikseli odbiera tylko jeden zestaw wartości stałych i nie można zmienić tych wartości, wystąpień różne cieniowania pikseli odbierać różne zestawy danych stałej. Ten projekt umożliwia programu do cieniowania do generowania danych wyjściowych kolorów dla każdego piksela element pierwotny.

## <a name="constant-node-reference"></a>Odwołanie do węzła stałej

|Węzeł|Szczegóły|Właściwości|
|----------|-------------|----------------|
|**Wektor kamery**|Wektor prowadzący od bieżącego piksela do kamery w przestrzeni świata.<br /><br /> Możesz użyć tego do obliczenia odbić w przestrzeni świata.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Wektor od bieżącego piksela do kamery.|Brak|
|**Stała kolorów**|Wartość stałą koloru.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Wartość koloru.|**Output**<br /> Wartość koloru.|
|**Stała**|Stała wartość skalarną.<br /><br /> **Output**<br /><br /> `Output`: `float`<br /> Wartość skalarną.|**Output**<br /> Wartość skalarną.|
|**Stała 2D**|Stała wektora z dwoma składowymi.<br /><br /> **Output**<br /><br /> `Output`: `float2`<br /> Wartość wektora.|**Output**<br /> Wartość wektora.|
|**Stała 3D**|Wektor z trzema składowymi stałą.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Wartość wektora.|**Output**<br /> Wartość wektora.|
|**Stała 4D**|Stała czterema składowymi wektora.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Wartość koloru.|**Output**<br /> Wartość wektora.|
|**Pozycja znormalizowane**|Pozycja bieżącego piksela wyrażona we współrzędnych urządzenia znormalizowaną.<br /><br /> Współrzędna x i współrzędna y mają wartości z zakresu [-1, 1], Współrzędna z ma wartość z zakresu [0, 1], i w składnika zawiera głębokość punktu w przestrzeni widoku; w nie jest znormalizowana.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Pozycja bieżącego piksela.|Brak|
|**Kolor punktu**|Kolor rozpraszania bieżącego piksela jest kombinacją materiału rozpraszania koloru i wierzchołków atrybutów koloru.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Kolor rozpraszania bieżącego piksela.|Brak|
|**Głębokość punktu**|Głębokość bieżącego piksela w przestrzeni widoku.<br /><br /> **Output**<br /><br /> `Output`: `float`<br /> Głębokość bieżącego piksela.|Brak|
|**Głębokość punktu znormalizowane**|Głębokość bieżącego piksela wyrażona we współrzędnych urządzenia znormalizowaną.<br /><br /> Wynik zawiera wartość z zakresu [0, 1].<br /><br /> **Output**<br /><br /> `Output`: `float`<br /> Głębokość bieżącego piksela.|Brak|
|**Pozycja ekranu**|Pozycja bieżącego piksela wyrażona w współrzędne ekranu.<br /><br /> Współrzędne ekranu są oparte na bieżącego okienka ekranu. X i y składników zawiera współrzędne ekranu, składnik z zawiera głębokość znormalizowany do zakresu [0, 1], i w składnik zawiera głębokość w przestrzeni widoku.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Pozycja bieżącego piksela.|Brak|
|**Normalna powierzchni**|Normalna powierzchni bieżącego piksela w przestrzeni obiektów.<br /><br /> Służy to do obliczenia udziału oświetlenia i odbić w przestrzeni obiektów.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Normalna powierzchni bieżącego piksela.|Brak|
|**Wektor kamery przestrzeni stycznej**|Wektor prowadzący od bieżącego piksela do kamery w przestrzeni stycznej.<br /><br /> Możesz użyć tego do obliczenia odbić w przestrzeni stycznej.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Wektor od bieżącego piksela do kamery.|Brak|
|**Kierunek światła przestrzeni stycznej**|Wektor definiujący kierunek padania światła ze źródła światła w przestrzeni stycznej bieżącego piksela.<br /><br /> Służy to do obliczenia udziału oświetlenia i odblasków w przestrzeni stycznej.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float3`<br /> Wektor od bieżącego piksela do źródła światła.|Brak|
|**Normalny świata**|Normalna powierzchni bieżącego piksela w przestrzeni świata.<br /><br /> Służy to do obliczenia udziału oświetlenia i odbić w przestrzeni świata.<br /><br /> **Output**<br /><br /> `Output`: `float3`<br /> Normalna powierzchni bieżącego piksela.|Brak|
|**Pozycja świata**|Pozycja bieżącego piksela w przestrzeni świata.<br /><br /> **Output**<br /><br /> `Output`: `float4`<br /> Pozycja bieżącego piksela.|Brak|