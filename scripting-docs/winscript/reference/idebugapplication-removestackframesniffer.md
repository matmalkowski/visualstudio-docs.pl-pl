---
title: IDebugApplication::RemoveStackFrameSniffer | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplication.RemoveStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::RemoveStackFrameSniffer
ms.assetid: 00304b88-e435-4b87-a331-44e7492eb32d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11289972dbd39d2e6221fb223a0d933ed90589c2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationremovestackframesniffer"></a>IDebugApplication::RemoveStackFrameSniffer
Usuwa dostawcę modułu wyliczającego ramki stosu z tej aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RemoveStackFrameSniffer(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwCookie`  
 [in] Plik cookie zwrócony przez `AddStackFrameSniffer` metody podczas dodawania dostawcy modułu wyliczającego ramki stosu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 `RemoveStackFrameSniffer` Metoda usuwa dostawcę modułu wyliczającego ramki stosu z tej aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)   
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Interfejs IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)