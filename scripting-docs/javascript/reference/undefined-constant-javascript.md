---
title: "Niezdefiniowana stała (JavaScript) | Dokumentacja firmy Microsoft"
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
- undefined
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- undefined property
ms.assetid: 2a689d7d-00b0-48fb-9c95-5c2867bde006
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ba7fa8b160e4f5d954c8d6545da5fae41c2f74b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="undefined-constant-javascript"></a>undefined — Stała (JavaScript)
Wartość, która nie została zdefiniowana, takie jak zmienna, która nie została zainicjowana.  
  
## <a name="syntax"></a>Składnia  
  
```  
undefined  
```  
  
## <a name="remarks"></a>Uwagi  
 `undefined` Stałej jest elementem członkowskim `Global` obiektu i stanie się dostępny po zainicjowaniu aparatu skryptów. Gdy zmienna została zadeklarowana, ale nie zainicjowano, jego wartość wynosi **Niezdefiniowany**.  
  
 Jeśli nie została zadeklarowana zmienna, nie można porównać jego `undefined`, ale można porównać typu zmienną do ciągu "undefined".  
  
 `undefined` Stałej jest przydatne, gdy jawnie testowania lub ustawienie zmiennej niezdefiniowany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `undefined` stałej.  
  
```JavaScript  
// A variable that has not been initialized.  
var declared;  
  
if (declared == undefined)  
    document.write("declared has not been given a value <br/>");  
else  
    document.write("declared has been given a value <br/>");  
  
document.write("typeof declared is " + typeof(declared) + "<br/>");  
  
// An undeclared variable cannot be compared to undefined,  
// so the next line would generate an error.  
// if (notDeclared == undefined);  
  
document.write("typeof notDeclared is " + typeof(notDeclared));  
  
// Output:  
// declared has not been given a value  
// typeof declared is undefined  
// typeof notDeclared is undefined  
```  
  
## <a name="requirements"></a>Wymagania  
 `undefined` Właściwość wprowadzono w [!INCLUDE[jsv55text](../../javascript/reference/includes/jsv55text-md.md)], a została wprowadzona tylko do odczytu w [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)].  
  
 **Dotyczy**: [obiekt globalny](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [TypeOf — Operator](../../javascript/reference/typeof-operator-decrementjavascript.md)