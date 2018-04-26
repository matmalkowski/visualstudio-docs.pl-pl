---
title: Właściwości elementów Decorator
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0521936dd155c162d045b451f4570ef9a1958c8b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="properties-of-decorators"></a>Właściwości elementów Decorator
Elementy decorator są ikony, tekst lub Rozwiń/Zwiń znaki, które mogą być wyświetlane na kształtów lub łączników na diagramie. W poniższej tabeli przedstawiono trzy rodzaje dekoratora właściwości. Niektóre właściwości są wyświetlane tylko na elementy kształtu decorator lub tylko dla elementów decorator łącznika.

 Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Rozwiń/Zwiń Dekoratora

|Właściwość|Opis|Domyślny|
|--------------|-----------------|-------------|
|Nazwa wyświetlana|Nazwa dekoratora, który będzie wyświetlany w Projektancie wygenerowany.|Rozwiń węzeł Dekoratora Zwiń|
|Nazwa|Nazwa dekorator.|ExpandCollapseDecorator|
|Uwagi|Nieformalne uwagi, które są skojarzone z tym dekoratora.|\<Brak >|
|HorizontalOffset|Przesunięcie w poziomie, względem to domyślne położenie dekoratora, w calach. (Kształtów tylko.)|0|
|VerticalOffset|Przesunięcie w pionie, względem to domyślne położenie dekoratora, w calach. (Kształtów tylko.)|0|
|OffsetFromLine|Przesunięcie dekoratora z poziomu wiersza względem położenia domyślnego w calach. (Dla łączników tylko.)|0|
|OffsetFromShape|Przesunięcie dekoratora z kształtu, względem położenia domyślnego w calach. (Dla łączników tylko.)|0|
|Pozycja|To domyślne położenie dekorator.|SourceTop|

## <a name="icon-decorator"></a>Ikona Dekoratora

|Właściwość|Opis|Domyślny|
|--------------|-----------------|-------------|
|DefaultIcon|Ścieżka pliku ikony lub obrazu do wyświetlenia.|\<Brak >|
|Nazwa wyświetlana|Nazwa dekoratora, który ma być wyświetlany w Projektancie wygenerowany.|Ikona Dekoratora|
|Nazwa|Nazwa dekorator.|IconDecorator|
|Uwagi|Nieformalne uwagi, które są skojarzone z dekorator.|\<Brak >|
|HorizontalOffset|Przesunięcie w poziomie, względem to domyślne położenie dekoratora, w calach. (Kształtów tylko.)|0|
|VerticalOffset|Przesunięcie w pionie, względem to domyślne położenie dekoratora, w calach. (Kształtów tylko.)|0|
|OffsetFromLine|Przesunięcie dekoratora z poziomu wiersza względem położenia domyślnego w calach. (Dla łączników tylko.)|0|
|OffsetFromShape|Przesunięcie dekoratora z kształtu, względem położenia domyślnego w calach. (Dla łączników tylko.)|0|
|Pozycja|To domyślne położenie dekorator.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Właściwość|Opis|Domyślny|
|--------------|-----------------|-------------|
|DefaultText|Domyślny tekst do wyświetlenia.|Etykieta|
|Nazwa wyświetlana|Nazwa dekoratora, który ma być wyświetlany w Projektancie wygenerowany.|Etykieta|
|FontSize|Rozmiar czcionki tekstu, który jest wyświetlany w dekorator.|8|
|FontStyle|Styl czcionki tekstu, który jest wyświetlany w dekorator.|Regularne|
|Nazwa|Nazwa dekorator.|Etykieta|
|Uwagi|Nieformalne uwagi, które są skojarzone z dekorator.|\<Brak >|
|HorizontalOffset|Przesunięcie w poziomie, względem to domyślne położenie dekoratora, w calach. (Kształtów tylko.)|0|
|VerticalOffset|Przesunięcie w pionie, względem to domyślne położenie dekoratora, w calach. (Kształtów tylko.)|0|
|OffsetFromLine|Przesunięcie dekoratora z poziomu wiersza względem położenia domyślnego w calach. (Dla łączników tylko.)|0|
|OffsetFromShape|Przesunięcie dekoratora z kształtu, względem położenia domyślnego w calach. (Dla łączników tylko.)|0|
|Pozycja|To domyślne położenie dekorator.|TargetBottom|

## <a name="see-also"></a>Zobacz też

- [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)