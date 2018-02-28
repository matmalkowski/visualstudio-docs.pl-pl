---
title: IDebugStackFrameSnifferEx::EnumStackFramesEx | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrameSnifferEx::EnumStackFramesEx
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a96a382c1dce73731fdd4326d8b0d1c35b7aa33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
Zwraca moduł wyliczający ramek stosu dla bieżącego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwSpMin`  
 [in] Dolny limit adresów dla wyliczania ramki stosu.  
  
 `ppedsf`  
 [out] Moduł wyliczający ramek stosu dla bieżącego wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Moduł wyliczający ramki stosu zwraca ramki, począwszy od góry stosu, najbardziej ostatnio wciśnięcia ramki. Moduł wyliczający zawiera tylko ramek stosu adresy większe niż lub równa `dwSpMin`.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugStackFrameSnifferEx](../../winscript/reference/idebugstackframesnifferex-interface.md)