---
title: "toLocaleString — metoda (obiekt) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLocaleString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLocaleString method
ms.assetid: 0901afcb-126b-4ed7-bd6a-2301d50e2326
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f88e1c702cd8a7d702630ae90ef840c4af88f30
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalestring-method-object-javascript"></a>toLocaleString — Metoda (Obiekt) (JavaScript)
Zwraca wartość typu date konwertowana na ciąg przy użyciu bieżących ustawień regionalnych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.toLocaleString()   
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `dateObj` dowolnego `Date` obiektu.  
  
 `toLocaleString` Metoda zwraca `String` obiekt, który zawiera napisana bieżące ustawienia regionalne długi domyślny format daty.  
  
-   Dat między 1601 i 1999 r. N.E. Data jest sformatowany zgodnie z jego ustawienia regionalne Panelu sterowania.  
  
-   Dla dat poza tym zakresem domyślny format **toString** metoda jest używana.  
  
 Na przykład w Stanach Zjednoczonych `toLocaleString` zwraca "96-01/05 00:00:00" dla stycznia 5. W Europie, zwraca "96-05/01 00:00:00" dla tego samego dnia, co Europejskich Konwencji umieszcza dzień przed miesiąca.  
  
> [!NOTE]
>  `toLocaleString`należy używać tylko do wyświetlania wyników dla użytkownika; nigdy nie można stosować jako podstawy do obliczeń w skrypcie zwrócony wynik jest specyficzne dla maszyny.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `toLocaleString` metody.  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt Array](../../javascript/reference/array-object-javascript.md)&#124; [Data obiektu](../../javascript/reference/date-object-javascript.md)&#124; [Number obiektu](../../javascript/reference/number-object-javascript.md)&#124; [Obiekt obiektu](../../javascript/reference/object-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [toLocaleDateString — metoda (Data)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)