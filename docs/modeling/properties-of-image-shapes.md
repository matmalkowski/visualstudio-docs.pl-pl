---
title: Właściwości kształtów obrazu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 780c9c98bc6be110a0c8bc987a70aeea3344d0e8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31952631"
---
# <a name="properties-of-image-shapes"></a>Właściwości kształtów obrazu
Kształty obraz umożliwia określić wygląd klasy domeny w Projektancie wygenerowany. Zdefiniuj obraz kształtu przez ustawienie `Image` właściwości klasy do pliku obrazu wstępnie zdefiniowane. Obsługiwane są następujące formaty:

-   .gif

-   .jpg

-   JPEG

-   .bmp

-   .wmf

-   .emf

-   .png

 Domyślnie pliki projektanta zasobów, takich jak pliki obrazów, znajdują się w **zasobów**folderu w **Dsl** projektu.

 Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Kształty obrazu mają właściwości, które są wymienione w poniższej tabeli.

|Właściwość|Opis|Domyślny|
|--------------|-----------------|-------------|
|Kolor wypełnienia|Kolor wypełnienia kształtu.|biały|
|Tryb gradientu wypełnienia|Tryb gradientu wypełnienia tego kształtu.|poziomy|
|Ma domyślne punkty połączenia|Jeśli `True`kształt będzie używać lewej górnej i dolnej i punkty połączenia na odpowiednie w Projektancie wygenerowany.|False|
|Kolor konturu|Kolor konturu kształtu.|czarne|
|Styl kreskowania konspektu|Styl kreskowania konturu kształtu (pełne, kreska, kropki, DashDot, DashDotDot lub niestandardowy).|Stałe|
|Szerokość konturu|Grubość konturu kształtu.|0.03125|
|Kolor tekstu|Kolor używany do elementów decorator tekstu, które są skojarzone z tym kształtem.|czarne|
|Modyfikator dostępu|Modyfikator dostępu geometrii kształtu (wewnętrzny lub publiczny).|Public|
|Atrybuty niestandardowe|Można dodawać atrybuty do klasy kodu źródłowego, która jest generowana z tego kształtu.|\<Brak >|
|Generuje o podwójnej precyzji pochodnych|Jeśli `True`, zarówno klasy podstawowej i częściowej klasy (obsługuje dostosowywania przy użyciu zastąpień) zostanie wygenerowany. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzenie klasy generowane](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Ma niestandardowy konstruktora|Jeśli `True`, niestandardowe konstruktora znajdzie się w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzenie klasy generowane](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego, która jest generowany na podstawie kształtu obrazu (`none`, `abstract` lub `sealed`).|brak|
|Obraz podstawowy kształtu|Klasa podstawowa tego kształtu.|(Brak)|
|Nazwa|Nazwa tego kształtu.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw, która jest połączona z tym kształtem.|Bieżącej przestrzeni nazw|
|ToolTip — typ|Miejsce gdzie element tooltip jest zdefiniowane (stałej, zmiennej lub brak). Jeśli następnie stałej wartości `Fixed Tooltip Text` właściwość jest używana jako etykietka narzędzia; Jeśli zmienna, następnie element tooltip jest zdefiniowany w kodu niestandardowego.|brak|
|Uwagi|Nieformalne uwagi, które są skojarzone z tym kształtem.|\<Brak >|
|Wysokość początkowego|Wysokość początkowego tego kształtu w calach.|1|
|Szerokość początkowa|Szerokość początkowa tego kształtu w calach.|1.5|
|Kolor wypełnienia dostępnego jako właściwość<br /><br /> Tryb gradientu wypełnienia dostępnego<br /><br /> Udostępniany jako właściwość kolor konturu<br /><br /> Udostępniany jako właściwość Styl kreskowany konspektu<br /><br /> Widoczne grubość konspektu jako właściwość<br /><br /> Opisuje kolor tekstu|Jeśli `True`, użytkownik może ustawić właściwość podane kształtu. Aby to ustawić, kliknij prawym przyciskiem myszy definicji kształtu, a następnie kliknij przycisk **dodać widoczne**.|False|
|Opis|Używany do dokumentów wygenerowanych projektanta.|\<Brak >|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektanta dla tego kształtu.|\<Brak >|
|Stały tekst etykietki narzędzia|Tekst, który jest używany dla stałych etykietka narzędzia.|\<Brak >|
|Słowo kluczowe pomocy|Słowo kluczowe jest używana do indeksowania pomocy F1 dla tego elementu.|\<Brak >|
|Obraz|Ścieżka do pliku obrazu, który służy do tego kształtu.|\<Brak >|

## <a name="see-also"></a>Zobacz też

- [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)