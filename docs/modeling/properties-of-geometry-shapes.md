---
title: Właściwości kształtów geometrii | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: f8b82f74afc133f99a4b9d2851c28ade1743ee3c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="properties-of-geometry-shapes"></a>Właściwości kształtów geometrycznych
Geometrii kształtów służy do określania sposobu wyświetlania wystąpienia klas domeny języka specyficznego dla domeny. Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Kształty geometrii mają właściwości, które są wymienione w poniższej tabeli.  
  
|Właściwość|Opis|Domyślny|  
|--------------|-----------------|-------------|  
|Kolor wypełnienia|Kolor wypełnienia kształtu.|biały|  
|Tryb gradientu wypełnienia|Tryb gradientu wypełnienia tego kształtu (poziomy, pionowy, do przodu ukośnych, z poprzednimi wersjami ukośnych lub brak).|poziomy|  
|Geometria|Geometria tego kształtu (prostokąta, zaokrąglony prostokąt, elipsy lub okręgu).|Prostokąt|  
|Ma domyślne punkty połączenia|Jeśli `True`kształt będzie używać lewej górnej i dolnej i punkty połączenia na odpowiednie w Projektancie wygenerowany.|False|  
|Kolor konturu|Kolor konturu kształtu.|czarne|  
|Styl kreskowania konspektu|Styl kreskowania konturu kształtu (pełne, kreska, kropki, DashDot, DashDotDot lub niestandardowy).|Stałe|  
|Szerokość konturu|Grubość konturu kształtu.|0.03125|  
|Kolor tekstu|Kolor używany do elementów decorator tekstu, które są skojarzone z tym kształtem.|czarne|  
|Modyfikator dostępu|Modyfikator dostępu klasy (wewnętrzny lub publiczny).|Public|  
|Atrybuty niestandardowe|Można dodawać atrybuty do klasy kodu źródłowego, generowany dla tego kształtu.|\<Brak >|  
|Generuje o podwójnej precyzji pochodnych|Jeśli `True`, zarówno klasy podstawowej i częściowej klasy (obsługuje dostosowywania przy użyciu zastąpień) zostanie wygenerowany. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzenie klasy generowane](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Ma niestandardowy konstruktora|Jeśli `True`, niestandardowe konstruktora znajdzie się w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzenie klasy generowane](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego, która jest generowana z kształtu (`none`, `abstract` lub `sealed`).|brak|  
|Podstawowy geometrii kształtu|Klasa podstawowa tego kształtu.|(Brak)|  
|Nazwa|Nazwa tego kształtu.|Bieżąca nazwa|  
|Przestrzeń nazw|Przestrzeń nazw, która jest połączona z tym kształtem.|Bieżącej przestrzeni nazw|  
|ToolTip — typ|W jaki sposób element tooltip jest zdefiniowany (stałej, zmiennej lub brak). Jeśli następnie stałej wartości `Fixed Tooltip Text` właściwość jest używana jako etykietka narzędzia; Jeśli zmienna, następnie element tooltip jest zdefiniowany w kodu niestandardowego.|Brak|  
|Uwagi|Nieformalne uwagi, które są skojarzone z tym elementem.|\<Brak >|  
|Wysokość początkowego|Początkowa wysokość tego kształtu w calach.|1|  
|Szerokość początkowa|Szerokość początkowa tego kształtu w calach.|1.5|  
|Kolor wypełnienia dostępnego jako właściwość<br /><br /> Tryb gradientu wypełnienia dostępnego<br /><br /> Udostępniany jako właściwość kolor konturu<br /><br /> Udostępniany jako właściwość Styl kreskowany konspektu<br /><br /> Widoczne grubość konspektu jako właściwość<br /><br /> Opisuje kolor tekstu|Jeśli `True`, użytkownik może ustawić właściwość podane kształtu. Aby to ustawić, kliknij prawym przyciskiem myszy definicji kształtu, a następnie kliknij przycisk **dodać widoczne**.|False|  
|Opis|Opis, który służy do dokumentów wygenerowanych projektanta.|\<Brak >|  
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektanta dla tego kształtu.|\<Brak >|  
|Stały tekst etykietki narzędzia|Tekst, który jest używany dla stałych etykietka narzędzia.|\<Brak >|  
|Słowo kluczowe pomocy|Słowo kluczowe jest używana do indeksowania pomocy F1 dla tego kształtu.|\<Brak >|  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)