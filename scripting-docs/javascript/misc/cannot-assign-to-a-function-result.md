---
title: Nie można przypisać do wyniku funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7e7ea718aa97ab7b2eb0924458826cd1eac5672
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788722"
---
# <a name="cannot-assign-to-a-function-result"></a>Nie można przypisać do wyniku funkcji
Próbujesz przypisać wartości do wyniku funkcji. Wynik funkcji można przypisać do zmiennej, ale nie można użyć jako zmiennej. Jeśli chcesz przypisać nową wartość do samej funkcji, należy pominąć nawiasów (operator wywołania funkcji). W poniższym przykładzie pokazano sytuację, w którym ten błąd jest generowany.  
  
```  
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Nie używaj wartości wyników wywołania funkcji jako możesz *przypisać*. Można przypisać wynik wywołania funkcji *do zmiennej* chociaż.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
-   Alternatywnie można przypisać funkcji się (i nie jego wartość zwrotna) do zmiennej.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Function — obiekt](../../javascript/reference/function-object-javascript.md)   
 [Pisanie kodu JavaScript](../../javascript/writing-javascript-code.md)   
 [Funkcje](../../javascript/functions-javascript.md)