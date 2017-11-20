---
title: "@if— Instrukcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '@if_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- elif statement
- conditional statements, if
- if statement, @if
- else statement
- '@if statement'
ms.assetid: ff11b29d-c06a-4276-b11d-db73e2da98ac
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87cfc157ab16b183ccf687fa221393be4ab74757
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="if-statement-javascript"></a>@if— Instrukcja (JavaScript)
Warunkowo wykonuje grupy poleceń w zależności od wartości wyrażenia.  
  
> [!WARNING]
>  Kompilacja warunkowa nie jest obsługiwane w trybie standardów programu Internet Explorer 11 i [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji. Kompilacja warunkowa nie jest obsługiwana w trybie standardów programu Internet Explorer 10 i wszystkich wcześniejszych wersjach.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      @if (  
   condition1  
)  
   text1  
[@elif (  
   condition2  
)  
   text2]  
[@else  
   text3]  
@end   
```  
  
## <a name="parameters"></a>Parametry  
 *condition1, condition2*  
 Opcjonalny. Wyrażenie, które może być przekształcone na wyrażenie logiczne.  
  
 `text1`  
 Opcjonalny. Tekst, który ma być analizowane `condition1` jest **true**.  
  
 `text2`  
 Opcjonalny. Tekst, który ma być analizowane `condition1` jest **false** i `condition2` jest **true**.  
  
 `text3`  
 Opcjonalny. Tekst, który ma zostać przeanalizowany, jeśli obie `condition1` i `condition2` są **false**.  
  
## <a name="remarks"></a>Uwagi  
 Podczas zapisu `@if` instrukcji, nie trzeba umieścić klauzuli każdego w osobnym wierszu. Można użyć wielu  **@elif**  klauzul. Jednak wszystkie  **@elif**  klauzule musi występować przed  **@else**  klauzuli.  
  
 `@if` Instrukcja jest zwykle używane do ustalenia między kilka opcji tekst, który powinien być używany dla tekstu w danych wyjściowych.  
  
 Korzystanie ze zmiennych kompilacji warunkowej w skryptach napisanych dla stron ASP lub ASP.NET lub programów wiersza polecenia nie jest powszechne. Powodem jest to, że można określić możliwości kompilatorów przy użyciu innych metod.  
  
 Podczas pisania skryptu dla strony sieci Web, kod kompilacji warunkowej zawsze dodawaj w komentarzach. Dzięki temu hosty, które nie obsługują kompilacji warunkowej, mogą ją ignorować.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie  **@if...@elif... @else... @end**  instrukcji.  
  
```JavaScript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on a 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on a 16-bit version of Windows.");  
    @else  
        document.write("Running on a different operating system.");  
    @end  
@*/  
```  
  
## <a name="requirements"></a>Wymagania  
 Obsługiwane we wszystkich wersjach programu Internet Explorer, ale nie w [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilacja warunkowa](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Zmienne kompilacji warunkowej](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on— Instrukcja](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@set— Instrukcja](../../javascript/reference/at-set-statement-javascript.md)