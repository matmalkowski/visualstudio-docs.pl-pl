---
title: "toLocaleUpperCase — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft"
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
- toLocaleUpperCase
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toLocaleUpperCase method
ms.assetid: e927adb6-475e-44b2-91f7-cedda10a39b0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07a89560dde0319598da30fc3451524112b99eac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="tolocaleuppercase-method-string-javascript"></a>toLocaleUpperCase — Metoda (ciąg) (JavaScript)
Zwraca ciąg, gdy wszystkie znaki alfabetyczne zostały przekonwertowane na wielkie litery, biorąc pod uwagę hosta środowiska bieżące ustawienia regionalne.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
stringVar.toLocaleUpperCase( )  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `stringVar` odwołanie jest `String` obiektu lub literałem ciągu.  
  
 `toLocaleUpperCase` Metoda konwertuje znaki w ciągu, biorąc pod uwagę bieżące ustawienia regionalne środowisku hosta. W większości przypadków wynik jest taka sama w wyniku `toUpperCase` metody. Wyniki są różne, jeśli konflikt zasad dla języka z regularnych mapowanie przypadków Unicode.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Dotyczy**: [ciągu obiektu](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [toLocaleLowerCase — metoda (ciąg)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase — metoda (ciąg)](../../javascript/reference/touppercase-method-string-javascript.md)