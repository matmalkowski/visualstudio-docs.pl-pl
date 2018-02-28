---
title: "@cc_on— Instrukcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@cc_on_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, activating
- '@cc_on statement'
- '@set statement'
- '@if statement'
ms.assetid: fdeda7ee-b9f4-4e52-8aa2-21c90c02a332
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e993d5bc8302931a5722495da70612e79f7dfd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ccon-statement-javascript"></a>@cc_on— Instrukcja (JavaScript)
Aktywuje obsługę kompilacji warunkowej w ramach komentarzy w skrypcie.  
  
> [!WARNING]
>  Kompilacja warunkowa nie jest obsługiwane w trybie standardów programu Internet Explorer 11 i [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji. Kompilacja warunkowa nie jest obsługiwana w trybie standardów programu Internet Explorer 10 i wszystkich wcześniejszych wersjach.  
  
## <a name="syntax"></a>Składnia  
  
```  
@cc_on   
```  
  
## <a name="remarks"></a>Uwagi  
 `@cc_on` Instrukcji aktywuje kompilacja warunkowa w komentarzy w skrypcie.  
  
 Korzystanie ze zmiennych kompilacji warunkowej w skryptach napisanych dla stron ASP lub ASP.NET lub programów wiersza polecenia nie jest powszechne, ponieważ możliwości kompilatorów można określić przy użyciu innych metod.  
  
 Podczas pisania skryptu dla strony sieci Web, kod kompilacji warunkowej zawsze umieszczaj w komentarzach. Dzięki temu hosty, które nie obsługują kompilacji warunkowej, mogą ją ignorować.  
  
 Zdecydowanie zaleca się, że używasz `@cc_on` instrukcji w komentarzu, tak aby przeglądarek, które nie obsługują kompilacja warunkowa będzie akceptować skrypt jako prawidłowej składni:  
  
 `@if` Lub `@set` instrukcję poza komentarz zostanie aktywowany kompilacji warunkowej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `@cc_on` instrukcji.  
  
```JavaScript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on the 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on the 16-bit version of Windows.");  
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
 [@if— Instrukcja](../../javascript/reference/at-if-statement-javascript.md)   
 [@set— Instrukcja](../../javascript/reference/at-set-statement-javascript.md)