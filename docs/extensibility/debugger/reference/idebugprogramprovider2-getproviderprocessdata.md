---
title: IDebugProgramProvider2::GetProviderProcessData | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords: IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ae46cd5e90b4cdd23b0c7fafa147c43805974283
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Pobiera listę uruchomionymi programami od określonego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```csharp  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Flags`  
 [in] Kombinacja flag z [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) wyliczenia. Następujące flagi są typowe dla tego wywołania:  
  
|Flaga|Opis|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|Obiekt wywołujący jest uruchomiona na komputerze zdalnym.|  
|`PFLAG_DEBUGGEE`|Obiekt wywołujący jest obecnie debugowany (dodatkowe informacje na temat kierowania zostanie zwrócony dla każdego węzła).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Dołączony do obiektu wywołującego, ale nie jest uruchomiony przez debuger.|  
|`PFLAG_GET_PROGRAM_NODES`|Obiekt wywołujący pyta o listy węzłów program ma zostać zwrócona.|  
  
 `pPort`  
 [in] Port procesu wywołującego jest uruchomiona na.  
  
 `processId`  
 [in] [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktury zawierający identyfikator procesu, który zawiera program jest zagrożona.  
  
 `EngineFilter`  
 [in] Tablica identyfikatorów GUID aparatów debugowania przypisane do debugowania tego procesu (zostaną one użyte do filtrowania programy, które są rzeczywiście zwracane na podstawie co podane aparaty obsługują; Jeśli nie określono żadnych aparaty, zostaną zwrócone wszystkie programy, a następnie).  
  
 `pProcess`  
 [out] A [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) struktury, która jest wypełniane żądane informacje.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest zazwyczaj wywoływana przez proces, aby uzyskać listę programów uruchomionych w tym procesie. Zwracane informacje znajduje się lista [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) obiektów.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)