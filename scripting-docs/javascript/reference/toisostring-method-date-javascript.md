---
title: "toISOString — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toISOString method [JavaScript]
ms.assetid: 58577d8f-3ae8-4887-8687-26233ea79ff6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31559e1bc44849573ec7dc903411ce98b0a4440d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="toisostring-method-date-javascript"></a>toISOString — Metoda (Data) (JavaScript)
Zwraca daty w postaci wartości ciągu w formacie ISO.  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
  
objDate.toISOString()  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Reprezentacja ciągu daty w formacie Międzynarodowej Organizacji Normalizacyjnej (ISO) format.  
  
## <a name="exceptions"></a>Wyjątki  
 Jeśli `objDate` nie zawiera prawidłowej daty, `RangeError` wyjątku.  
  
## <a name="remarks"></a>Uwagi  
 ISO format jest uproszczenie w formacie ISO 8601. Aby uzyskać więcej informacji, zobacz [ciągów daty i godziny](../../javascript/date-and-time-strings-javascript.md).  
  
 Strefa czasowa jest zawsze UTC przedstawiany Z sufiksem w danych wyjściowych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `toISOString` metody.  
  
```JavaScript  
var dt = new Date("30 July 2010 15:05 UTC");  
document.write(dt.toISOString());  
document.write("<br />");  
document.write(dt.toUTCString());  
  
// Output:  
//  2010-07-30T15:05:00.000Z  
//  Fri, 30 Jul 2010 15:05:00 UTC  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Date — obiekt](../../javascript/reference/date-object-javascript.md)   
 [Ciągi daty i godziny](../../javascript/date-and-time-strings-javascript.md)