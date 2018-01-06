---
title: "Właściwości łączniki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, connectors
ms.assetid: b1f24e8d-cdd7-4a5d-af37-1038f43b45c7
caps.latest.revision: "21"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: e974c768f9bf73b92cb974875654846a267bb893
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="properties-of-connectors"></a>Właściwości łączników
Łączniki reprezentują relacje domeny w wygenerowanym projektanta.  
  
 Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Łączniki mają właściwości, które są wymienione w poniższej tabeli.  
  
|Właściwość|Opis|Domyślny|  
|--------------|-----------------|-------------|  
|Kolor|Kolor tego łącznika.|czarne|  
|Styl kreskowania|Styl kreskowania dla wiersza dla tego łącznika (pełne, kreska, kropki, DashDot, DashDotDot lub niestandardowy).|Stałe|  
|Styl zakończenia źródła|Styl zakończenia źródła dla tego łącznika (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond lub brak).|Brak|  
|Styl końca docelowej|Styl zakończenia docelowego dla tego łącznika (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond lub brak).|Brak|  
|Kolor tekstu|Kolor używany do elementów decorator tekstu, które są skojarzone z tym łącznikiem.|czarne|  
|Grubość|Grubość linii dla tego łącznika, mierzony w milimetrach.|0.03125|  
|Modyfikator dostępu|Poziom dostępu klasy (`public` lub `internal`).|Public|  
|Atrybuty niestandardowe|Można dodawać atrybuty do klasy kodu źródłowego, która jest generowana z tego łącznika.|\<Brak >|  
|Generuje o podwójnej precyzji pochodnych|Jeśli `True`, zarówno klasy podstawowej i częściowej klasy (obsługuje dostosowywania przy użyciu zastąpień) zostanie wygenerowany. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzenie klasy generowane](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Ma niestandardowy konstruktora|Jeśli `True`, niestandardowe konstruktora znajdzie się w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzenie klasy generowane](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego, która jest generowana z łącznika (`none`, `abstract` lub `sealed`).|brak|  
|Podstawowy łącznika|Klasa podstawowa tego łącznika.|(Brak)|  
|Nazwa|Nazwa tego łącznika.|Bieżąca nazwa|  
|Przestrzeń nazw|Przestrzeń nazw, która jest połączona z tym łącznikiem.|Bieżącej przestrzeni nazw|  
|ToolTip — typ|W jaki sposób element tooltip jest zdefiniowany (stałej, zmiennej lub brak). Jeśli następnie stałej wartości `Fixed Tooltip Text` właściwość jest używana jako etykietka narzędzia; Jeśli zmienna, następnie element tooltip jest zdefiniowany w kodu niestandardowego.|\<Brak >|  
|Uwagi|Nieformalne uwagi, które są skojarzone z tym łącznikiem.|\<Brak >|  
|Styl trasowania|Styl, który służy do routingu łącznika. A `Rectilinear` kątem prostym włącza zgodnie z wymaganiami; sprawia, że łącznik `Straight` łącznika nie ma.|Prostoliniowego|  
|Kolor narażonych jako właściwość<br /><br /> Styl kreskowania narażonych jako właściwość<br /><br /> Grubość narażonych jako właściwość<br /><br /> Opisuje kolor tekstu|Jeśli `True`, użytkownik może ustawić właściwość podane kształtu. Aby to ustawić, kliknij prawym przyciskiem myszy definicji kształtu, a następnie kliknij przycisk **dodać widoczne**.|False|  
|Opis|Używany do dokumentów wygenerowanych projektanta.|\<Brak >|  
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektanta dla tego łącznika.|\<Brak >|  
|Stały tekst etykietki narzędzia|Tekst, który jest używany dla stałych etykietka narzędzia.|\<Brak >|  
|Słowo kluczowe pomocy|Słowo kluczowe jest używana do indeksowania pomocy F1 dla tego elementu.|\<Brak >|  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)