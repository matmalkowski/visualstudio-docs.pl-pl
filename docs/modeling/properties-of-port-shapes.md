---
title: "Właściwości kształtów portu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.port
helpviewer_keywords: Domain-Specific Language, port shape
ms.assetid: 9d69c4c1-4f72-4876-96b6-9b846e0495a4
caps.latest.revision: "21"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 3cc8f57b0615be6255425e396f0fc4ea3e763810
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="properties-of-port-shapes"></a>Właściwości kształtów portu
Kształty port służy do reprezentowania klasy domeny w Projektancie wygenerowany.  
  
 Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Port kształty mają właściwości, które są wymienione w poniższej tabeli.  
  
|Właściwość|Opis|Domyślny|  
|--------------|-----------------|-------------|  
|Kolor wypełnienia|Kolor wypełnienia kształtu.|biały|  
|Tryb gradientu wypełnienia|Tryb gradientu wypełnienia tego kształtu.|poziomy|  
|Geometria|Geometria tego kształtu (prostokąta, zaokrąglony prostokąt, elipsy lub okręgu).|Prostokąt|  
|Ma domyślne punkty połączenia|Jeśli `True`kształt będzie używać lewej górnej i dolnej i punkty połączenia na odpowiednie w Projektancie wygenerowany.|False|  
|Kolor konturu|Kolor konturu kształtu.|czarne|  
|Styl kreskowania konspektu|Styl kreskowania konturu kształtu (pełne, kreska, kropki, DashDot, DashDotDot lub niestandardowy).|Stałe|  
|Szerokość konturu|Grubość konturu kształtu.|0.03125|  
|Kolor tekstu|Kolor używany do elementów decorator tekstu, które są skojarzone z tym kształtem.|czarne|  
|Modyfikator dostępu|Poziom dostępu klasy (`public` lub `internal`).|Public|  
|Atrybuty niestandardowe|Można dodawać atrybuty do klasy kodu źródłowego, która jest generowana z tego kształtu.|\<Brak >|  
|Generuje o podwójnej precyzji pochodnych|Jeśli `True`, zarówno klasy podstawowej i częściowej klasy (obsługuje dostosowywania przy użyciu zastąpień) zostanie wygenerowany. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md)|False|  
|Ma niestandardowy konstruktora|Jeśli `True`, niestandardowe konstruktora znajdzie się w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzenie klasy generowane](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródła, która jest generowana z portu (`none`, `abstract` lub `sealed`).|brak|  
|Podstawowy Port|Klasa podstawowa tego kształtu.|(Brak)|  
|Nazwa|Nazwa tego kształtu.|Bieżąca nazwa|  
|Przestrzeń nazw|Przestrzeń nazw, która jest połączona z tym kształtem.|Bieżącej przestrzeni nazw|  
|Typ Porada narzędzia|W jaki sposób element tooltip jest zdefiniowany (stałej, zmiennej lub brak). Jeśli następnie stałej wartości `Fixed Tooltip Text` właściwość jest używana jako etykietka narzędzia; Jeśli zmienna, następnie element tooltip jest zdefiniowany w kodu niestandardowego.|brak|  
|Uwagi|Nieformalne uwagi, które są skojarzone z tym kształtem.|\<Brak >|  
|Wysokość początkowego|Wysokość początkowego tego kształtu w calach.|1|  
|Szerokość początkowa|Szerokość początkowa tego kształtu w calach.|1.5|  
|Kolor wypełnienia dostępnego jako właściwość<br /><br /> Tryb gradientu wypełnienia dostępnego<br /><br /> Udostępniany jako właściwość kolor konturu<br /><br /> Udostępniany jako właściwość Styl kreskowany konspektu<br /><br /> Widoczne grubość konspektu jako właściwość<br /><br /> Opisuje kolor tekstu|Jeśli `True`, użytkownik może ustawić właściwość podane kształtu. Aby to ustawić, kliknij prawym przyciskiem myszy definicji kształtu, a następnie kliknij przycisk **dodać widoczne**.|False|  
|Opis|Używany do dokumentów wygenerowanych projektanta.|\<Brak >|  
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektanta dla tego kształtu.|\<Brak >|  
|Stały tekst wskazówki|Tekst, który jest używany dla stałych etykietka narzędzia.|\<Brak >|  
|Słowo kluczowe pomocy|Słowo kluczowe jest używana do indeksowania pomocy F1 dla tego kształtu.|\<Brak >|  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)