---
title: Informacje o wersji JavaScript | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript, version information
ms.assetid: 440f4924-f7a9-48e0-873e-bd599a93b437
caps.latest.revision: 93
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a2335c3697be9ef3e2d674ac37047ddd3de242d
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2018
ms.locfileid: "29753500"
---
# <a name="javascript-version-information"></a>Informacje o wersji JavaScript
Różne wersje języka JavaScript obsługują różne zbiory jego elementów. [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacje obsługują nieco inny zestaw funkcji w programie Internet Explorer.  
  
> [!IMPORTANT]
>  A [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacja jest nowy typ aplikacji, która działa na [!INCLUDE[win8](../../javascript/includes/win8-md.md)] urządzeń. Aby dowiedzieć się więcej o [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji, zobacz [co to jest aplikacja ze Sklepu Windows?](http://msdn.microsoft.com/en-us/231c1fba-9f87-468e-94aa-45dd57edcc70)  
  
 Tryb standardów (tryb używane we wszystkich wersjach programu Internet Explorer do programu Internet Explorer 11 w przypadku `<!doctype>` dyrektywy) obsługuje inny zestaw elementów niż tryb Osobliwości (tryb używane w przypadku nie `<!doctype>` dyrektywy). Aby uzyskać więcej informacji o wersji, zobacz [Definiowanie zgodności dokumentów](http://go.microsoft.com/fwlink/?LinkId=208537).  
  
 Tabela poniżej zawiera tryby dokumentu programu Internet Explorer (i aplikacji ze sklepu reprezentujący [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] i [!INCLUDE[winphone_appname](../../javascript/reference/includes/winphone-appname-md.md)]) obsługują określonych elementów języka. Tryby dokumentu, które obsługują danego elementu są wyświetlane z literą **Y**, i trybach dokumentu, które nie obsługują danego elementu są wyświetlane z literą **N**.  
  
> [!IMPORTANT]
>  [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] (Przeglądarce edge w systemie Windows 10) nie obsługują tryb starszej wersji dokumentów. Obsługa [!INCLUDE[winphone_appname](../../javascript/reference/includes/winphone-appname-md.md)] uruchamia aplikacje z systemu Windows Phone 8.1. Eksperymentalną (o: flags) są wskazywane przez "Exp".  
  
 Tabela zawiera podsumowanie informacji o. Aby uzyskać dokładniejsze informacje Zobacz dokumentację dla elementu języka.  
  
|Element języka|Osobliwości, standardy programu Internet Explorer 6, standardy programu Internet Explorer 7|Standardy programu Internet Explorer 8|Standardów programu Internet Explorer 9|Standardów programu Internet Explorer 10|Standardów programu Internet Explorer 11|Krawędź|Aplikacje Sklepu|  
|----------------------|--------------------------------------------------------------------------|-----------------------------------|-----------------------------------|------------------------------------|------------------------------------|----------|----------------|  
|[__proto\_ \_ właściwość (obiekt)](../../javascript/reference/proto-property-object-javascript.md)|N|N|N|N|T|T|v8 (Win): N<br />v8.1 (Win): Y<br />v8.1 (Phone): T|  
|[Właściwości $1...$9 (RegExp)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)|T|T|T|T|T|T|T|  
|[Właściwość 0n](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)|T|T|T|T|T|T|T|  
|[ABS — funkcja](../../javascript/reference/math-abs-function-javascript.md)|T|T|T|T|T|T|T|  
|[ACOS — funkcja](../../javascript/reference/math-acos-function-javascript.md)|T|T|T|T|T|T|T|  
|[ACOSH — funkcja](../../javascript/reference/math-acosh-function-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[ActiveXObject, obiekt](../../javascript/reference/activexobject-object-javascript.md)|T|T|T|T|T|T|N|  
|[Operator przypisania dodawania (+=)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)|T|T|T|T|T|T|T|  
|[Operator dodawania (+)](../../javascript/reference/addition-operator-decrement-javascript.md)|T|T|T|T|T|T|T|  
|[Apply — metoda](../../javascript/reference/apply-method-function-javascript.md)|T|T|T|T|T|T|T|  
|[arguments, obiekt](../../javascript/reference/arguments-object-javascript.md)|T|T|T|T|T|T|T|  
|[arguments — właściwość](../../javascript/reference/arguments-property-function-javascript.md)|T|T|T|T|T|T|T|  
|[Array, obiekt](../../javascript/reference/array-object-javascript.md)|T|T|T|T|T|T|T|  
|[Array.from, funkcja (Array)](../../javascript/reference/array-from-function-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Array.isArray, funkcja](../../javascript/reference/array-isarray-function-javascript.md)|N|N|T|T|T|T|T|  
|[Array.of, funkcja (Array)](../../javascript/reference/array-of-function-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[ArrayBuffer, obiekt](../../javascript/reference/arraybuffer-object.md)|N|N|N|T|T|T|T|  
|[Funkcje](../../javascript/functions-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[ASIN — funkcja](../../javascript/reference/math-asin-function-javascript.md)|T|T|T|T|T|T|T|  
|[Object.assign, funkcja (Object)](../../javascript/reference/object-assign-function-object-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Operator przypisania (=)](../../javascript/reference/assignment-operator-decrement-equal-javascript.md)|T|T|T|T|T|T|T|  
|[ATAN — funkcja](../../javascript/reference/math-atan-function-javascript.md)|T|T|T|T|T|T|T|  
|[ATAN2 — funkcja](../../javascript/reference/math-atan2-function-javascript.md)|T|T|T|T|T|T|T|  
|[atEnd — metoda](../../javascript/reference/atend-method-enumerator-javascript.md)|T|T|T|T|T|T|N|  
|[BIND — metoda](../../javascript/reference/bind-method-function-javascript.md)|N|N|T|T|T|T|T|  
|[Operator przypisania iloczynu bitowego AND (&=)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)|T|T|T|T|T|T|T|  
|[Bitowy operator AND (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)|T|T|T|T|T|T|T|  
|[Bitowy Operator przesunięcia w lewo (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|T|T|T|T|T|T|T|  
|[Operator negacji bitowej NOT (~)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|T|T|T|T|T|T|T|  
|[Operator lub Operator przypisania (&#124; =)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)|T|T|T|T|T|T|T|  
|[Bitowe lub operatora (&#124;)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)|T|T|T|T|T|T|T|  
|[Operator przesunięcia bitowego w prawo (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|T|T|T|T|T|T|T|  
|[Operator przypisania Twój bitowe (^ =)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)|T|T|T|T|T|T|T|  
|[Operator Twój bitowe (^)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|T|T|T|T|T|T|T|  
|[BLINK — metoda](../../javascript/reference/html-tag-methods-javascript.md)|T|T|T|T|T|T|T|  
|[Bold — metoda](../../javascript/reference/html-tag-methods-javascript.md)|T|T|T|T|T|T|T|  
|[Boolean, obiekt](../../javascript/reference/boolean-object-javascript.md)|T|T|T|T|T|T|T|  
|[break, instrukcja](../../javascript/reference/break-statement-javascript.md)|T|T|T|T|T|T|T|  
|[Wywołaj metodę](../../javascript/reference/call-method-function-javascript.md)|T|T|T|T|T|T|T|  
|[callee — właściwość](../../javascript/reference/callee-property-arguments-javascript.md)|T|T|T|T|T|T|T|  
|[caller — właściwość](../../javascript/reference/caller-property-function-javascript.md)|T|T|T|T|T|T|T|  
|[CATCH — instrukcja](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|T|T|T|T|T|T|T|  
|[ceil — funkcja](../../javascript/reference/math-ceil-function-javascript.md)|T|T|T|T|T|T|T|  
|[charAt — metoda](../../javascript/reference/charat-method-string-javascript.md)|T|T|T|T|T|T|T|  
|[charCodeAt — metoda](../../javascript/reference/charcodeat-method-string-javascript.md)|T|T|T|T|T|T|T|  
|[class, instrukcja](../../javascript/reference/class-statement-javascript.md)|N|N|N|N|N|EXP.|v8.1: N<br />v10: Exp.|  
|[codePointAt, metoda (String)](../../javascript/reference/codepointat-method-string-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[Operator przecinkowy (,)](../../javascript/reference/comma-operator-decrement-javascript.md)|T|T|T|T|T|T|T|  
|[(Jednowierszowego komentarza instrukcji)](../../javascript/reference/comment-statements-javascript.md)|T|T|T|T|T|T|T|  
|[/*.. \*/ (Multiline Comment instrukcji)](../../javascript/reference/comment-statements-javascript.md)|T|T|T|T|T|T|T|  
|[Operatory porównania](../../javascript/reference/comparison-operators-javascript.md)|T|T|T|T|T|T|T|  
|[Compile — metoda](../../javascript/reference/compile-method-regular-expression-javascript.md)|T|T|T|T|T|T|T|  
|[concat, metoda (Array)](../../javascript/reference/concat-method-array-javascript.md)|T|T|T|T|T|T|T|  
|[concat, metoda (String)](../../javascript/reference/concat-method-string-javascript.md)|T|T|T|T|T|T|T|  
|[Kompilacja warunkowa](../../javascript/advanced/conditional-compilation-javascript.md)|T|T|T|T|N|N|N|  
|[Zmienne kompilacji warunkowej](../../javascript/advanced/conditional-compilation-variables-javascript.md)|T|T|T|T|N|N|N|  
|[Operator warunkowy (trójargumentowy) (?:)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|T|T|T|T|T|T|T|  
|[constructor — właściwość](../../javascript/reference/constructor-property-object-javascript.md)|T|T|T|T|T|T|T|  
|[Const, instrukcja](../../javascript/reference/const-statement-javascript.md)|N|N|N|N|T|T|v8 (Win): N<br />v8.1 (Win): Y<br />v8.1 (Phone): T|  
|[continue, instrukcja](../../javascript/reference/continue-statement-javascript.md)|T|T|T|T|T|T|T|  
|[COS — funkcja](../../javascript/reference/math-cos-function-javascript.md)|T|T|T|T|T|T|T|  
|[Create — funkcja](../../javascript/reference/object-create-function-javascript.md)|N|N|T|T|T|T|T|  
|[DataView, obiekt](../../javascript/reference/dataview-object.md)|N|N|N|T|T|T|T|  
|[Date, obiekt](../../javascript/reference/date-object-javascript.md)|T|T|T|T|T|T|T|  
|[Debug, obiekt](../../javascript/reference/debug-object-javascript.md)|T|T|T|T|T|T|T|  
|[Debug.setNonUserCodeExceptions, właściwość](../../javascript/reference/debug-setnonusercodeexceptions-property.md)|N|N|N|T|T|T|T|  
|[Debug.setNonUserCodeExceptions, właściwość](../../javascript/reference/debug-setnonusercodeexceptions-property.md)|N|N|N|T|T|T|T|  
|[debugger, instrukcja](../../javascript/reference/debugger-statement-javascript.md)|T|T|T|T|T|T|T|  
|[decodeURI, funkcja](../../javascript/reference/decodeuri-function-javascript.md)|T|T|T|T|T|T|T|  
|[Decodeuricomponent — funkcja](../../javascript/reference/decodeuricomponent-function-javascript.md)|T|T|T|T|T|T|T|  
|[Operator dekrementacji (-)](../../javascript/reference/increment-and-decrement-operators-javascript.md)|T|T|T|T|T|T|T|  
|[Funkcje](../../javascript/functions-javascript.md)|N|N|N|N|N|EXP.|v8.1: N<br />v10: Exp.|  
|[defineProperties — funkcja](../../javascript/reference/object-defineproperties-function-javascript.md)|N|T*|T|T|T|T|T|  
|[defineProperty — funkcja](../../javascript/reference/object-defineproperty-function-javascript.md)|N|T*|T|T|T|T|T|  
|[Operator delete](../../javascript/reference/delete-operator-decrementjavascript.md)|T|T|T|T|T|T|T|  
|[Description — właściwość](../../javascript/reference/description-property-error-javascript.md)|T|T|T|T|T|T|T|  
|[Dimensions — metoda](../../javascript/reference/dimensions-method-vbarray-javascript.md)|T|T|T|T|T|T|T|  
|[Operator przypisania dzielenia (/=)](../../javascript/reference/division-assignment-operator-decrement-equal-javascript.md)|T|T|T|T|T|T|T|  
|[Operator dzielenia (/)](../../javascript/reference/division-operator-decrement-javascript.md)|T|T|T|T|T|T|T|  
|[do...while, instrukcja](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)|T|T|T|T|T|T|T|  
|[E — stała](../../javascript/reference/math-constants-javascript.md)|T|T|T|T|T|T|T|  
|[encodeURI, funkcja](../../javascript/reference/encodeuri-function-javascript.md)|T|T|T|T|T|T|T|  
|[Składnik funkcja encodeURI](../../javascript/reference/encodeuricomponent-function-javascript.md)|T|T|T|T|T|T|T|  
|[entries, metoda (Array)](../../javascript/reference/entries-method-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Enumerator, obiekt](../../javascript/reference/enumerator-object-javascript.md)|T|T|T|T|T|T|N|  
|[Number, stałe](../../javascript/reference/number-constants-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Operator równości (==)](../../javascript/reference/comparison-operators-javascript.md)|T|T|T|T|T|T|T|  
|[Error, obiekt](../../javascript/reference/error-object-javascript.md)|T|T|T|T|T|T|T|  
|[stack, właściwość (Error)](../../javascript/reference/stack-property-error-javascript.md)|N|N|N|T|T|T|T|  
|[stackTraceLimit, właściwość (Error)](../../javascript/reference/stacktracelimit-property-error-javascript.md)|N|N|N|T|T|T|T|  
|[escape, funkcja](../../javascript/reference/escape-function-javascript.md)|T|T|T|T|T|T|T|  
|[eval, funkcja](../../javascript/reference/eval-function-javascript.md)|T|T|T|T|T|T|T|  
|[exec — metoda](../../javascript/reference/exec-method-regular-expression-javascript.md)|T|T|T|T|T|T|T|  
|[EVERY — metoda](../../javascript/reference/every-method-array-javascript.md)|N|N|T|T|T|T|T|  
|[EXP — funkcja](../../javascript/reference/math-exp-function-javascript.md)|T|T|T|T|T|T|T|  
|[fill, metoda (Array)](../../javascript/reference/fill-method-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Filter — metoda](../../javascript/reference/filter-method-array-javascript.md)|N|N|T|T|T|T|T|  
|[finally — instrukcja](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|T|T|T|T|T|T|T|  
|[findIndex, metoda (Array)](../../javascript/reference/findindex-method-array-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[Fixed — metoda](../../javascript/reference/html-tag-methods-javascript.md)|T|T|T|T|T|T|T|  
|[Float32Array, obiekt](../../javascript/reference/float32array-object.md)|N|N|N|T|T|T|T|  
|[Float64Array, obiekt](../../javascript/reference/float64array-object.md)|N|N|N|T|T|T|T|  
|[FLOOR — funkcja](../../javascript/reference/math-floor-function-javascript.md)|T|T|T|T|T|T|T|  
|[fontcolor — metoda](../../javascript/reference/html-tag-methods-javascript.md)|T|T|T|T|T|T|T|  
|[FontSize — metoda](../../javascript/reference/html-tag-methods-javascript.md)|T|T|T|T|T|T|T|  
|[for, instrukcja](../../javascript/reference/for-statement-javascript.md)|T|T|T|T|T|T|T|  
|[forEach — metoda](../../javascript/reference/foreach-method-array-javascript.md)|N|N|T|T|T|T|T|  
|[for...in, instrukcja](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)|T|T|T|T|T|T|T|  
|[for...of, instrukcja](../../javascript/reference/for-dot-dot-dot-of-statement-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[FREEZE — funkcja](../../javascript/reference/object-freeze-function-javascript.md)|N|N|T|T|T|T|T|  
|[fromCharCode — funkcja](../../javascript/reference/string-fromcharcode-function-javascript.md)|T|T|T|T|T|T|T|  
|[fromCodePoint — funkcja](../../javascript/reference/string-fromcodepoint-function-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[Function, obiekt](../../javascript/reference/function-object-javascript.md)|T|T|T|T|T|T|T|  
|[function, instrukcja](../../javascript/reference/function-statement-javascript.md)|T|T|T|T|T|T|T|  
|[Generatory kodu](../../javascript/advanced/iterators-and-generators-javascript.md)|N|N|N|N|N|EXP.|v8.1: N<br />v10: Exp.|  
|[getDate — metoda](../../javascript/reference/getdate-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[getDay — metoda](../../javascript/reference/getday-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[getFullYear — metoda](../../javascript/reference/getfullyear-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[getHours — metoda](../../javascript/reference/gethours-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[getItem — metoda](../../javascript/reference/getitem-method-vbarray-javascript.md)|T|T|T|T|T|T|T|  
|[getMilliseconds — metoda](../../javascript/reference/getmilliseconds-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[getMinutes — metoda](../../javascript/reference/getminutes-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[getMonth — metoda](../../javascript/reference/getmonth-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[GetObject, funkcja](../../javascript/reference/getobject-function-javascript.md)|T|T|N|N|N|N|N|  
|[getOwnPropertyDescriptor — funkcja](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|N|T*|T|T|T|T|T|  
|[getOwnPropertyNames Function](../../javascript/reference/object-getownpropertynames-function-javascript.md)|N|N|T|T|T|T|T|  
|[getprototypeof — funkcja](../../javascript/reference/object-getprototypeof-function-javascript.md)|N|N|T|T|T|T|T|  
|[getSeconds — metoda](../../javascript/reference/getseconds-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[getTime — metoda](../../javascript/reference/gettime-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[getTimezoneOffset — metoda](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[getUTCDate — metoda](../../javascript/reference/getutcdate-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[getUTCDay — metoda](../../javascript/reference/getutcday-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[getUTCFullYear — metoda](../../javascript/reference/getutcfullyear-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[getUTCHours — metoda](../../javascript/reference/getutchours-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[getUTCMilliseconds — metoda](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[getUTCMinutes — metoda](../../javascript/reference/getutcminutes-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[getUTCMonth — metoda](../../javascript/reference/getutcmonth-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[getUTCSeconds — metoda](../../javascript/reference/getutcseconds-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[getVarDate — metoda](../../javascript/reference/getvardate-method-date-javascript.md)|T|T|T|T|T|T|N|  
|[getYear — metoda](../../javascript/reference/getyear-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[Global, obiekt](../../javascript/reference/global-object-javascript.md)|T|T|T|T|T|T|T|  
|[global Property](../../javascript/reference/global-property-regular-expression-javascript.md)|T|T|T|T|T|T|T|  
|[Większe niż — Operator (>)](../../javascript/reference/comparison-operators-javascript.md)|T|T|T|T|T|T|T|  
|[Większe lub równe — Operator (> =)](../../javascript/reference/comparison-operators-javascript.md)|T|T|T|T|T|T|T|  
|[hasOwnProperty — metoda](../../javascript/reference/hasownproperty-method-object-javascript.md)|T|T|T|T|T|T|T|  
|[Metody HTML Tag](../../javascript/reference/html-tag-methods-javascript.md)|T|T|T|T|T|T|T|  
|[hypot — funkcja](../../javascript/reference/math-hypot-function-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[Tożsamość — Operator (=)](../../javascript/reference/comparison-operators-javascript.md)|T|T|T|T|T|T|T|  
|[if...else, instrukcja](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)|T|T|T|T|T|T|T|  
|[ignoreCase właściwość](../../javascript/reference/ignorecase-property-regular-expression-javascript.md)|T|T|T|T|T|T|T|  
|[imul — funkcja](../../javascript/reference/math-imul-function-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[In — Operator](../../javascript/reference/in-operator-decrementjavascript.md)|T|T|T|T|T|T|T|  
|[includes, metoda (String)](../../javascript/reference/includes-method-string-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[Operator inkrementacji (++)](../../javascript/reference/increment-and-decrement-operators-javascript.md)|T|T|T|T|T|T|T|  
|[INDEX — właściwość](../../javascript/reference/index-property-regexp-javascript.md)|T|T|T|T|T|T|T|  
|[indexOf, metoda (Array)](../../javascript/reference/indexof-method-array-javascript.md)|N|N|T|T|T|T|T|  
|[indexOf, metoda (String)](../../javascript/reference/indexof-method-string-javascript.md)|T|T|T|T|T|T|T|  
|[Operator nierówności (! =)](../../javascript/reference/comparison-operators-javascript.md)|T|T|T|T|T|T|T|  
|[Infinity, stała](../../javascript/reference/infinity-constant-javascript.md)|T|T|T|T|T|T|T|  
|[Input — właściwość ($_)](../../javascript/reference/input-property-dollar-regexp-javascript.md)|T|T|T|T|T|T|T|  
|[Operator instanceof](../../javascript/reference/instanceof-operator-decrementjavascript.md)|T|T|T|T|T|T|T|  
|[Int8Array, obiekt](../../javascript/reference/int8array-object.md)|N|N|N|T|T|T|T|  
|[Int16Array, obiekt](../../javascript/reference/int16array-object.md)|N|N|N|T|T|T|T|  
|[Int32Array, obiekt](../../javascript/reference/int32array-object.md)|N|N|N|T|T|T|T|  
|[Intl.Collator, obiekt](../../javascript/reference/intl-collator-object-javascript.md)|N|N|N|N|T|T|v8 (Win): N<br />v8.1 (Win): Y<br />v8.1 (Phone): T|  
|[Intl.DateTimeFormat, obiekt](../../javascript/reference/intl-datetimeformat-object-javascript.md)|N|N|N|N|T|T|v8: N<br />v8.1: T|  
|[Intl.NumberFormat, obiekt](../../javascript/reference/intl-numberformat-object-javascript.md)|N|N|N|N|T|T|v8: N<br />v8.1: T|  
|[isFinite, funkcja](../../javascript/reference/isfinite-function-javascript.md)|T|T|T|T|T|T|T|  
|[isArray — funkcja](../../javascript/reference/array-isarray-function-javascript.md)|N|N|T|T|T|T|T|  
|[Isextensible — funkcja](../../javascript/reference/object-isextensible-function-javascript.md)|N|N|T|T|T|T|T|  
|[isFrozen — funkcja](../../javascript/reference/object-isfrozen-function-javascript.md)|N|N|T|T|T|T|T|  
|[isInteger — funkcja](../../javascript/reference/number-isinteger-function-number-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[isNaN, funkcja](../../javascript/reference/isnan-function-javascript.md)|T|T|T|T|T|T|T|  
|[isNaN — funkcja (numer)](../../javascript/reference/number-isnan-function-number-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[Format daty ISO](../../javascript/date-and-time-strings-javascript.md)|N|N|T|T|T|T|T|  
|[IsPrototypeOf — metoda](../../javascript/reference/isprototypeof-method-object-javascript.md)|T|T|T|T|T|T|T|  
|[issealed — funkcja](../../javascript/reference/object-issealed-function-javascript.md)|N|N|T|T|T|T|T|  
|[italics — metoda](../../javascript/reference/html-tag-methods-javascript.md)|T|T|T|T|T|T|T|  
|[Iteratory](../../javascript/advanced/iterators-and-generators-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[Item — metoda](../../javascript/reference/item-method-enumerator-javascript.md)|T|T|T|T|T|T|T|  
|[JOIN — metoda](../../javascript/reference/join-method-array-javascript.md)|T|T|T|T|T|T|T|  
|[JSON, obiekt](../../javascript/reference/json-object-javascript.md)|N|T|T|T|T|T|T|  
|[klucze — funkcja](../../javascript/reference/object-keys-function-javascript.md)|N|N|T|T|T|T|T|  
|[keys, metoda (Array)](../../javascript/reference/keys-method-array-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[labeled, instrukcja](../../javascript/reference/labeled-statement-javascript.md)|T|T|T|T|T|T|T|  
|[lastIndex właściwość](../../javascript/reference/lastindex-property-regexp-javascript.md)|T|T|T|T|T|T|T|  
|[lastIndexOf, metoda (Array)](../../javascript/reference/lastindexof-method-array-javascript.md)|N|N|T|T|T|T|T|  
|[lastIndexOf, metoda (String)](../../javascript/reference/lastindexof-method-string-javascript.md)|T|T|T|T|T|T|T|  
|[lastMatch właściwość ($&)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)|T|T|T|T|T|T|T|  
|[lastParen właściwość ($ +)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)|T|T|T|T|T|T|T|  
|[LBound — metoda](../../javascript/reference/lbound-method-vbarray-javascript.md)|T|T|T|T|T|T|T|  
|[leftContext właściwość ($')](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)|T|T|T|T|T|T|T|  
|[Operator przypisania przesunięcia bitowego w lewo (<<=)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)|T|T|T|T|T|T|T|  
|[length — właściwość (argumenty)](../../javascript/reference/length-property-arguments-javascript.md)|T|T|T|T|T|T|T|  
|[length, właściwość (Array)](../../javascript/reference/length-property-array-javascript.md)|T|T|T|T|T|T|T|  
|[length, właściwość (Function)](../../javascript/reference/length-property-function-javascript.md)|T|T|T|T|T|T|T|  
|[length, właściwość (String)](../../javascript/reference/length-property-string-javascript.md)|T|T|T|T|T|T|T|  
|[Mniejsze niż — Operator (<)](../../javascript/reference/comparison-operators-javascript.md)|T|T|T|T|T|T|T|  
|[Mniejsze niż lub równe — Operator (< =)](../../javascript/reference/comparison-operators-javascript.md)|T|T|T|T|T|T|T|  
|[let, instrukcja](../../javascript/reference/let-statement-javascript.md)|N|N|N|N|T|T|v8: N<br />v8.1: T|  
|[Link — metoda](../../javascript/reference/html-tag-methods-javascript.md)|T|T|T|T|T|T|T|  
|[Ln2 — stała](../../javascript/reference/math-constants-javascript.md)|T|T|T|T|T|T|T|  
|[Ln10 — stała](../../javascript/reference/math-constants-javascript.md)|T|T|T|T|T|T|T|  
|[localeCompare — metoda](../../javascript/reference/localecompare-method-string-javascript.md)|T|T|T|T|T|T|T|  
|[log — funkcja](../../javascript/reference/math-log-function-javascript.md)|T|T|T|T|T|T|T|  
|[Log2e — stała](../../javascript/reference/math-constants-javascript.md)|T|T|T|T|T|T|T|  
|[Log10e — stała](../../javascript/reference/math-constants-javascript.md)|T|T|T|T|T|T|T|  
|[Operator logiczny AND (&&)](../../javascript/reference/logical-and-operator-decrement-javascript.md)|T|T|T|T|T|T|T|  
|[Operator logiczny NOT (!)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|T|T|T|T|T|T|T|  
|[Operatora logicznego OR — Operator (&#124; &#124;)](../../javascript/reference/logical-or-operator-decrement-javascript.md)|T|T|T|T|T|T|T|  
|[map — metoda](../../javascript/reference/map-method-array-javascript.md)|N|N|T|T|T|T|T|  
|[Map, obiekt](../../javascript/reference/map-object-javascript.md)|N|N|N|N|T|T|v8: N<br />v8.1: T|  
|[Match — metoda](../../javascript/reference/match-method-string-javascript.md)|T|T|T|T|T|T|T|  
|[Math, obiekt](../../javascript/reference/math-object-javascript.md)|T|T|T|T|T|T|T|  
|[MAX — funkcja](../../javascript/reference/math-max-function-javascript.md)|T|T|T|T|T|T|T|  
|[MAX_VALUE — stała](../../javascript/reference/number-constants-javascript.md)|T|T|T|T|T|T|T|  
|[Message — właściwość](../../javascript/reference/message-property-error-javascript.md)|T|T|T|T|T|T|T|  
|[min — funkcja](../../javascript/reference/math-min-function-javascript.md)|T|T|T|T|T|T|T|  
|[MIN_VALUE — stała](../../javascript/reference/number-constants-javascript.md)|T|T|T|T|T|T|T|  
|[Remainder — Operator przypisania (% =)](../../javascript/reference/modulus-assignment-operator-decrement-javascript.md)|T|T|T|T|T|T|T|  
|[Operator reszty (%)](../../javascript/reference/modulus-operator-decrementjavascript.md)|T|T|T|T|T|T|T|  
|[moveFirst — metoda](../../javascript/reference/movefirst-method-enumerator-javascript.md)|T|T|T|T|T|T|T|  
|[moveNext — metoda](../../javascript/reference/movenext-method-enumerator-javascript.md)|T|T|T|T|T|T|T|  
|[multiline — właściwość](../../javascript/reference/multiline-property-regular-expression-javascript.md)|T|T|T|T|T|T|T|  
|[Operator przypisania mnożenia (*=)](../../javascript/reference/multiplication-assignment-operator-decrement-equal-javascript.md)|T|T|T|T|T|T|T|  
|[Operator mnożenia (*)](../../javascript/reference/multiplication-operator-decrement-javascript.md)|T|T|T|T|T|T|T|  
|[name Property](../../javascript/reference/name-property-error-javascript.md)|T|T|T|T|T|T|T|  
|[NaN — stała (globalna)](../../javascript/reference/nan-constant-javascript.md)|T|T|T|T|T|T|T|  
|[NaN — stała (numer)](../../javascript/reference/number-constants-javascript.md)|T|T|T|T|T|T|T|  
|[Negative_infinity — stała](../../javascript/reference/number-constants-javascript.md)|T|T|T|T|T|T|T|  
|[new, operator](../../javascript/reference/new-operator-decrementjavascript.md)|T|T|T|T|T|T|T|  
|[Nonidentity Operator (! ==)](../../javascript/reference/comparison-operators-javascript.md)|T|T|T|T|T|T|T|  
|[Funkcja Now](../../javascript/reference/date-now-function-javascript.md)|N|N|T|T|T|T|T|  
|[Number, obiekt](../../javascript/reference/number-object-javascript.md)|T|T|T|T|T|T|T|  
|[Właściwość numeru](../../javascript/reference/number-property-error-javascript.md)|T|T|T|T|T|T|T|  
|[Object, obiekt](../../javascript/reference/object-object-javascript.md)|T|T|T|T|T|T|T|  
|[Pierwszeństwo operatorów](../../javascript/operator-subtractprecedence-javascript.md)|T|T|T|T|T|T|T|  
|[Date.parse, funkcja](../../javascript/reference/date-parse-function-javascript.md)|T|T|T|T|T|T|T|  
|[JSON.parse, funkcja](../../javascript/reference/json-parse-function-javascript.md)|N|T|T|T|T|T|T|  
|[parseFloat, funkcja](../../javascript/reference/parsefloat-function-javascript.md)|T|T|T|T|T|T|T|  
|[parseInt, funkcja](../../javascript/reference/parseint-function-javascript.md)|T|T|T|T|T|T|T|  
|[PI — stała](../../javascript/reference/math-constants-javascript.md)|T|T|T|T|T|T|T|  
|[POP — metoda](../../javascript/reference/pop-method-array-javascript.md)|T|T|T|T|T|T|T|  
|[Positive_infinity — stała](../../javascript/reference/number-constants-javascript.md)|T|T|T|T|T|T|T|  
|[Funkcja Pow](../../javascript/reference/math-pow-function-javascript.md)|T|T|T|T|T|T|T|  
|[preventextensions — funkcja](../../javascript/reference/object-preventextensions-function-javascript.md)|N|N|T|T|T|T|T|  
|[Promise, obiekt](../../javascript/reference/promise-object-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[prototype — właściwość](../../javascript/reference/prototype-property-object-javascript.md)|T|T|T|T|T|T|T|  
|[propertyIsEnumerable — metoda](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|T|T|T|T|T|T|T|  
|[Proxy, obiekt](../../javascript/reference/proxy-object-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[push — metoda](../../javascript/reference/push-method-array-javascript.md)|T|T|T|T|T|T|T|  
|[Funkcja losowych](../../javascript/reference/math-random-function-javascript.md)|T|T|T|T|T|T|T|  
|[RAW — funkcja](../../javascript/reference/string-raw-function-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[Reduce — metoda](../../javascript/reference/reduce-method-array-javascript.md)|N|N|T|T|T|T|T|  
|[reduceRight — metoda](../../javascript/reference/reduceright-method-array-javascript.md)|N|N|T|T|T|T|T|  
|[RegExp, obiekt](../../javascript/reference/regexp-object-javascript.md)|T|T|T|T|T|T|T|  
|[Regular Expression, obiekt](../../javascript/reference/regular-expression-object-javascript.md)|T|T|T|T|T|T|T|  
|[Składnia wyrażeń regularnych](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)|T|T|T|T|T|T|T|  
|[Regularne flagi /y wyrażenia](../../javascript/reference/regular-expression-object-javascript.md)|N|N|N|N|N|EXP.|v8.1: N<br />v10: Exp.|  
|[repeat, metoda (String)](../../javascript/reference/repeat-method-string-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[replace — metoda](../../javascript/reference/replace-method-string-javascript.md)|T|T|T|T|T|T|T|  
|[Funkcje](../../javascript/functions-javascript.md)|N|N|N|N|N|N|v8.1: N<br />v10: Y|  
|[return, instrukcja](../../javascript/reference/return-statement-javascript.md)|T|T|T|T|T|T|T|  
|[reverse, metoda](../../javascript/reference/reverse-method-javascript.md)|T|T|T|T|T|T|T|  
|[rightContext właściwość ($')](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)|T|T|T|T|T|T|T|  
|[Operator przypisania przesunięcia bitowego w prawo (>>=)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)|T|T|T|T|T|T|T|  
|[ROUND — funkcja](../../javascript/reference/math-round-function-javascript.md)|T|T|T|T|T|T|T|  
|[ScriptEngine, funkcja](../../javascript/reference/scriptengine-function-javascript.md)|T|T|T|T|T|T|T|  
|[ScriptEngineBuildVersion, funkcja](../../javascript/reference/scriptenginebuildversion-function-javascript.md)|T|T|T|T|T|T|T|  
|[ScriptEngineMajorVersion, funkcja](../../javascript/reference/scriptenginemajorversion-function-javascript.md)|T|T|T|T|T|T|T|  
|[ScriptEngineMinorVersion, funkcja](../../javascript/reference/scriptengineminorversion-function-javascript.md)|T|T|T|T|T|T|T|  
|[Seal — funkcja](../../javascript/reference/object-seal-function-javascript.md)|N|N|T|T|T|T|T|  
|[Search — metoda](../../javascript/reference/search-method-string-javascript.md)|T|T|T|T|T|T|T|  
|[Set, obiekt](../../javascript/reference/set-object-javascript.md)|N|N|N|N|T|T|v8: N<br />v8.1: T|  
|[setDate — metoda](../../javascript/reference/setdate-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[setFullYear — metoda](../../javascript/reference/setfullyear-method-date-javascript.md)||T|T|T|T|T|T|  
|[setHours — metoda](../../javascript/reference/sethours-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[setMilliseconds — metoda](../../javascript/reference/setmilliseconds-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[setMinutes — metoda](../../javascript/reference/setminutes-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[setMonth — metoda](../../javascript/reference/setmonth-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[setSeconds — metoda](../../javascript/reference/setseconds-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[setTime — metoda](../../javascript/reference/settime-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[setUTCDate — metoda](../../javascript/reference/setutcdate-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[setUTCFullYear — metoda](../../javascript/reference/setutcfullyear-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[setUTCHours — metoda](../../javascript/reference/setutchours-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[setUTCMilliseconds — metoda](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[setUTCMinutes — metoda](../../javascript/reference/setutcminutes-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[setUTCMonth — metoda](../../javascript/reference/setutcmonth-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[setUTCSeconds — metoda](../../javascript/reference/setutcseconds-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[setYear — metoda](../../javascript/reference/setyear-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[SHIFT — metoda](../../javascript/reference/shift-method-array-javascript.md)|T|T|T|T|T|T|T|  
|[SIN — funkcja](../../javascript/reference/math-sin-function-javascript.md)|T|T|T|T|T|T|T|  
|[slice, metoda (Array)](../../javascript/reference/slice-method-array-javascript.md)|T|T|T|T|T|T|T|  
|[slice, metoda (String)](../../javascript/reference/slice-method-string-javascript.md)|T|T|T|T|T|T|T|  
|[Small — metoda](../../javascript/reference/html-tag-methods-javascript.md)|T|T|T|T|T|T|T|  
|[Some — metoda](../../javascript/reference/some-method-array-javascript.md)|N|N|T|T|T|T|T|  
|[sort — metoda](../../javascript/reference/sort-method-array-javascript.md)|T|T|T|T|T|T|T|  
|[Właściwość źródła](../../javascript/reference/source-property-regular-expression-javascript.md)|T|T|T|T|T|T|T|  
|[splice — metoda](../../javascript/reference/splice-method-array-javascript.md)|T|T|T|T|T|T|T|  
|[split — metoda](../../javascript/reference/split-method-string-javascript.md)|T|T|T|T|T|T|T|  
|[Funkcje](../../javascript/functions-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[SQRT — funkcja](../../javascript/reference/math-sqrt-function-javascript.md)|T|T|T|T|T|T|T|  
|[Sqrt1_2 — stała](../../javascript/reference/math-constants-javascript.md)|T|T|T|T|T|T|T|  
|[Sqrt2 — stała](../../javascript/reference/math-constants-javascript.md)|T|T|T|T|T|T|T|  
|[Dyrektywa use strict](../../javascript/reference/use-strict-directive.md)|N|N|N|T|T|T|T|  
|[znalezienia — metoda](../../javascript/reference/html-tag-methods-javascript.md)|T|T|T|T|T|T|T|  
|[String, obiekt](../../javascript/reference/string-object-javascript.md)|T|T|T|T|T|T|T|  
|[JSON.stringify, funkcja](../../javascript/reference/json-stringify-function-javascript.md)|N|T|T|T|T|T|T|  
|[Sub — metoda](../../javascript/reference/html-tag-methods-javascript.md)|T|T|T|T|T|T|T|  
|[substr — metoda](../../javascript/reference/substr-method-string-javascript.md)|T|T|T|T|T|T|T|  
|[substring — metoda](../../javascript/reference/substring-method-string-javascript.md)|T|T|T|T|T|T|T|  
|[Operator przypisania odejmowania (-=)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)|T|T|T|T|T|T|T|  
|[Operator odejmowania (-)](../../javascript/reference/subtraction-operator-decrement-javascript.md)|T|T|T|T|T|T|T|  
|[sup — metoda](../../javascript/reference/html-tag-methods-javascript.md)|T|T|T|T|T|T|T|  
|[switch, instrukcja](../../javascript/reference/switch-statement-javascript.md)|T|T|T|T|T|T|T|  
|[Symbol, obiekt](../../javascript/reference/symbol-object-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[tan — funkcja](../../javascript/reference/math-tan-function-javascript.md)|T|T|T|T|T|T|T|  
|[Ciągi szablonu](../../javascript/advanced/template-strings-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[Test — metoda](../../javascript/reference/test-method-regular-expression-javascript.md)|T|T|T|T|T|T|T|  
|[this, instrukcja](../../javascript/reference/this-statement-javascript.md)|T|T|T|T|T|T|T|  
|[throw, instrukcja](../../javascript/reference/throw-statement-javascript.md)|T|T|T|T|T|T|T|  
|[toArray — metoda](../../javascript/reference/toarray-method-vbarray-javascript.md)|T|T|T|T|T|T|T|  
|[toDateString — metoda](../../javascript/reference/todatestring-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[toExponential — metoda](../../javascript/reference/toexponential-method-number-javascript.md)|T|T|T|T|T|T|T|  
|[toFixed — metoda](../../javascript/reference/tofixed-method-number-javascript.md)|T|T|T|T|T|T|T|  
|[toGMTString — metoda](../../javascript/reference/togmtstring-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[toISOString — metoda](../../javascript/reference/toisostring-method-date-javascript.md)|N|N|T|T|T|T|T|  
|[toJSON — metoda](../../javascript/reference/tojson-method-date-javascript.md)|N|T|T|T|T|T|T|  
|[toLocaleDateString — metoda](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[toLocaleLowercase — metoda](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|T|T|T|T|T|T|T|  
|[toLocaleString — metoda](../../javascript/reference/tolocalestring-method-object-javascript.md)|T|T|T|T|T|T|T|  
|[toLocaleTimeString — metoda](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[toLocaleUppercase — metoda](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|T|T|T|T|T|T|T|  
|[toLowerCase, metoda](../../javascript/reference/tolowercase-method-javascript.md)|T|T|T|T|T|T|T|  
|[toPrecision — metoda](../../javascript/reference/toprecision-method-number-javascript.md)|T|T|T|T|T|T|T|  
|[toString — metoda](../../javascript/reference/tostring-method-object-javascript.md)|T|T|T|T|T|T|T|  
|[toTimeString — metoda](../../javascript/reference/totimestring-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[toUpperCase — metoda](../../javascript/reference/touppercase-method-string-javascript.md)|T|T|T|T|T|T|T|  
|[toUTCString — metoda](../../javascript/reference/toutcstring-method-date-javascript.md)|T|T|T|T|T|T|T|  
|[TRIM — metoda](../../javascript/reference/trim-method-string-javascript.md)|N|N|T|T|T|T|T|  
|[Instrukcja try](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)|T|T|T|T|T|T|T|  
|[Operator typeof](../../javascript/reference/typeof-operator-decrementjavascript.md)|T|T|T|T|T|T|T|  
|[UBound — metoda](../../javascript/reference/ubound-method-vbarray-javascript.md)|T|T|T|T|T|T|T|  
|[Uint8Array, obiekt](../../javascript/reference/uint8array-object.md)|N|N|N|T|T|T|T|  
|[Uint16Array, obiekt](../../javascript/reference/uint16array-object.md)|N|N|N|T|T|T|T|  
|[Uint32Array, obiekt](../../javascript/reference/uint32array-object.md)|N|N|N|T|T|T|T|  
|[Uint8ClampedArray, obiekt](../../javascript/reference/uint8clampedarray-object-javascript.md)|N|N|N|N|T|T|v8: nie<br />v8.1 (Win): Tak<br />v8.1 (Phone): Nie<br />v10: Y|  
|[Jednoargumentowy Operator negacji (-)](../../javascript/reference/subtraction-operator-decrement-javascript.md)|T|T|T|T|T|T|T|  
|[undefined, stała](../../javascript/reference/undefined-constant-javascript.md)|T|T|T|T|T|T|T|  
|[unescape, funkcja](../../javascript/reference/unescape-function-javascript.md)|T|T|T|T|T|T|T|  
|[Znaki specjalne punkt kodu Unicode](../../javascript/advanced/special-characters-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[unshift — metoda](../../javascript/reference/unshift-method-array-javascript.md)|T|T|T|T|T|T|T|  
|[Operator przypisania przesunięcia w prawo bez znaku (>>>=)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)|T|T|T|T|T|T|T|  
|[Operator przesunięcia bitowego w prawo bez znaku (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|T|T|T|T|T|T|T|  
|[Dyrektywa use strict](../../javascript/reference/use-strict-directive.md)|N|N|N|T|T|T|T|  
|[UTC — funkcja](../../javascript/reference/date-utc-function-javascript.md)|T|T|T|T|T|T|T|  
|[valueOf — metoda](../../javascript/reference/valueof-method-object-javascript.md)|T|T|T|T|T|T|T|  
|[values, metoda (Array)](../../javascript/reference/values-method-array-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[var, instrukcja](../../javascript/reference/var-statement-javascript.md)|T|T|T|T|T|T|T|  
|[VBArray, obiekt](../../javascript/reference/vbarray-object-javascript.md)|T|T|T|T|T|T|N|  
|[Operator void](../../javascript/reference/void-operator-decrementjavascript.md)|T|T|T|T|T|T|T|  
|[WeakMap, obiekt](../../javascript/reference/weakmap-object-javascript.md)|N|N|N|N|T|T|v8: N<br />v8.1: T|  
|[WeakSet, obiekt](../../javascript/reference/weakset-object-javascript.md)|N|N|N|N|N|T|v8.1: N<br />v10: Y|  
|[while, instrukcja](../../javascript/reference/while-statement-javascript.md)|T|T|T|T|T|T|T|  
|[WinRTError, obiekt](../../javascript/reference/winrterror-object-javascript.md)|N|N|N|T|T|T|T|  
|[with, instrukcja](../../javascript/reference/with-statement-javascript.md)|T|T|T|T|T|T|T|  
|[Write — funkcja](../../javascript/reference/debug-write-function-javascript.md)|T|T|T|T|T|T|T|  
|[writeln — funkcja](../../javascript/reference/debug-writeln-function-javascript.md)|T|T|T|T|T|T|T|  
  
 \* Obsługuje obiekty modelu DOM, ale nie zdefiniowany przez użytkownika obiekty. `enumerable` i `configurable` można określić atrybuty, ale nie są one używane.  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie zgodności dokumentów](http://go.microsoft.com/fwlink/?LinkId=208537)