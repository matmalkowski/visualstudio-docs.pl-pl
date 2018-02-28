---
title: "Operator warunkowy (trójargumentowy) (?:) (JavaScript) | Dokumentacja firmy Microsoft"
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
- '?:'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional operators
- conditional (Ternary) operator
- ternary
ms.assetid: 7399ac32-9324-4a9a-ae76-be9c0f9df81c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dc34b5c633cfc02219cb01061e1aaa017e0f7f2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-ternary-operator--javascript"></a>Operator warunkowy (trójargumentowy) (?:) (JavaScript)
Zwraca jedno z dwóch wyrażeń w zależności od warunku.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
test ? expression1 : expression2  
```  
  
## <a name="parameters"></a>Parametry  
 `test`  
 Dowolne wyrażenie logiczne.  
  
 `expression1`  
 Wyrażenie if zwrócony `test` jest `true`. Może być wyrażeniem przecinkowym.  
  
 `expression2`  
 Wyrażenie if zwrócony `test` jest `false`. Więcej niż jedno wyrażenie może być połączone wyrażeniem przecinkowym.  
  
## <a name="remarks"></a>Uwagi  
 `?:` Operator może być używany jako skrót do `if...else` instrukcji. Zwykle jest używana jako część większego wyrażenia gdzie `if...else` instrukcja może być nieodpowiednich. Na przykład:  
  
```JavaScript  
var now = new Date();  
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");  
```  
  
 W przykładzie jest tworzony ciąg zawierający "Dobry wieczór." Jeśli po 18: 00. Odpowiednik kodu za pomocą `if...else` instrukcji będzie wyglądać następująco:  
  
```JavaScript  
var now = new Date();  
var greeting = "Good";  
if (now.getHours() > 17)  
   greeting += " evening.";  
else  
   greeting += " day.";  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IF... else — instrukcja](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)   
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)   
 [Skrypt ScriptJunkie Konfiguracja elementu widget przykładowej aplikacji](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)