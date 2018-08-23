---
title: Właściwości kształtów przedziałów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
ms.assetid: 9a9e112d-210d-413b-a44f-0e976a4a78bc
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8ae8a384fd554185c35abe007472decbe2d91242
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42630237"
---
# <a name="properties-of-compartment-shapes"></a>Właściwości kształtów przedziałów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [właściwości kształtów przedziałów](https://docs.microsoft.com/visualstudio/modeling/properties-of-compartment-shapes).  
  
Kształtów przedziałów są jednymi z kształtami, które służy do wyświetlania klasy domeny w języku specyficznym dla domeny. Można rozwijać i zwijać przedziałów.  
  
 Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji o tym, jak korzystać z tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Kształtów przedziałów mają właściwości, które są wymienione w poniższej tabeli.  
  
|Właściwość|Opis|Domyślny|  
|--------------|-----------------|-------------|  
|Domyślne Rozwiń Zwiń|Jeśli `Expanded`, przedziały są pokazywane podczas ich tworzenia. Jeśli `Collapsed`, nie są one.|Rozwinięte|  
|Kolor wypełnienia|Kolor wypełnienia tego kształtu.|Biały|  
|Tryb gradientu wypełnienia|Tryb gradientu wypełnienia tego kształtu.|Poziome|  
|Geometrii|Geometria tego kształtu (prostokąt lub prostokąt zaokrąglony).|Prostokąt|  
|Ma domyślne punkty połączenia|Jeśli `True`kształt użyje górnej, dolnej, lewej i połączenia na odpowiednie punkty w wygenerowanym projektancie.|False|  
|Jeden przedział, nagłówek jest widoczny|Jeśli `False`i kształt ma jeden przedział, nagłówek przedziału nie jest widoczny.|True|  
|Kolor konturu|Kolor konturu tego kształtu.|Czarny|  
|Styl kreskowania konturu|Styl kreskowania konturu tego kształtu (stałe, kreski, kropki, DashDot, DashDotDot, niestandardowe).|Stałe|  
|Grubość konturu|Grubość konturu tego kształtu.|0.03125|  
|Kolor tekstu|Kolor używany dla dekoratorów tekstu, które są skojarzone z tym kształtem.|Czarny|  
|Modyfikator dostępu|Poziom dostępu kształt przedziału (`public` lub `internal`).|Public|  
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu źródłowego, która jest generowany na podstawie tego kształtu przedziału|\<Brak >|  
|Generuje Double pochodne|Jeśli `True`, zostaną wygenerowane klasy podstawowej i klasy częściowej (obsługuje dostosowywania przy użyciu zastąpień). Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Ma konstruktora niestandardowego|Jeśli `True`, konstruktora niestandardowego, które będą dostępne w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modyfikator dziedziczenia|Opisuje typ dziedziczenia klasy kodu źródłowego, która jest generowany na podstawie kształt przedziału (`none`, `abstract` lub `sealed`).|Brak|  
|Podstawowy kształt przedziału|Klasa bazowa tego kształtu.|(Brak)|  
|Nazwa|Nazwa tego kształtu.|Bieżąca nazwa|  
|Przestrzeń nazw|Przestrzeń nazw, która jest połączona z tym kształtem.|Bieżąca przestrzeń nazw|  
|Typ etykietki narzędzia|Jak etykietka narzędzia jest zdefiniowane (stałe, zmienna lub brak). Jeśli następnie stałej wartości `Fixed Tooltip Text` właściwość jest używana jako etykietka narzędzia; Jeśli jest to zmienna, następnie etykietki narzędzia jest definiowana w kodzie niestandardowym.|brak|  
|Uwagi|Uwagi informacyjne, które są skojarzone z tym kształtem.|\<Brak >|  
|Początkowa wysokość|Początkowa wysokość tego kształtu, w calach. Dla kształtów przedziałów jest wysokość w sekcji nagłówka i nie można zmienić rozmiaru.|1|  
|Początkowa szerokość|Początkowa szerokość tego kształtu, w calach.|1.5|  
|Kolor wypełnienia uwidocznione jako właściwość<br /><br /> Tryb gradientu wypełnienia narażone<br /><br /> Widoczne kolor konturu jako właściwość<br /><br /> Widoczne stylu kreskowania konturu jako właściwość<br /><br /> Grubość konturu jako właściwość widoczne<br /><br /> Opisuje kolor tekstu|Jeśli `True`, użytkownik może ustawić właściwość podane kształtu. Aby to ustawić, kliknij prawym przyciskiem myszy definicję kształtu, a następnie kliknij przycisk **Dodaj udostępniane**.|False|  
|Opis|Umożliwia dokumentowanie wygenerowanego projektanta.|\<Brak >|  
|Nazwa wyświetlana|Nazwa która będzie wyświetlana w wygenerowanym projektancie dla tego kształtu.|\<Brak >|  
|Stały tekst etykietki narzędzia|Tekst, który jest używany dla ustalonej etykietki narzędzia.|\<Brak >|  
|Słowo kluczowe pomocy|Słowo kluczowe, które jest używane do indeksowania pomocy F1 dla tego kształtu.|\<Brak >|  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzi języka specyficznego dla domeny](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



