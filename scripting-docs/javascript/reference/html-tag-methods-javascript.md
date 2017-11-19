---
title: Metody HTML Tag (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- link method [JavaScript]
- blink method [JavaScript]
- fontsize method [JavaScript]
- italics method [JavaScript]
- sup method [JavaScript]
- anchor method [JavaScript]
- fixed method [JavaScript]
- fontcolor method [JavaScript]
- bold method [JavaScript]
- small method [JavaScript]
- HTML Tag methods [JavaScript]
- sub method [JavaScript]
- big method [JavaScript]
ms.assetid: 50376223-be95-4aa4-9147-9e738a5d3cfa
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7639bc609d8e9b7e4b212fe67ae40f81487d708e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="html-tag-methods-javascript"></a>Metody HTML Tag (JavaScript)
HTML tag — metody służy do umieszczania elementów HTML wokół tekstu w `String` obiektu.  
  
## <a name="syntax"></a>Składnia  
 W poniższej tabeli wymieniono składnia oraz opis poszczególnych metod tagu HTML.  
  
 W kolumnie składni `string1` jest `String` literału lub obiektu.  
  
 Wskazuje kolumny standardowe [sieci World Wide Web konsorcjum W3C](http://go.microsoft.com/fwlink/?LinkId=199553) zalecenia dotyczące HTML 4. "Odradzane" wskazuje, że nie jest zalecane na rzecz arkusze stylów elementu HTML.  
  
|Składnia|Opis elementu — metoda|Opis parametru|Standard|  
|------------|------------------------|---------------------------|--------------|  
|`string1`.Anchor (`name`)|Umieszcza zakotwiczenie HTML, który ma atrybut Nazwa wokół tekstu.|`name` Parametr jest tekst w atrybut NAME elementu zakotwiczenia kodu HTML.||  
|`string1`.big()|Umieszcza HTML \<BIG > tagi wokół tekstu.||Niezalecane|  
|`string1`.BLINK()|Umieszcza HTML \<BLINK > tagi wokół tekstu. \<BLINK > tag nie jest obsługiwana w programie Internet Explorer.||Nie w warstwie standardowa|  
|`string1`.Bold()|Umieszcza HTML \<B > tagi wokół tekstu.||Niezalecane|  
|`string1`.Fixed()|Umieszcza HTML \<TT > tagi wokół tekstu.||Niezalecane|  
|`string1`.fontcolor (`color`)|Umieszcza HTML \<czcionki > tag z atrybutem kolor wokół tekstu.|`color` Parametr ma wartość ciągu, która zawiera wartość szesnastkową lub wstępnie zdefiniowanej nazwy koloru. Prawidłowy kolor wstępnie zdefiniowane nazwy są zależne od [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obsługi przeglądarki i jego wersji.|Przestarzałe|  
|`string1`.FontSize (`size`)|Umieszcza HTML \<czcionki > tag z atrybutem rozmiar wokół tekstu.|`size` Parametr jest wartość całkowita określająca rozmiar tekstu. Prawidłowe wartości całkowite są zależne od [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obsługi przeglądarki i jego wersji.|Przestarzałe|  
|`string1`.italics()|Umieszcza HTML \<I > tagi wokół tekstu.||Niezalecane|  
|`string1`.Link (`href`)|Umieszcza zakotwiczenie HTML, który ma atrybut HREF wokół tekstu.|`href` Parametr jest tekst w atrybucie HREF kotwicy HTML.||  
|`string1`.Small()|Umieszcza HTML \<małych > tagi wokół tekstu.||Niezalecane|  
|`string1`.Strike()|Umieszcza HTML \<ZNALEZIENIA > tagi wokół tekstu.||Przestarzałe|  
|`string1`.Sub()|Umieszcza HTML \<SUB > tagi wokół tekstu.|||  
|`string1`.sup()|Umieszcza HTML \<SUP > tagi wokół tekstu.|||  
  
## <a name="remarks"></a>Uwagi  
 Aby określić, czy znaczniki HTML zostały już zastosowane do ciągu jest przeprowadzane żadne sprawdzanie.  
  
## <a name="example"></a>Przykład  
 Następujące przykłady przedstawiają sposób użycia metody tag HTML.  
  
```JavaScript  
// anchor method.  
var strVariable = "This is an anchor.";  
document.write(strVariable.anchor("Anchor1"));  
// Output: <A NAME="Anchor1">This is an anchor.</A>  
  
// big method.  
var strVariable = "This is a string.";  
document.write(strVariable.big());  
// Output: <BIG>This is a string.</BIG>  
  
//  blink method.  
var strVariable = "This is a string.";  
document.write(strVariable.blink());  
// Output: <BLINK>This is a string.</BLINK>  
  
//  bold method.  
var strVariable = "This is a string.";  
document.write(strVariable.bold());  
// Output: <B>This is a string.</B>  
  
//  fixed method.  
var strVariable = "This is a string.";  
document.write(strVariable.fixed());  
// Output: <TT>This is a string.</TT>  
  
//  fontcolor method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontcolor("red"));  
// Output: <FONT COLOR="red">This is a string.</FONT>  
  
//  fontsize method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontsize(-1));  
// Output: <FONT SIZE="-1">This is a string.</FONT>  
  
//  italics method  
var strVariable = "This is a string.";  
document.write(strVariable.italics());  
// Output: <I>This is a string.</I>  
  
//  link method.  
var strVariable = "This is a hyperlink.";  
document.write(strVariable.link("http://www.microsoft.com"));  
// Output: <A HREF="http://www.microsoft.com">This is a hyperlink.</A>  
  
//  small method.  
var strVariable = "This is a string.";  
document.write(strVariable.small());  
// Output: <SMALL>This is a string.</SMALL>  
  
//  strike method.  
var strVariable = "This is a string.";  
document.write(strVariable.strike());  
// Output: <STRIKE>This is a string.</STRIKE>  
  
//  sub method.  
var strVariable = "This is a string.";  
document.write(strVariable.sub());  
// Output: <SUB>This is a string.</SUB>  
  
//  sup method.  
var strVariable = "This is a string.";  
document.write(strVariable.sup());  
// Output: <SUP>This is a string.</SUP>  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [ciągu obiektu](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [String — obiekt](../../javascript/reference/string-object-javascript.md)