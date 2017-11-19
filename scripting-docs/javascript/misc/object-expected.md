---
title: Oczekiwano obiektu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6add25325653627d23eb699ab53c0f2799c8322f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="object-expected"></a>Oczekiwany obiekt
Podjęto próbę wywołania metody lub właściwości w obiekcie typu innego niż `Object`, lub inne niż przekazany argument typu `Object` podczas `Object` była wymagana.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Tylko wywołania metody lub właściwości w obiektach typu `Object`.  
  
-   Jeśli wystąpi błąd argumentu-object, przekaż obiekt typu `Object`.  
  
-   Sprawdź, czy odwołanie Niezdefiniowany ani mieć wartości null jest wprowadzenie wywoływana zamiast typu obiektu `Object`.  
  
     Na przykład, jeśli ten błąd na myVar w następującym kodzie:  
  
    ```JavaScript  
    var str = myVar.toString();  
    ```  
  
     Zamiast tego można użyć tego kodu:  
  
    ```JavaScript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Object — obiekt](../../javascript/reference/object-object-javascript.md)   
 [Obiekty i tablice](../../javascript/objects-and-arrays-javascript.md)