---
title: "setUTCFullYear — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
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
- setUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCFullYear method
- UTC dates, setting
ms.assetid: e6c51b49-0149-4f9a-aa74-c73c0306f98e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dda8b75dd8bc8dac87ea383546f392b064c1d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="setutcfullyear-method-date-javascript"></a>setUTCFullYear — Metoda (Data) (JavaScript)
Ustawia wartość roku w `Date` przy użyciu uniwersalnego czasu koordynowanego (UTC).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.setUTCFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. Wszelkie `Date` obiektu.  
  
 `numYear`  
 Wymagany. Liczbowa wartość równą roku.  
  
 `numMonth`  
 Opcjonalny. Liczbowa wartość równą miesiąca. Wartość w styczniu wynosi 0, a inne wartości miesiąca wykonaj po kolei. Musi być dostarczona, jeśli *numDate* podano.  
  
 *numDate*  
 Opcjonalny. Liczbowa wartość równą dzień miesiąca.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie **ustawić** metody biorąc Argumenty opcjonalne używać wartość zwracana z odpowiadającego **uzyskać** metody, jeśli nie zostanie określony opcjonalny argument. Na przykład jeśli `numMonth` argument nie zostanie określony, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] używa wartość zwracana z `getUTCMonth` metody.  
  
 Ponadto, jeśli wartość argumentu jest większa który jego zakres lub number, inne przechowywanej wartości ujemne są odpowiednio zmienione.  
  
 Aby ustawić rok, używając czasu lokalnego, należy użyć `setFullYear` metody.  
  
 Zakres lat obsługiwane w `Date` obiektu wynosi około 285,616 lat z obu stron rokiem 1970.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `setUTCFullYear` metody.  
  
```JavaScript  
var dtFirst = new Date();  
dtFirst.setUTCFullYear(2007);  
  
var dtSecond = new Date();  
// 10 is the value for November.   
dtSecond.setUTCFullYear(2008, 10, 3);   
  
document.write (dtFirst.toUTCString());  
document.write ("<br />");  
document.write (dtSecond.toUTCString());  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getFullYear — metoda (Data)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear — metoda (Data)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear — metoda (Data)](../../javascript/reference/setfullyear-method-date-javascript.md)