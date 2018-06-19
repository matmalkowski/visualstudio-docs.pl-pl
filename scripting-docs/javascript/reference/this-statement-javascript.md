---
title: Ta instrukcja (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- this_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- this statement
- constructors, referring to current object
ms.assetid: 8510a00b-2f14-4700-a276-4d9a523c5112
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4afed1bd978d1985c151efa77873c93e699f0b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791605"
---
# <a name="this-statement-javascript"></a>this — Instrukcja (JavaScript)
Odnosi się do bieżącego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
this.property  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `property` argument jest jedna z właściwości bieżącego obiektu  
  
 `this` w konstruktorów obiektów można użyć słowa kluczowego do odwoływania się do bieżącego obiektu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie **to** odwołuje się do nowo utworzony obiekt Car i przypisuje wartości trzy właściwości:  
  
```JavaScript  
function Car(color, make, model){  
   this.color = color;  
   this.make = make;  
   this.model = model;  
}  
```  
  
 **To** — słowo kluczowe odnosi się zazwyczaj do **okna** obiektu, jeśli używana poza zakresem innego obiektu. Jednak wewnątrz obsługi zdarzeń `this` odwołuje się do elementu modelu DOM, który wywołał zdarzenie.  
  
 W poniższym kodzie (dla programu Internet Explorer 9 lub nowszego) program obsługi zdarzeń drukuje wersję ciągu przycisku, który ma identyfikator „clicker” (ten, który kliknął).  
  
```JavaScript  
document.getElementById("clicker").addEventListener("click", eventHandler, false);  
  
        function eventHandler(ev) {  
            document.write(this.toString());  
        }  
  
// Output (when you click the button): [object HTMLButtonElement]  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [New — Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Używanie metody bind](../../javascript/advanced/using-the-bind-method-javascript.md)