---
title: IDebugProgramProvider2::WatchForProviderEvents | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramProvider2::WatchForProviderEvents
helpviewer_keywords:
- IDebugProgramProvider2::WatchForProviderEvents
ms.assetid: 2eb93653-b5fb-45b6-b136-56008c5d25ef
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 096de389b7e62f70f8aad275e4fe098b399ee615
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramprovider2watchforproviderevents"></a>IDebugProgramProvider2::WatchForProviderEvents
Umożliwia procesu ma być powiadamiany o zdarzeniach portu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT WatchForProviderEvents(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   CONST_GUID_ARRAY     EngineFilter,  
   REFGUID              guidLaunchingEngine,  
   IDebugPortNotify2*   pEventCallback  
);  
```  
  
```csharp  
int WatchForProviderEvents(  
   enum_PROVIDER_FLAGS   Flags,  
   IDebugDefaultPort2    pPort,  
   AD_PROCESS_ID         ProcessId,  
   CONST_GUID_ARRAY      EngineFilter,  
   ref Guid              guidLaunchingEngine,  
   IDebugPortNotify2     pEventCallback  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Flags`  
 [in] Kombinacja flag z [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) wyliczenia. Następujące flagi są typowe dla tego wywołania:  
  
|Flaga|Opis|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|Obiekt wywołujący jest uruchomiona na komputerze zdalnym.|  
|`PFLAG_DEBUGGEE`|Obiekt wywołujący jest obecnie debugowany (dodatkowe informacje dotyczące kierowania są zwracane w każdym węźle).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Dołączony do obiektu wywołującego, ale nie jest uruchomiony przez debuger.|  
|`PFLAG_REASON_WATCH`|Obiekt wywołujący chce, aby śledzić zdarzenia. Jeśli ta flaga nie jest ustawiona. następnie zdarzenia wywołania zwrotnego jest usuwany, a obiekt wywołujący nie będzie już otrzymywać powiadomienia.|  
  
 `pPort`  
 [in] Port procesu wywołującego jest uruchomiona na.  
  
 `processId`  
 [in] [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktury zawierający identyfikator procesu, który zawiera program jest zagrożona.  
  
 `EngineFilter`  
 [in] Tablica identyfikatory GUID aparatami debugowania skojarzonych z procesem.  
  
 `guidLaunchingEngine`  
 [in] Identyfikator GUID aparatu debugowania uruchomienia tego procesu (jeśli istnieje).  
  
 `pEventCallback`  
 [in] [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) obiekt, który odbiera powiadomienia o zdarzeniach.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Gdy obiekt wywołujący chce usunąć program obsługi zdarzeń, które zostało ustanowione poprzednie wywołanie tej metody, wywołujący te same parametry, jak podczas pierwszej, ale pozostawia poza `PFLAG_REASON_WATCH` flagi.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób zaimplementować tę metodę do **CDebugEngine** obiekt ujawniający [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interfejsu.  
  
```cpp  
STDMETHODIMP CDebugEngine::WatchForProviderEvents(  
    PROVIDER_FLAGS Flags,   
    IDebugDefaultPort2 *pPort,   
    AD_PROCESS_ID processId,   
    CONST_GUID_ARRAY EngineFilter,   
    REFGUID guidLaunchingEngine,   
    IDebugPortNotify2 *pPortNotify)  
{  
    HRESULT hRes = E_FAIL;  
  
    if (EVAL(pPort != NULL) && EVAL(pPortNotify != NULL))  
    {  
        // We will only watch/send events about the process if the debugger  
        // is actually debugging the process, and only if this is an attach or a LoRIE launch  
        if (IsFlagSet(Flags, PFLAG_DEBUGGEE) &&  
            guidLaunchingEngine == GUID_NULL &&  
            processId.ProcessIdType == AD_PROCESS_ID_SYSTEM)  
        {  
            // We don't support WatchForProviderEvents when in interop mode  
            if (m_fInterop)  
            {  
                ASSERT(!"Shouldn't ever be called in interop mode");  
                hRes = E_FAIL;  
            }  
            else  
            {  
                if (IsFlagSet(Flags, PFLAG_REASON_WATCH))  
                {  
                    // QI to get IDebugEventCallback2 which is required.  
                    CComQIPtr<IDebugEventCallback2> pCallback(pPortNotify);  
  
                    ASSERT(pCallback != NULL);  
                    if ( pCallback != NULL )  
                    {  
                        // Register the callback  
                        hRes = this->InitDebugSession(pCallback);  
  
                        if ( S_OK == hRes )  
                        {  
                            // Get the IDebugProcess2 from the port and call AttachImpl  
                            CComPtr<IDebugProcess2> spProcess;  
  
                            hRes = pPort->GetProcess(processId, &spProcess);  
  
                            if (HREVAL(S_OK, hRes))  
                            {  
                                hRes = AttachImpl(spProcess, NULL, NULL, processId.ProcessId.dwProcessId, ATTACH_REASON_USER, NULL);  
  
                                if ( FAILED(hRes) && (!m_pPidList || 0 == m_pPidList->GetCount()) )  
                                    this->Cleanup();  
                            }  
                        }  
                        else  
                            this->Cleanup();  
                    }  
                    else  
                        hRes = E_FAIL;  
                }  
                else  
                {  
                    // Detach will be done by SDM calling on programs directly if there are managed programs.  
  
                    // This handling is the case where no managed code ever ran.  
                    if ( this->IsProcessBeingDebugged(processId.ProcessId.dwProcessId) )  
                    {  
                        ProgramList *pProgList = this->GetProgramListCopy();  
  
                        if ( EVAL(pProgList) )  
                        {  
                            if ( pProgList->GetCount() == 0)  
                            {  
                                CComPtr<ICorDebugProcess> pCorProcess;  
  
                                hRes = this->GetCorProcess(processId.ProcessId.dwProcessId, &pCorProcess);  
  
                                if (HREVAL(S_OK, hRes) )  
                                {  
                                    hRes = pCorProcess->Stop(INFINITE);  
  
                                    if ( HREVAL(S_OK, hRes) )  
                                        hRes = pCorProcess->Detach();  
                                }  
  
                                // Tell the engine that it should unregister this process from com+  
                                this->UnregisterProcess(processId.ProcessId.dwProcessId);  
  
                                // If there are no more pids left then cleanup everything.  
                                if ( 0 == m_pPidList->GetCount() )  
                                    this->Cleanup();  
                            }  
                            // This is needed for cases where the SDM has not yet recieved program create  
                            // by the time that we need to detach (example: the managed attach succeeds,  
                            // but some other attach step fails).  
                            else  
                            {  
                                PROGNODE *pProgNode = NULL;  
                                while ( pProgNode = pProgList->Next(pProgNode) )  
                                {  
                                    CDebugProgram * pProgram = ((CDebugProgram *)pProgNode->data);  
                                    hRes = pProgram->Detach();  
                                }  
                            }  
  
                            delete pProgList;  
                        }  
                    }  
                    else  
                        hRes = S_OK;  
                }  
            }  
        }  
        else  
        {  
            hRes = S_FALSE;  
        }  
    }  
    else  
    {  
        hRes = E_INVALIDARG;  
    }  
  
    return hRes;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)