---
title: "valueOf — metoda (obiekt) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: valueOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: valueOf method
ms.assetid: c555e38b-f451-4341-8fcd-4c8b02906a2c
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 677b56fd6fc142ce175b130d2f83291c1ac9535f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-object-javascript"></a>valueOf — Metoda (Obiekt) (JavaScript)
Zwraca wartość pierwotnych określonego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
object.valueOf( )  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `object` odwołanie jest wewnętrznych any [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiektu.  
  
 `valueOf` Metody jest określony inaczej dla każdego wewnętrzne [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiektu.  
  
|Obiekt|Wartość zwracana|  
|------------|------------------|  
|Tablica|Zwraca wystąpienie tablicy.|  
|Boolean|Wartość logiczna.|  
|Data|Wartość czasu przechowywanych w milisekundach od północy, 1 stycznia 1970 UTC.|  
|Funkcja|Ta funkcja.|  
|Wartość liczbowa|Wartość liczbowa.|  
|Obiekt|Sam obiekt. Domyślnie włączone.|  
|String|Wartość ciągu.|  
  
 **Matematyczne** i `Error` obiekty nie mają `valueOf` metody.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **Dotyczy**: [obiekt Array](../../javascript/reference/array-object-javascript.md)&#124; [Boolean — obiekt](../../javascript/reference/boolean-object-javascript.md)&#124; [Data obiektu](../../javascript/reference/date-object-javascript.md)&#124; [Funkcji obiektu](../../javascript/reference/function-object-javascript.md)&#124; [Number obiektu](../../javascript/reference/number-object-javascript.md)&#124; [Obiekt obiektu](../../javascript/reference/object-object-javascript.md)&#124; [Ciągu obiektu](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [toString — metoda (obiekt)](../../javascript/reference/tostring-method-object-javascript.md)