---
title: getMilliseconds — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft
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
- getMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- getMilliseconds method
ms.assetid: 1b512146-1e8a-44a4-89da-6cc5338d15cb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33e5fc54dffbe06e47f0978e6cef94b1f650c90f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790492"
---
# <a name="getmilliseconds-method-date-javascript"></a>getMilliseconds — Metoda (Data) (JavaScript)
Pobiera milisekund daty przy użyciu czasu lokalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.getMilliseconds()   
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `dateObj` odwołanie jest `Date` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca daty w milisekundach. Wartość może należeć do zakresu od 0 do 999. Jeśli datę zostały utworzone na bez określania MS, wartość zwracana jest wartość 0.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać wyrażony w milisekundach czas uniwersalny czas koordynowany (UTC), należy użyć `getUTCMilliseconds` metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **getMilliseconds** metody.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(5);  
document.write(date.getMilliseconds());  
// Output:   
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getUTCMilliseconds — metoda (Data)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setMilliseconds — metoda (Data)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds — metoda (Data)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)