---
title: "setYear — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setYear method
ms.assetid: 36431050-e0ec-45ee-830d-0d7c20e207ea
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a9318de4a9420e0518dcd7f00a51c7161a8f92c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="setyear-method-date-javascript"></a>setYear — Metoda (Data) (JavaScript)
Ustawia wartość roku w `Date` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.setYear(numYear)   
```  
  
## <a name="parameters"></a>Parametry  
 `dateObj`  
 Wymagany. Wszelkie `Date` obiektu.  
  
 `numYear`  
 Wymagany. Lat 1900 do 1999 jest wartość liczbowa równa minus 1900 roku. Dat spoza zakresu to 4-cyfrowego wartość liczbową.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest przestarzała i jest zachowywana na potrzeby poprzednimi wersjami. Użyj `setFullYear` metody zamiast tego.  
  
 Aby ustawić roku `Date` obiektu 1997, wywołanie **setYear(97)**. Aby ustawić roku 2010, należy wywołać **setYear(2010)**. Na koniec roku ustawiono wartość roku z zakresu 0-99, użyj `setFullYear` metody.  
  
> [!NOTE]
>  Aby uzyskać [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] w wersji 1.0 `setYear` używa wartości będące wynikiem dodania 1900 roku wartości dostarczone przez `numYear`, niezależnie od wartości roku. Na przykład, aby ustawić roku 1899 `numYear` wynosi -1 i można ustawić roku 2000 `numYear` to 100.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getFullYear — metoda (Data)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear — metoda (Data)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [getYear — metoda (Data)](../../javascript/reference/getyear-method-date-javascript.md)   
 [setFullYear — metoda (Data)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear — metoda (Data)](../../javascript/reference/setutcfullyear-method-date-javascript.md)