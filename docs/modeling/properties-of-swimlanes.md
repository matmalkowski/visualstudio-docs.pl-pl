---
title: Właściwości ścieżek | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 9a9a07549773d9881b3512bdb1b84c0cb6654280
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="properties-of-swimlanes"></a>Właściwości torów
Można dodać ścieżek do diagramu. Ścieżek podział diagramu obszarów pionowych lub poziomych. Można określić innych kształtów, który będzie wyświetlany w ścieżek. Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Ścieżek mają właściwości, które są wymienione w poniższej tabeli.  
  
|Właściwość|Opis|Domyślny|  
|--------------|-----------------|-------------|  
|Kolor wypełnienia treści|Kolor wypełnienia treści tor.|biały|  
|Kolor wypełnienia nagłówka|Kolor wypełnienia nagłówka tor.|DarkGray|  
|Kolor separatora|Kolor linii separatora.|LightGray|  
|Styl linii separatora|Styl linii separatora (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`, lub `Custom`).|`Dash`|  
|Szerokość separatora|Grubość linii separatora w calach.|0.03125|  
|Kolor tekstu|Kolor używany do elementów decorator tekstu, które są skojarzone z tym tor.|czarne|  
|Modyfikator dostępu|Poziom dostępu klasy (`public` lub `internal`).|Public|  
|Atrybuty niestandardowe|Można dodawać atrybuty do klasy kodu, które są generowane na podstawie tego tor.|\<Brak >|  
|Generuje o podwójnej precyzji pochodnych|Jeśli `True`, zarówno klasy podstawowej i częściowej klasy (obsługuje dostosowywania przy użyciu zastąpień) zostanie wygenerowany. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzenie klasy generowane](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Ma niestandardowy konstruktora|Jeśli `True`, niestandardowe konstruktora znajdzie się w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzenie klasy generowane](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego, która jest generowana z tor (`none`, `abstract` lub `sealed`).|brak|  
|Tor podstawowej|Klasa podstawowa to tor.|(Brak)|  
|Nazwa|Nazwa tego tor.|Bieżąca nazwa|  
|Przestrzeń nazw|Przestrzeń nazw, która jest połączona z tym tor.|Bieżącej przestrzeni nazw|  
|ToolTip — typ|Jak jest zdefiniowany element tooltip (`fixed`, `variable`, lub `none`). Jeśli `fixed`, wartość `Fixed Tooltip Text` właściwość jest używana; jeśli `variable`, a następnie element tooltip jest zdefiniowany w niestandardowym.|\<Brak >|  
|Uwagi|Nieformalne uwagi, które są skojarzone z tym tor.|\<Brak >|  
|Wyrównanie|Wyrównanie w poziomie lub pionie.|Pionowe|  
|Wysokość początkowego|Początkowa wysokość tego tor w calach. Dotyczy tylko pozioma ścieżek.|0|  
|Szerokość początkowa|Szerokość początkowego tego tor w calach. Dotyczy tylko pionowy ścieżek.|0|  
|Opisuje kolor tekstu|Jeśli `True`, użytkownik może ustawić kolor tor w Projektancie wygenerowany. Aby to ustawić, kliknij prawym przyciskiem myszy kształtu tor, a następnie kliknij przycisk **dodać widoczne**.|False|  
|Opis|Używany do dokumentów wygenerowanych projektanta.|\<Brak >|  
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektanta, aby odwoływać się do tej klasy tor.|\<Brak >|  
|Stały tekst etykietki narzędzia|Tekst, który jest używany dla stałych etykietka narzędzia.|\<Brak >|  
|Słowo kluczowe pomocy|Słowo kluczowe jest używana do indeksowania pomocy F1 dla tego tor.|\<Brak >|  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzia języka specyficznego dla domeny](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)