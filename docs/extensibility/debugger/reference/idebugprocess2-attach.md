---
title: IDebugProcess2::Attach | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::Attach
helpviewer_keywords: IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 47b14c3de6b5b9980e2ad420596a1243e84c8882
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Dołącza Menedżera debugowania sesji (SDM) do procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) obiekt, który służy do debugowania powiadomienie o zdarzeniu.  
  
 `rgguidSpecificEngines`  
 [in] Tablica identyfikatory GUID aparatami debugowania ma być używany do debugowania programom działającym w procesie. Ten parametr może być wartością null. Aby uzyskać więcej informacji, zobacz uwagi.  
  
 `celtSpecificEngines`  
 [in] Liczba debugowania silników w `rgguidSpecificEngines` tablicy i rozmiar `rghrEngineAttach` tablicy.  
  
 `rghrEngineAttach`  
 [w, out] Tablica kody HRESULT zwrócony przez aparaty debugowania. Rozmiar tej tablicy jest określona w `celtSpecificEngines` parametru. Każdy kod jest zwykle `S_OK` lub `S_ATTACH_DEFERRED`. Drugie wskazuje, że DE jest obecnie dołączony do żadnych programów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. W poniższej tabeli przedstawiono innych możliwych wartości.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Określony proces jest już dołączony do debugera.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Wystąpiło naruszenie zabezpieczeń podczas wykonywania procedury attach.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Proces pulpitu nie można dołączyć debugera.|  
  
## <a name="remarks"></a>Uwagi  
 Dołączanie do procesu dołącza SDM do wszystkich programów uruchomionych w ten proces, który może być debugowany przez aparaty debugowania (DE) określona w `rgguidSpecificEngines` tablicy. Ustaw `rgguidSpecificEngines` parametru z wartością null wartość lub zawierać `GUID_NULL` w tablicy, tak aby dołączyć wszystkie programy w procesie.  
  
 Wszystkie zdarzenia debugowania, które występują w procesie są wysyłane do danego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) obiektu. To `IDebugEventCallback2` obiektu jest udostępniane po SDM wywołuje tę metodę.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)