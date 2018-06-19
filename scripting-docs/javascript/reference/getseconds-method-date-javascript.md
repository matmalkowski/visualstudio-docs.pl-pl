---
title: getSeconds — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft
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
- getSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- seconds method
- GetSeconds method
ms.assetid: 97b10674-af0b-4681-a846-38f972196501
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 151d720b92fb9d7068c320983a25b965078f1b2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790543"
---
# <a name="getseconds-method-date-javascript"></a>getSeconds — Metoda (Data) (JavaScript)
Pobiera sekund z `Date` obiekt przy użyciu czasu lokalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.getSeconds()   
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `dateObj` odwołanie jest `Date` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę całkowitą od 0 do 59. Zero jest zwracana w odpowiednim czasie krótszym niż jedna sekunda w ciągu bieżącej minuty. Jeśli `Date` obiekt został utworzony bez określania czasu, wartość sekund domyślna to 0.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać sekund wartość przy użyciu uniwersalnego czasu koordynowanego (UTC), należy użyć `getUTCSeconds` metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `getSeconds` metody.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getSeconds());  
document.write("<br/>");  
  
date.setSeconds(5);  
document.write(date.getSeconds());  
  
// Output:  
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getUTCSeconds — metoda (Data)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds — metoda (Data)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds — metoda (Data)](../../javascript/reference/setutcseconds-method-date-javascript.md)