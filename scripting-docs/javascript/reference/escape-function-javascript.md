---
title: "Escape — funkcja (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: escape
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- encoding string objects
- Escape method
- hexadecimal
- String object, encoding
ms.assetid: caa92bea-ba69-4109-a68a-6e2debda463a
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b53a447ae6dde917c12a4711d9038136dc4500cf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="escape-function-javascript"></a>escape — Funkcja (JavaScript)
Koduje ciągi, więc może zostać odczytany na wszystkich komputerach. Przestarzałe.  
  
## <a name="syntax"></a>Składnia  
  
```  
escape(charString)   
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `charString` argument jest dowolne `String` obiektu ani literał do zakodowania.  
  
 **Escape** funkcja zwraca wartość ciągu (w formacie Unicode), który zawiera zawartość `charstring`. Wszystkie spacje i znaki interpunkcyjne, akcentowanie znaków, a inne znaki spoza zestawu ASCII są zastępowane `%` *xx* kodowania, gdzie *xx* jest odpowiednikiem szesnastkowe liczbę reprezentującą znak. Na przykład miejsca są zwracane w postaci "% 20".  
  
 Znaki o wartości większej niż 255 są przechowywane przy użyciu **%u** *xxxx* format.  
  
> [!NOTE]
>  **Escape** funkcja nie powinien być używany do kodowania identyfikatory URI (Uniform Resource). Użyj `encodeURI` i `encodeURIComponent` zamiast tego funkcje.  
  
 **Dotyczy**: [obiekt globalny](../../javascript/reference/global-object-javascript.md)  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [encodeURI — funkcja](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeuricomponent — funkcja](../../javascript/reference/encodeuricomponent-function-javascript.md)   
 [String — obiekt](../../javascript/reference/string-object-javascript.md)   
 [unescape — funkcja](../../javascript/reference/unescape-function-javascript.md)