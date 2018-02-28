---
title: "Błędy składniowe JavaScript | Dokumentacja firmy Microsoft"
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
- JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- errors [JavaScript]
- syntax errors, JavaScript
ms.assetid: 0343dc19-5f5e-4a4c-83da-630b4fbcb3b6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3bc3398d6a90ef308fd2b4b367bc1006ad95f5b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="javascript-syntax-errors"></a>Błędy składniowe JavaScript
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]wystąpiły błędy składniowe gdy struktura jednego z Twojej [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] instrukcje narusza co najmniej jeden składni reguł.  
  
## <a name="errors"></a>błędy  
  
|Numer błędu|Opis|  
|------------------|-----------------|  
|1019|[Nie może mieć break poza pętlą](../../javascript/misc/can-t-have-break-outside-of-loop.md)|  
|1020|[Nie może mieć "continue" poza pętlą](../../javascript/misc/can-t-have-continue-outside-of-loop.md)|  
|1030|[Kompilacja warunkowa jest wyłączona.](../../javascript/misc/conditional-compilation-is-turned-off.md)|  
|1027|["default" może wystąpić tylko raz w instrukcji "switch"](../../javascript/misc/default-can-only-appear-once-in-a-switch-statement.md)|  
|1005|[Oczekiwano "("](../../javascript/misc/expected-left-parenthesis-javascript.md)|  
|1006|[Oczekiwano ")"](../../javascript/misc/expected-right-parenthesis-javascript.md)|  
|1012|[Oczekiwano "/"](../../javascript/misc/expected-minus.md)|  
|1003|[Oczekiwano ":"](../../javascript/misc/expected-colon.md)|  
|1004|[Oczekiwano ";"](../../javascript/misc/expected-semicolon.md)|  
|1032|[Oczekiwano "@"](../../javascript/misc/expected-at.md)|  
|1029|[Oczekiwano "@end"](../../javascript/misc/expected-at-end.md)|  
|1007|[Oczekiwano "&#93;"](../../javascript/misc/expected-right-square-bracket.md)|  
|1008|[Oczekiwano "{"](../../javascript/misc/expected-left-curly-brace.md)|  
|1009|[Oczekiwano "}"](../../javascript/misc/expected-right-curly-brace.md)|  
|1011|[Oczekiwano znaku "="](../../javascript/misc/expected-equal-javascript.md)|  
|1033|[Oczekiwano instrukcji "catch"](../../javascript/misc/expected-catch.md)|  
|1031|[Oczekiwano stałej](../../javascript/misc/expected-constant.md)|  
|1023|[Oczekiwano liczby szestnastkowej](../../javascript/misc/expected-hexadecimal-digit.md)|  
|1010|[Oczekiwano identyfikatora](../../javascript/misc/expected-identifier-javascript.md)|  
|1028|[Oczekiwano identyfikatora, ciągu lub liczby](../../javascript/misc/expected-identifier-string-or-number.md)|  
|1024|[Oczekiwano instrukcji "while"](../../javascript/misc/expected-while.md)|  
|1014|[Nieprawidłowy znak](../../javascript/misc/invalid-character-javascript.md)|  
|1026|[Nie można odnaleźć etykiety](../../javascript/misc/label-not-found.md)|  
|1025|[Etykieta zdefiniowana ponownie](../../javascript/misc/label-redefined.md)|  
|1018|[Instrukcja "return" poza funkcją](../../javascript/misc/return-statement-outside-of-function.md)|  
|1002|[Błąd składni](../../javascript/misc/syntax-error-javascript.md)|  
|1035|[Throw musi występować wyrażenie w tym samym wierszu źródłowym](../../javascript/misc/throw-must-be-followed-by-an-expression-on-the-same-source-line.md)|  
|1016|[Niezakończony komentarz](../../javascript/misc/unterminated-comment.md)|  
|1015|[Niezakończona stała typu string](../../javascript/misc/unterminated-string-constant-javascript.md)|  
  
### <a name="script-host-errors"></a>Błędy hosta skryptów  
 Następujące błędy prawidłowo rozmowy błędy dotyczące hosta skryptów, ale może wyświetlić je od czasu do czasu.  
  
|Błąd|HRESULT|Opis|  
|-----------|-------------|-----------------|  
|SCRIPT_E_RECORDED|0x86664004|Błąd został zarejestrowany do przekazania między aparat skryptu i hostem. Host musi przekazać do obiektu wywołującego kod błędu.|  
|SCRIPT_E_REPORTED|0x80020101|Aparat skryptu zgłosiła nieobsługiwany wyjątek dla hosta za pomocą IActiveScriptSite::OnScriptError. Ten błąd można zignorować hosta.|  
|SCRIPT_E_PROPAGATE|0x8002010|Błąd skryptu jest przekazywana dalej do wywołującego, która może być w innym wątku. Host należy przekazać kod błędu do obiektu wywołującego.|  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy środowiska wykonawczego języka JavaScript](../../javascript/reference/javascript-run-time-errors.md)