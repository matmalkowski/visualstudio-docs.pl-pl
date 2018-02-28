---
title: "Identyfikator URI, który ma być zdekodowany, zawiera nieprawidłowy znak | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e93d145ea6b0991123c2a7c80f8acf54a83a264
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Identyfikator URI, który ma być zdekodowany, zawiera nieprawidłowy znak.
Podjęto próbę zakodować ciąg jako identyfikatora URI (Uniform Resource Identifier), ale zawiera nieprawidłowe znaki. Mimo że większość znaków są prawidłowe w ciągów, które ma zostać przekonwertowane na identyfikatory URI, niektóre sekwencje znaków Unicode są niedozwolone.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że ciąg do zakodowania zawiera tylko prawidłowe sekwencje Unicode. Pełny identyfikator URI składa się z sekwencji składników i separatorów. Nazwy w nawiasach ostrych reprezentują składników i ":", "/", ";" i "?" są zastrzeżone znaki używane jako separatorów. Ogólny kształt jest:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [encodeURI — funkcja](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeuricomponent — funkcja](../../javascript/reference/encodeuricomponent-function-javascript.md)