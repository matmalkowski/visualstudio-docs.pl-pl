---
title: IPerPropertyBrowsing2::GetDisplayString | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IPerPropertyBrowsing2.GetDisplayString
apilocation: scrobj.dll
helpviewer_keywords: IPerPropertyBrowsing2::GetDisplayString
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be6f665d1f63966b3828868f4fb8fbf1cae002e9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
Pobiera ciąg, aby wyświetlić typy, które nie są z założenia widoczny zwracanym tekście jest nazwą właściwości opisujące i mogą być wyświetlane w interfejsie użytkownika wywołującego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dispid`  
 [in] Wyślij identyfikator właściwości, których nazwa wyświetlana jest wymagane.  
  
 `pBstr`  
 [out] Wskaźnik do `BSTR` zawierający nazwę wyświetlaną dla właściwości określonej przez `dispID`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłową `HRESULT`, zwykle `S_OK`.  
  
## <a name="remarks"></a>Uwagi  
 Zwracany ciąg nie jest dozwoloną wartością właściwości. Jest po prostu Wyświetl ciąg właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IPerPropertyBrowsing2 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)