---
title: Nieprawidłowy argument zastępczy | Dokumentacja firmy Microsoft
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
- VS.WebClient.Help.SCRIPT5035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 588909bae9c5cf198d3108490111b36d5a2d182b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788683"
---
# <a name="invalid-replacer-argument"></a>Nieprawidłowy argument zastępczy
Została podjęta próba wywołania `JSON.stringify` z argumentem, który jest nieprawidłowy. `replacer` Argument musi być funkcją lub tablicy.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zmień `replacer` argumentu dla funkcji lub tablicy.  
  
## <a name="example"></a>Przykład  
 Kod w tym przykładzie powoduje błąd w czasie wykonywania, ponieważ `memberfilter` jest obiektem zamiast funkcji lub tablicy.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt JSON](../../javascript/reference/json-object-javascript.md)   
 [JSON.Parse — funkcja](../../javascript/reference/json-parse-function-javascript.md)   
 [Błędy środowiska wykonawczego języka JavaScript](../../javascript/reference/javascript-run-time-errors.md)