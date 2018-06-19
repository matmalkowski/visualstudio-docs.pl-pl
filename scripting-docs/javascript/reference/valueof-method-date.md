---
title: valueOf — metoda (Data) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 39a1f96e-14b0-4db2-b53d-cdfd67cbb208
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87c5e6ea3c3e28d866f7cabf92dc97b81703b5b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791647"
---
# <a name="valueof-method-date"></a>valueOf — Metoda (Data)
Zwraca wartość czasu przechowywanych w milisekundach od północy, 1 stycznia 1970 UTC.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
date.valueOf()  
```  
  
#### <a name="parameters"></a>Parametry  
 `date` Obiekt jest wystąpienie typu Date.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość czasu przechowywanych w milisekundach od północy, 1 stycznia 1970 UTC. Jest to taką samą wartość jak `getTime`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `valueOf` metody z datą.  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
if (myDate.getTime() == myDate.valueOf())  
    document.write("values are the same");  
else  
    document.write("values are different");  
  
// Output: values are the same  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]