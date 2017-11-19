---
title: "Za pomocą wyrażeń regularnych w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.wildcardsbuilder
- vs.netregularexpressionhelp
- vs.wildcards
helpviewer_keywords:
- regular expressions [Visual Studio]
- regular expressions
- Visual Studio, regular expressions
ms.assetid: 718a617d-0e05-47e1-a218-9746971527f4
caps.latest.revision: "53"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c01023649879c34838cbca3172aec6b5a053f4bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="using-regular-expressions-in-visual-studio"></a>Używanie wyrażeń regularnych w Visual Studio
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]używa wyrażeniach regularnych programu .NET Framework w celu znajdowania i zamieniania tekstu. Aby uzyskać więcej informacji na temat wyrażeń regularnych programu .NET, zobacz [wyrażeń regularnych programu .NET Framework](/dotnet/standard/base-types/regular-expressions).  
  
 Przed zastosowaniem programu Visual Studio 2012 Visual Studio użycie składni wyrażeń regularnych niestandardowych w systemie windows Znajdź i Zamień. Zobacz [programu Visual Studio regularne konwersji wyrażenia](https://msdn.microsoft.com/en-us/library/2k3te2cs\(v=vs.110\).aspx) opis przekonwertować niektóre symbole niestandardowe wyrażenie regularne więcej często używane do wersji platformy .NET.  
  
> [!TIP]
>  W systemach operacyjnych Windows większość wierszy kończyć się "\r\n" (znak powrotu karetki znak nowego wiersza). Te znaki nie są widoczne, ale znajdują się w edytorze i są przekazywane do usługi .NET wyrażenia regularnego.  
  
> [!TIP]
>  Informacji o wyrażeń regularnych, które są używane w wzorce zamiany znajduje się w temacie [podstawienia](/dotnet/standard/base-types/substitutions-in-regular-expressions). Aby użyć grupy numerowanych przechwytywania, składnia jest `$1` do określenia grupy numerowanych i `(x)` do określenia danej grupy. Na przykład grupowanych wyrażenia regularnego `(\d)([a-z])` znajduje cztery dopasowań w następujący ciąg: **2b 1a 3c 4d**. Ciąg zastępczy `z$1` konwertuje tego ciągu do **z1 z2 z3 z4**.  
  
## <a name="regular-expressions-in-visual-studio"></a>Wyrażeń regularnych w programie Visual Studio  
 Oto kilka przykładów  
  
|Cel|Wyrażenie|Przykład|  
|-------------|----------------|-------------|  
|Dopasowuje dowolny pojedynczy znak (z wyjątkiem podziału wiersza)|.|`a.o`Dopasowuje "aro" w "wokół" i "abo" w "temat", ale nie "akro" w "w".|  
|Zgodne zero lub więcej wystąpień poprzedniego wyrażenia (odpowiadać maksymalną liczbę znaków, jak to możliwe)|*|`a*r`Dopasowuje "r" w "rack", "ar" w "arek" i "aar" w "aardvark"|  
|Dopasowuje dowolny znak zero lub więcej razy (symbol wieloznaczny *)|.*|Dopasowuje c.*e "cke" w "hałasu", "comme" w "comment", a 'code' w 'code'|  
|Odpowiada jedno lub więcej wystąpień poprzedniego wyrażenia (odpowiadać maksymalną liczbę znaków, jak to możliwe)|+|`e.+e`Dopasowuje "eede" w "podajnik", ale nie "ee".|  
|Dopasowuje dowolny znak jeden lub więcej razy (symbol wieloznaczny?)|.+|e. + e odpowiada "eede" w "podajnik", ale nie "ee".|  
|Zgodne zero lub więcej wystąpień poprzedniego wyrażenia (odpowiadać liczbę znaków, jak to możliwe)|*?|`e.*?e`Dopasowuje "ee" w "podajnik", ale nie "eede".|  
|Odpowiada jedno lub więcej wystąpień poprzedniego wyrażenia (odpowiadać liczbę znaków, jak to możliwe)|+?|`e.+?e`Dopasowuje "Wprowadź" i "erprise" w "przedsiębiorstwa", ale nie całe wyrazy "przedsiębiorstwa".|  
|Zakotwicz dopasowanie ciągu do początku wiersza lub ciąg|^|`^car`wyraz "samochód" jest zgodna tylko wtedy, gdy znajduje się na początku wiersza.|  
|Zakotwicz dopasowanie ciągu do końca wiersza|\r?$|`End\r?$`Dopasowuje "Zakończ" tylko gdy znajduje się na końcu wiersza.|  
|Dopasowuje dowolny pojedynczy znak ze zbioru|[abc]|`b[abc]`Dopasowuje "ba", "bb" i "bc".|  
|Dopasowuje dowolny znak z zakresu znaków|[a-f]|`be[n-t]`Dopasowuje "trafień" w "między", "ben" w "poniżej" i "bes" w "obok", ale nie "poniżej".|  
|Przechwytuje i niejawnie numeruje wyrażenie zawarte w nawiasach|()|`([a-z])X\1`Dopasowuje "aXa" i "bXb", ale nie "aXb". ". "\1" odwołuje się do pierwszej grupy wyrażenie "[a-z]".|  
|Unieważnienie dopasowania|(?! ABC)|`real (?!ity)`Dopasowuje "rzeczywiste" w "realność" i "naprawdę", ale nie w "rzeczywistości." Drugi "rzeczywistym" (ale nie pierwszy "rzeczywistego") również znalezione w "realityreal".|  
|Dopasowuje dowolny znak, który nie jest w danym zestawie znaków|[^ abc]|`be[^n-t]`Dopasowuje "bef" w "before", "beh" w "za" i "etykietę" w "poniżej", ale nie "poniżej".|  
|Zgodne wyrażenie przed lub jeden po symbolu.|&#124;|`(sponge&#124;mud) bath`Dopasowuje "Gąbka łaźni" i "błocie Łaźnia."|  
|Ucieczki znaku po ukośniku odwrotnym|\|`\^`Dopasowuje znak ^.|  
|Określ liczbę wystąpień poprzedniego znaku lub grupy|{x}, gdzie x to liczba wystąpień|`x(ab){2}x`Dopasowuje "xababx" i `x(ab){2,3}x` pasuje do "xababx" i "xabababx", ale nie "xababababx".|  
|Dopasowanie tekstu w klasie znaków Unicode, gdzie "X" jest numerem Unicode. Aby uzyskać więcej informacji na temat klas znaków Unicode zobacz<br /><br /> [Właściwości znaku w standardzie Unicode 5.2](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}|`\p{Lu}`Dopasowuje "T" i "D" w "Blogu Thomasa Nowak".|  
|Zgodne granic programu word|`\b`(Poza klasą znak \b Określa granicy słowa i wewnątrz znak klasa określa polecenie backspace).|`\bin`pasuje do "w" w "wewnątrz" ale nie "pinto".|  
|Zgodne podział wiersza (ie powrotu karetki znak nowego wiersza).|\r?\n|`End\r?\nBegin`Dopasowuje "End" i "Begin" tylko wtedy, gdy "End" jest ciągiem ostatniego wiersza i "Begin" jest pierwszy ciąg w następnym wierszu.|  
|Dopasowuje dowolny znak alfanumeryczny|\w|`a\wd`dopasowania "Dodaj" i "a1d", ale nie "d".|  
|Dopasowuje dowolny biały znak.|(? ([^ \r\n])\s)|`Public\sInterface`pasuje do frazy "Interfejs publiczny".|  
|Pasuje do dowolnego znaku numerycznego|\d|`\d`zgodne i "3" w "3456", "2" w 23" i"1"w"1".|  
|Dopasowuje znak Unicode|\uXXXX gdzie XXXX określa wartość znaku Unicode.|`\u0065`Dopasowuje znak "e".|  
|Zgodny z identyfikatorem|\b (_\w + &#124; [ \w-[0-9\_]] \w*)\b|Dopasowania "type1", ale nie & type1 "lub" #define ".|  
|Dopasowanie ciągu wewnątrz cudzysłowów|((\\".+?\\")&#124;('.+?'))|Dopasowuje dowolny ciąg w pojedynczym lub podwójnym cudzysłowie.|  
|Dopasowanie do liczby szesnastkowej|\b0[xX]([0-9a-fA-F]\)\b|Dopasowuje "0xc67f", ale nie "0xc67fc67f".|  
|Dopasowanie do liczb całkowitych i dziesiętnych|\b[0-9]*\\.\* [0-9] + \b|Dopasowuje "1,333".|  
  
## <a name="see-also"></a>Zobacz też  
 [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)