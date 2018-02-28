---
title: "@set— Instrukcja (JavaScript) | Dokumentacja firmy Microsoft"
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
- '@set_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '@set statement'
- conditional compilation, variables
ms.assetid: 36f15926-3e69-422d-82a2-d186dc088203
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10f74a1d57a61d78897b660812a6fd8078244b6b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="set-statement-javascript"></a>@set— Instrukcja (JavaScript)
Tworzy zmienne używane w instrukcjach kompilacji warunkowej.  
  
> [!WARNING]
>  Kompilacja warunkowa nie jest obsługiwane w trybie standardów programu Internet Explorer 11 i [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji. Kompilacja warunkowa nie jest obsługiwana w trybie standardów programu Internet Explorer 10 i wszystkich wcześniejszych wersjach.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
@set @varname = term   
```  
  
## <a name="parameters"></a>Parametry  
 *nazwa_zmiennej*  
 Wymagany. Nieprawidłowa [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] nazwy zmiennej. Musi być zawsze poprzedzona znakiem „@”.  
  
 `term`  
 Wymagany. Zero lub więcej operatorów jednoargumentowych, które poprzedzają stałą, zmienną warunkowej kompilacji lub wyrażenie ujęte w nawiasy.  
  
## <a name="remarks"></a>Uwagi  
 Zmienne liczbowe i logiczne są obsługiwane w kompilacji warunkowej. Ciągi nie są. Zmienne utworzone za pomocą `@set` są zazwyczaj używane w instrukcji warunkowej kompilacji, ale można używać w dowolnym miejscu [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kodu.  
  
 Przykłady deklaracji zmiennych:  
  
```JavaScript  
  
      @set @myvar1 = 12  
  
@set @myvar2 = (@myvar1 * 20)  
  
@set @myvar3 = @_jscript_version  
```  
  
 Następujące operatory są obsługiwane przez w wyrażeniach ujętych w nawiasy:  
  
-   `! ~`  
  
-   `* / %`  
  
-   `+ -`  
  
-   `<< >> >>>`  
  
-   `< <= > >=`  
  
-   `== != === !==`  
  
-   `& ^ |`  
  
-   `&& | |`  
  
 Jeśli zmienna jest używana, zanim została ona zdefiniowana, jego wartość wynosi `NaN`. `NaN`można sprawdzić za pomocą `@if` instrukcji:  
  
```JavaScript  
@if (@newVar != @newVar)  
   ...  
```  
  
 To działa, ponieważ `NaN` to jedyna wartość nie jest równy sobie samemu.  
  
## <a name="requirements"></a>Wymagania  
 Obsługiwane we wszystkich wersjach programu Internet Explorer, ale nie w [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilacja warunkowa](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Zmienne kompilacji warunkowej](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on— Instrukcja](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if— Instrukcja](../../javascript/reference/at-if-statement-javascript.md)