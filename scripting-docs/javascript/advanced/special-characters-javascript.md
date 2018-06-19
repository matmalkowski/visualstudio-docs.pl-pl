---
title: Znaki specjalne (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- line terminator character
- white space character
- Unicode character
- escape sequence
- backslash (\)
ms.assetid: 3b38b1bd-1f0f-4748-b13e-55cab36fd126
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0eaae8dfc84d9a3be6db54c50558d4cf675a53a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24789280"
---
# <a name="special-characters-javascript"></a>Znaki specjalne (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]udostępnia sekwencji unikowych, które można uwzględnić w ciągach znaków, których nie można wpisać bezpośrednio utworzyć.  
  
## <a name="remarks"></a>Uwagi  
 Wartość ciągu jest szereg zero lub więcej znaków Unicode (litery, cyfry i znaki). Literały ciągu są ujęte w par pojedynczego lub podwójny cudzysłów. Podwójny cudzysłów mogą być zawarte w ciąg ujęty w apostrofy. Pojedynczy cudzysłów mogą być zawarte w ciągu, który jest ujęta w znaki podwójnego cudzysłowu.  
  
 Każdy znaków w literale ciągu może być reprezentowany przez sekwencję ucieczki. Sekwencja specjalna rozpoczyna się od ukośnika odwrotnego (\\) który informuje o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] interpreter, że następny znak jest znak specjalny.  
  
 Można określić znak Unicode za pomocą \u*gg* escape sekwencji, gdzie *gg* jest to liczba szesnastkowa czterech cyfr. Sekwencja ucieczki kodu Unicode może reprezentować dowolny znak 16-bitowych. Aby uzyskać dodatkowe informacje, zobacz [sekwencji ucieczki punkt kodu Unicode](#CodePoint).  
  
 Można użyć sekwencji ucieczki jednoznakowym niektórych znaków. Na przykład \t Określa znak tabulacji.  
  
## <a name="escape-sequences"></a>Sekwencje unikowe  
 W poniższej tabeli wymieniono kilka przykładów sekwencje specjalne znaków wspólnej.  
  
|Znak Unicode o wartości|Sekwencja specjalna|Znaczenie|Kategoria|  
|-----------------------------|---------------------|-------------|--------------|  
|\u0008|\b|Backspace||  
|\u0009|\t|Tab|Biały znak|  
|\u000A|\n|Wysuw nowego wiersza)|Terminator wiersza|  
|\u000B|\v<br /><br /> (Zobacz uwagi pod tą tabelą).|Tabulator pionowy|Biały znak|  
|\u000C|\f|Wysuw strony|Biały znak|  
|\u000D|\r|Powrót karetki|Terminator wiersza|  
|\u0020||Miejsce|Biały znak|  
|\u0022|\\"|Podwójny cudzysłów (")||  
|\u0027|\\'|Znak pojedynczego cudzysłowu (')||  
|\u005C|\\\|Ukośnik odwrotny (\\)||  
|\u00A0||Miejsce nierozdzielający|Biały znak|  
|\u2028||Separator wierszy|Terminator wiersza|  
|\u2029||Separator akapitu|Terminator wiersza|  
|\uFEFF||Znacznik porządku bajtów|Biały znak|  
  
 Kolumna kategorii określa, czy znak jest znak ogranicznika biały znak lub wiersza. [Trim — metoda (ciąg)](../../javascript/reference/trim-method-string-javascript.md) usuwa spacji wiodących i końcowych białych i wiersz znaków terminatora z ciągu.  
  
 Ukośnik odwrotny, sam jest używany jako znak ucieczki. W związku z tym nie można bezpośrednio wpisać w skrypcie. Jeśli chcesz zapisać ukośnik odwrotny, należy wpisać dwa z nich razem (\\\\).  
  
> [!NOTE]
>  Począwszy od [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)], nie można zidentyfikować przeglądarki Internet Explorer, testując do pełnienia roli równoważnika tabulator pionowy (\v) i "v". W starszych wersjach, wyrażenie `"\v" === "v"` zwraca `true`. W [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)], wyrażenie zwraca `false`.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie pokazano \\\ i \\"sekwencje specjalne.  
  
### <a name="code"></a>Kod  
  
```JavaScript  
document.write('The image path is C:\\webstuff\\mypage\\gifs\\garden.gif.');  
document.write ("<br />");  
document.write('The caption reads, "After the snow of \'97. Grandma\'s house is covered."');  
```  
  
<a name="CodePoint"></a>   
## <a name="unicode-code-point-escape-sequences"></a>Sekwencje unikowe punkt kodu Unicode  
 W [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)], Unicode jest w pełni obsługiwane. Najbardziej typowe punktów kodowych Unicode są reprezentowane przez cztery cyfry szesnastkowe, takich jak /u0009 dla znak tabulacji. Kod błyszczące punktów, które obejmują wszystkie symbole, które wymagają więcej niż czterech cyfr szesnastkowych, są teraz obsługiwane w formacie uproszczone. Przy użyciu formatu "\u {*punktów kodowych znaków dwuskładnikowych*}", pełny zestaw znaków Unicode, może być reprezentowany w postaci literału. Na przykład do reprezentowania symbol "𠮷", można użyć następującego formatu: "\u{20BB7}".  
  
 W poniższym przykładzie kodu ciągi są wszystkie równoważne. (\uD842\uDFB7 jest metodę obejście, aby określić tego symbolu w poprzednich wersjach).  
  
```JavaScript  
"\u{20BB7}"=="𠮷"=="\uD842\uDFB7"  
```  
  
 RegExp zawiera teraz flagi /u, aby włączyć pełną obsługę punktów błyszczące kodu. Na przykład w poniższym przykładzie kodu flagę /u umożliwia wyrażenia regularnego dopasowanie błyszczące kodu punktów (okres dopasowuje dowolny znak w ciągu podanego).  
  
```JavaScript  
"𠮷".match(/./u)[0].length == 2  
```  
  
 Flaga /u umożliwia analizowanie nowy format \u{codepoint}), sekwencja unikowa jako Unicode. Jest to konieczne, ponieważ \u{xxxxx} bez /u flaga ma inne znaczenie w wyrażeniu regularnym.  
  
> [!NOTE]
>  Punkty kodu błyszczące długość jest zawsze 2. Odpowiada to zachowanie w poprzednich wersjach.  
  
 Z obiektem ciągu zawiera teraz dwa nowe metody, String.codePointAt i String.fromcodepoint —, do obsługi błyszczące kod punktów. Na przykład można użyć codepointat — do zwrócenia punkt kodu równoważne dla symbolu "𠮷".  
  
```JavaScript  
"𠮷".codePointAt(0) == 0x20BB7  
  
```  
  
 Można również wykonać iterację punkty w kodzie za pomocą `for...of` instrukcji.  
  
```JavaScript  
for(var c of "𠮷") {  
    console.log(c);  
}  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcja String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)