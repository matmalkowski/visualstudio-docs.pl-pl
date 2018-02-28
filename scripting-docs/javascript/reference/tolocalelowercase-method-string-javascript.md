---
title: "toLocaleLowerCase — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft"
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
- toLocaleLowerCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleLowerCase method
ms.assetid: add894d3-d14a-4dbc-a9b9-7ad1d3a2e581
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 642ced387e0d3b4cf763767ec147d6160ed7d36b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalelowercase-method-string-javascript"></a>toLocaleLowerCase — Metoda (ciąg) (JavaScript)
Konwertuje wszystkie znaki alfabetyczne na małe litery, biorąc pod uwagę bieżące ustawienia regionalne środowisku hosta.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
stringVar.toLocaleLowerCase( )  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `stringVar` odwołanie jest `String` obiektu lub literałem ciągu.  
  
 `toLocaleLowerCase` Metoda konwertuje znaki w ciągu, biorąc pod uwagę bieżące ustawienia regionalne środowisku hosta. W większości przypadków wynik jest taka sama w wyniku `toLowerCase` metody. Wyniki są różne, jeśli konflikt zasad dla języka z regularnych mapowanie przypadków Unicode.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Dotyczy**: [ciągu obiektu](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [toLocaleUpperCase — metoda (ciąg)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [toLowerCase — metoda](../../javascript/reference/tolowercase-method-javascript.md)