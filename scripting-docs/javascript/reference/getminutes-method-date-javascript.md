---
title: getMinutes — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft
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
- getMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetMinutes method
- minutes method
ms.assetid: d4139b5d-04e1-474c-9a83-e9d40597243a
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff08fd84345c9ceb816444a1b44643a8353b60b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790540"
---
# <a name="getminutes-method-date-javascript"></a>getMinutes — Metoda (Data) (JavaScript)
Pobiera notatki z `Date` obiekt przy użyciu czasu lokalnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.getMinutes()   
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `dateObj` odwołanie jest `Date` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę całkowitą od 0 do 59. Zero jest zwracany czas jest mniej niż minutę godziny. Jeśli `Date` obiekt został utworzony bez określania czasu, domyślnie minuty wartość wynosi 0.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać wartość minut przy użyciu uniwersalnego czasu koordynowanego (UTC), należy użyć `getUTCMinutes` metody.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono sposób `getMinutes` metody.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getMinutes());  
  
// Output:  
// 0  
// 5  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getUTCMinutes — metoda (Data)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes — metoda (Data)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes — metoda (Data)](../../javascript/reference/setutcminutes-method-date-javascript.md)