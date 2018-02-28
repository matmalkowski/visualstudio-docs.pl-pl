---
title: "getYear — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
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
- getYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- GetYear method
ms.assetid: 0e23e832-acd4-49a9-a175-515d0094f172
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0e08fae8da1b102918de70650d09080a7ff7ebd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="getyear-method-date-javascript"></a>getYear — Metoda (Data) (JavaScript)
Pobiera roku `Date` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.getYear()   
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `dateObj` odwołanie jest `Date` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca rok.  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
>  Ta metoda jest przestarzała i zapewnia tylko zgodność z poprzednimi wersjami. Użyj `getFullYear` metody zamiast tego.  
  
 W [!INCLUDE[jsv1textspecific](../../javascript/reference/includes/jsv1textspecific-md.md)], a następnie w programie Internet Explorer począwszy [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], wartość zwracana jest przechowywane roku minus 1900 roku. Na przykład roku 1899 jest zwracana wartość-1 i roku 2000 jest zwracana jako 100.  
  
 W [!INCLUDE[jsv3textspecific](../../javascript/reference/includes/jsv3textspecific-md.md)] za pośrednictwem [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)], formuła jest zależna od roku. Lat 1900 do 1999 wartość zwracana jest wartość 2-cyfrowy przechowywanych roku minus 1900. Dat poza ten zakres jest zwracany rok 4 cyfr. Na przykład 1996 jest zwracana jako 96, ale 1825 i 2025 są zwracane jest.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getFullYear — metoda (Data)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear — metoda (Data)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear — metoda (Data)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear — metoda (Data)](../../javascript/reference/setutcfullyear-method-date-javascript.md)   
 [setYear — metoda (Data)](../../javascript/reference/setyear-method-date-javascript.md)