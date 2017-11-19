---
title: "Debugowanie — wizualizacji danych"
description: "Debugowanie jest typowe i konieczne, część programowania. Visual Studio for Mac zawiera całego zestawu funkcji Łatwe debugowanie. W tym artykule analizuje wizualizacji danych, które mogą być wyświetlane podczas sprawdzania obiektów w debugerze."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-debug
ms.assetid: 527E6BEC-EF15-4002-ACB5-62AE1C16F6B7
ms.openlocfilehash: 5f1eda5ccf6f308c626d525bbe7069a84ce3154b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="data-visualizations"></a>Wizualizacji danych

Visual Studio for Mac obsługuje interfejs użytkownika debugera, dzięki czemu wizualizacje wartości zmiennej, pole lub właściwość podczas debugowania. Wizualizatory tych danych Pokaż rozszerzona wersja danych i umożliwiają deweloperom sprawdzić znane struktur, na przykład wyświetlanie koloru struktury kolorów.

Wizualizatory w debugowania **lokalnego** konsoli można wyświetlić, klikając ikonę w wersji zapoznawczej, która pojawia się po prawej stronie wartości, gdy użytkownik znajduje się nad wiersz:

 ![Konsola lokalnego](media/data-visualizations-image9.png)

Na poniższej liście wygląda na wiele nowych wizualizacji dostępne podczas debugowania w programie Visual Studio dla komputerów Mac.

## <a name="point"></a>punkt
Punkt/PointF lub CGPoint w systemie iOS i Mac, spowoduje, że jako krotki zawierające wartości X i Y w konsoli debugowania:

 ![Punkt wizualizacji](media/data-visualizations-image10.png)

## <a name="size"></a>Rozmiar
Rozmiar/SizeF lub CGSize w systemie iOS i Mac, spowoduje, że jako prostokąta. Jest rysowane przez skalowanie do momentu wymiar rozwoju poza 250, w którym są skalowane prostokąt z największy wymiar jako 250:

![Rozmiar wizualizacji](media/data-visualizations-image11.png)


## <a name="rectangle"></a>Prostokąt
Prostokąt/RectangleF lub CGRect w systemie iOS i Mac, zostanie wyświetlone wymiary i pochodzenia. Podobnie jak rozmiar, jego jest rysowana na dużą skalę, dopóki wymiar rozwoju poza 250:

 ![Prostokąt wizualizacji](media/data-visualizations-image12.png)

## <a name="coordinate"></a>Współrzędna
Współrzędne są kreślone na mapie, z lokalizacją przypięty do Centrum:

![Współrzędna wizualizacji](media/data-visualizations-image13.png)

## <a name="color"></a>Kolor
Spowoduje to wyświetlenie właściwości UIColor, CGColor i kolor przedstawiające Podgląd koloru, składniki RGBA Hue-nasycenie-jasności i szesnastkowej wartości koloru:

![Kolor wizualizacji](media/data-visualizations-image14.png)


## <a name="images"></a>Obrazy

Nośniki będzie renderowany Aby skalować, aby maksymalny rozmiar 250 i będą skalowane w celu dopasowania obrazu przekracza 250:

 ![Obraz wizualizacji](media/data-visualizations-image15.png)


## <a name="bezier-curves"></a>Krzywe Beziera

Wizualizator spowoduje wyświetlenie `NSBezierPath`:

![Wizualizacja krzywej Beziera](media/data-visualizations-image16.png)


## <a name="string"></a>String

W pełni bez Podgląd pojawi się ciąg o mniej niż 100 znaków. Ciągi dłużej pojawi się w całości w wersji zapoznawczej. Ciągi są edytowalne i wizualizatora towarzyszy przycisk Edytuj, umożliwiając wartość ciągu do edycji w podglądzie lub w wartości edytor ciągów, pokazano poniżej:

![Ciąg wizualizacji](media/data-visualizations-image17.png)

### <a name="small-strings"></a>Ciągi małych:
![Ciąg małych wizualizacji](media/data-visualizations-image18.png)]

### <a name="medium-length-strings"></a>Średnia długość ciągów:
![Średnia ciąg wizualizacji](media/data-visualizations-image19.png)

### <a name="editor"></a>Edytor:

 ![Edytor wizualizacji](media/data-visualizations-image21.png)

## <a name="ienumerable"></a>Interfejs IEnumerable

Interfejs IEnumerable wylicza wszystkie wartości. wartości każdego z nich można wyświetlić, klikając **Pokaż** przycisku wartości. Opcja IEnumerable nie będą wyświetlane wartości dla obiektów, takich jak `Array`, `ArrayList`, `List<>`, `Dictionary<,>` te mają własne wizualizatory debugera.

![Wizualizacja IEnumerable](media/data-visualizations-image22.png)

## <a name="other-visualizers"></a>Inne Wizualizatorach

Poniżej przedstawiono niektóre inne typy, które również mieć własne wizualizatorów wbudowany:

 ![Inne wizualizacji](media/data-visualizations-image23.png)

*   **Elementy podstawowe**
    *   Wyświetli nieprzetworzone wartości typu pierwotnego.
*   **Wyliczenia**
    *   Zostanie wyświetlona wartość pola bez kwalifikatora typu wyliczenia.
*   **Krotki**
    *   Wyświetlane w formacie ()
*   **Wartość null**
    *   Pokazuje wartość "null".
*   **ADRES URL**
    *   Spowoduje to wyświetlenie aktywne hiperłącze.
*   **IntPtr**
    *   Spowoduje to wyświetlenie szesnastkową reprezentację IntPtr.
