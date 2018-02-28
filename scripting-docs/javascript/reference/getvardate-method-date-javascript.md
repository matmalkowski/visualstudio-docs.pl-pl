---
title: "getVarDate — metoda (Data) (JavaScript) | Dokumentacja firmy Microsoft"
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
- getVarDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- getVarDate method
- dates, VT_DATE format
ms.assetid: 561238de-5c91-45a3-b839-a16910d3a1cf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d21394a5381653997a6b406537a6bde4f5266b97
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="getvardate-method-date-javascript"></a>getVarDate — Metoda (Data) (JavaScript)
Zwraca wartość VT_DATE z `Date` obiektu.  
  
> [!WARNING]
>  Ta metoda jest obsługiwana tylko w programie Internet Explorer.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dateObj.getVarDate()   
```  
  
#### <a name="parameters"></a>Parametry  
 Wymagane `dateObj` odwołanie jest `Date` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość VT_DATE.  
  
## <a name="remarks"></a>Uwagi  
 `getVarDate` Metoda jest używana, gdy kod JavaScript użyje obiektów COM, obiekty ActiveX lub inne obiekty, które akceptować i zwracać wartości daty w formacie VT_DATE. Obejmują one obiektów w Visual Basic i Visual Basic Scripting Edition (VBScript). Rzeczywiste format zwrócona wartość zależy od ustawień regionalnych.  
  
## <a name="requirements"></a>Wymagania  
 Obsługiwane w następujących trybach dokumentu: Osobliwości, Standardy programu Internet Explorer 6, Standardy programu Internet Explorer 7, Standardy programu Internet Explorer 8, Standardy programu Internet Explorer 9 i standardy programu Internet Explorer 10. Nieobsługiwane w [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji. Zobacz [Informacje o wersji](../../javascript/reference/javascript-version-information.md).  
  
 **Dotyczy**: [obiekt Date](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [getDate — metoda (Data)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Date.Parse — funkcja](../../javascript/reference/date-parse-function-javascript.md)