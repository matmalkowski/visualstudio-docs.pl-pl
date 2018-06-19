---
title: toTimeString — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft
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
- toTimeString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toTimeString method
ms.assetid: a4a8c0f2-55a9-4e84-94c3-f0a547fb04b5
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d9af1f688fee0c066158d8504e00f22af9b3a21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791530"
---
# <a name="totimestring-method-date-javascript"></a>toTimeString — Metoda (Data) (JavaScript)
Zwraca godzinę jako wartość ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
objDate. toTimeString( )  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `objDate` odwołanie jest `Date` obiektu.  
  
 `toTimeString` Metoda zwraca ciąg zawierający wartość godziny w bieżącej strefy czasowej.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie czasu ma ustawioną 2000 milisekund po północy 1 stycznia 1970 UTC, a następnie jest on zapisywany.  
  
```JavaScript  
var aDate = new Date();  
     aDate.setTime(2000);  
     document.write(aDate.toTimeString());  
  
// Output depends on the time in the current time zone.  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [toDateString — metoda (Data)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString — metoda (Data)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)