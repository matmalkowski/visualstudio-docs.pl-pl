---
title: "REPEAT — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: fe02cdfd-f0f6-45a2-ad36-31c4300ef142
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1a3d6edce877a97b0e46a69c43b667231c26981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="repeat-method-string-javascript"></a>repeat (String) — metoda (JavaScript)
Zwraca obiekt ciągu o wartości równej oryginalnego ciągu powtórzone określoną liczbę razy.  
  
## <a name="syntax"></a>Składnia  
  
```  
stringObj.repeat(count);  
```  
  
#### <a name="parameters"></a>Parametry  
 `stringObj`  
 Wymagany. Z obiektem ciągu.  
  
 `count`  
 Wymagany. Liczba powtórzeń oryginalnej ciąg w zwracany ciąg.  
  
## <a name="exceptions"></a>Wyjątki  
 Ta metoda zgłasza wyjątek RangeError tylko wtedy, gdy argument jest ujemny lub + nieskończoności.  
  
## <a name="remarks"></a>Uwagi  
 `repeat` Metody łączy oryginalny ciąg do nowego ciągu liczba określona przez `count`.  
  
 Ta metoda zgłasza błąd, jeśli `count` nie jest liczbą dodatnią mniej niż `Infinity`.  
  
## <a name="example"></a>Przykład  
  
```JavaScript  
"abc".repeat(3); // Returns "abcabcabc"  
"abc".repeat(0); // Returns an empty string.  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]