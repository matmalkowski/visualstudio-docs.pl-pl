---
title: IBindEventHandler::BindHandler | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IBindEventHandler.BindHandler
apilocation: scrobj.dll
helpviewer_keywords: IBindEventHandler::BindHandler
ms.assetid: 87909828-2224-4bb1-a6c9-dfe715ac4c9b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66de7cba8181ce9f3d683a90e4d7dd51e63d4779
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ibindeventhandlerbindhandler"></a>IBindEventHandler::BindHandler
Wiąże zdarzenia obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT BindHandler(  
   LPCOLESTR   pstrEvent,  
   IDispatch*  pdisp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrEvent`  
 [in] Określa zdarzenia w celu obsługi.  
  
 `pdisp`  
 [in] Określa obiekt do obsługi zdarzenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wiąże zdarzenia obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IBindEventHandler](../../winscript/reference/ibindeventhandler-interface.md)