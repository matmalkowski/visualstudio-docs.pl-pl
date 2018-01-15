---
title: "Właściwości przedziału kształtów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords: Domain-Specific Language, compartment shape
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ecec7f30df607400eaf333a21ae2746a30f1a41d
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="properties-of-compartment-shapes"></a>Właściwości kształtów przedziałów
Kształty przedział są jednym kształtów, który służy do wyświetlania klasą domeny w języku specyficznego dla domeny. Można zwijać i rozwijać przedziałów.  
  
 Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Kształty przedział mają właściwości, które są wymienione w poniższej tabeli.  
  
|Właściwość|Opis|Domyślny|  
|--------------|-----------------|-------------|  
|Zwiń Rozwiń węzeł domyślne|Jeśli `Expanded`, przedziałów są wyświetlane po utworzeniu. Jeśli `Collapsed`, nie są one.|Rozwinięty|  
|Kolor wypełnienia|Kolor wypełnienia kształtu.|biały|  
|Tryb gradientu wypełnienia|Tryb gradientu wypełnienia tego kształtu.|poziomy|  
|Geometria|Geometria tego kształtu (prostokąta lub zaokrąglony prostokąt).|Prostokąt|  
|Ma domyślne punkty połączenia|Jeśli `True`kształt będzie używać lewej górnej i dolnej i punkty połączenia na odpowiednie w Projektancie wygenerowany.|False|  
|Nagłówek pojedynczych komór jest widoczny|Jeśli `False`i kształtu ma pojedynczych komór, nagłówek przedziału nie jest widoczny.|Wartość true|  
|Kolor konturu|Kolor konturu kształtu.|czarne|  
|Styl kreskowania konspektu|Styl kreskowania konturu kształtu (pełne, kreska, kropki, DashDot, DashDotDot, niestandardowe).|Stałe|  
|Szerokość konturu|Grubość konturu kształtu.|0.03125|  
|Kolor tekstu|Kolor tekstu elementów decorator, które są skojarzone z tym kształtem.|czarne|  
|Modyfikator dostępu|Poziom dostępu kształtu przedział (`public` lub `internal`).|Public|  
|Atrybuty niestandardowe|Można dodawać atrybuty do klasy kod źródłowej, które są generowane na podstawie tego kształtu Przedział|\<Brak >|  
|Generuje o podwójnej precyzji pochodnych|Jeśli `True`, zarówno klasy podstawowej i częściowej klasy (obsługuje dostosowywania przy użyciu zastąpień) zostanie wygenerowany. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzenie klasy generowane](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Ma niestandardowy konstruktora|Jeśli `True`, niestandardowe konstruktora znajdzie się w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzenie klasy generowane](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego, która jest generowany na podstawie kształtu przedział (`none`, `abstract` lub `sealed`).|Brak|  
|Kształt Przedział podstawowej|Klasa podstawowa tego kształtu.|(Brak)|  
|Nazwa|Nazwa tego kształtu.|Bieżąca nazwa|  
|Przestrzeń nazw|Przestrzeń nazw, która jest połączona z tym kształtem.|Bieżącej przestrzeni nazw|  
|ToolTip — typ|W jaki sposób element tooltip jest zdefiniowany (stałej, zmiennej lub brak). Jeśli następnie stałej wartości `Fixed Tooltip Text` właściwość jest używana jako etykietka narzędzia; Jeśli zmienna, następnie element tooltip jest zdefiniowany w kodu niestandardowego.|brak|  
|Uwagi|Nieformalne uwagi, które są skojarzone z tym kształtem.|\<Brak >|  
|Wysokość początkowego|Wysokość początkowego tego kształtu w calach. Kształtów przedział jest wysokość w sekcji nagłówka i nie można zmienić rozmiaru.|1|  
|Szerokość początkowa|Szerokość początkowa tego kształtu w calach.|1.5|  
|Kolor wypełnienia dostępnego jako właściwość<br /><br /> Tryb gradientu wypełnienia dostępnego<br /><br /> Udostępniany jako właściwość kolor konturu<br /><br /> Udostępniany jako właściwość Styl kreskowany konspektu<br /><br /> Widoczne grubość konspektu jako właściwość<br /><br /> Opisuje kolor tekstu|Jeśli `True`, użytkownik może ustawić właściwość podane kształtu. Aby to ustawić, kliknij prawym przyciskiem myszy definicji kształtu, a następnie kliknij przycisk **dodać widoczne**.|False|  
|Opis|Używany do dokumentów wygenerowanych projektanta.|\<Brak >|  
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektanta dla tego kształtu.|\<Brak >|  
|Stały tekst etykietki narzędzia|Tekst, który jest używany dla stałych etykietka narzędzia.|\<Brak >|  
|Słowo kluczowe pomocy|Słowo kluczowe jest używana do indeksowania pomocy F1 dla tego kształtu.|\<Brak >|  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)