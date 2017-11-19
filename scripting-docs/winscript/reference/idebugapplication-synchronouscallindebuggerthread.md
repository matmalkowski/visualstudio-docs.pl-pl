---
title: IDebugApplication::SynchronousCallInDebuggerThread | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.SynchronousCallInDebuggerThread
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::SynchronousCallInDebuggerThread
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7b66b0b085c0fe3abbee3c3b8c5c3f7d252d3b5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Udostępnia mechanizm dla obiekt wywołujący, aby uruchomić kod w wątku debugera.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pptc`  
 [in] Obiekt do wywołania.  
  
 `dwParam1`  
 [in] Pierwszy parametr do przekazania do `IDebugThreadCall::ThreadCallHandler` metody.  
  
 `dwParam2`  
 [in] Drugi parametr do przekazania do `IDebugThreadCall::ThreadCallHandler` metody.  
  
 `dwParam3`  
 [in] Trzeci parametr do przekazania do `IDebugThreadCall::ThreadCallHandler` metody.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Aparaty języka i hosty zwykle ta metoda umożliwia zaimplementować obiekty bezwątkowe na ich pojedynczego implementacje wątków.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Interfejs IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)