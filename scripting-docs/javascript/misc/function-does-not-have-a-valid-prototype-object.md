---
title: "Funkcja nie zawiera prawidłowego prototypu obiektu | Dokumentacja firmy Microsoft"
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
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4e2cbf198a452cd61f1355682ea3041436d2a27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Funkcja nie zawiera prawidłowego prototypu obiektu
Podjęto próbę użycia **instanceof** ustalenie, jeśli obiekt pochodzi z klasy określonej funkcji, ale można ponownie zdefiniować obiektu `prototype` właściwość jako `null`, lub typ obiektu zewnętrznego (zarówno nieprawidłowy [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiektów). Obiekt zewnętrzny może być obiekt modelu obiektu hosta (na przykład dokument programu Internet Explorer lub obiekt window) lub obiektu COM zewnętrznego.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, funkcja `prototype` właściwość odwołuje się do prawidłowej [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Function — obiekt](../../javascript/reference/function-object-javascript.md)   
 [prototype — właściwość (obiekt)](../../javascript/reference/prototype-property-object-javascript.md)