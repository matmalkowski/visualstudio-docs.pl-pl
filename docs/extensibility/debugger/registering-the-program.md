---
title: Rejestrowanie programu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: eb61257b80e3f8b4a09819b2b037f342e2ecbee0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="registering-the-program"></a>Rejestrowanie programu
Po aparat debugowania uzyskała portu, reprezentowany przez [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfejsu, następnym krokiem podczas włączania programu do debugowania jest zarejestrowanie go za pomocą portu. Po zarejestrowaniu program jest dostępny do debugowania za pomocą jednej z następujących sposobów:  
  
-   Proces dołączania, dzięki czemu debuger przejęcie kontroli debugowania uruchomionej aplikacji.  
  
-   Just-in-time (JIT) debugowania, co umożliwia debugowanie po fakcie program, który działa niezależnie od debugera. Architektura środowiska wykonawczego przechwytuje usterki, Debuger jest powiadamiany o przed systemu operacyjnego lub środowisko uruchomieniowe zwalnia pamięć i zasoby źle działający program.  
  
## <a name="registering-procedure"></a>Rejestrowanie procedury  
  
#### <a name="to-register-your-program"></a>Aby zarejestrować program  
  
1.  Wywołanie [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) metody implementowane przez port.  
  
     `IDebugPortNotify2::AddProgramNode`wskaźnik do wymaga [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfejsu.  
  
     Zazwyczaj podczas ładowania programu systemu operacyjnego oraz środowisko wykonawcze tworzy węzeł programu. Jeśli aparat debugowania (DE) jest proszony o załadować program DE tworzy i rejestruje węzła programu.  
  
     W poniższym przykładzie przedstawiono aparat debugowania, otwierając program i rejestrując ją z portem.  
  
    > [!NOTE]
    >  To nie jest jedynym sposobem na uruchamianie i wznowić proces; to jest głównie przykład rejestrowania programu z portem.  
  
    ```cpp  
    // This is an IDebugEngineLaunch2 method.  
    HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,  
                                          IDebugPort2 *pPort,  
                                          /* omitted parameters */,  
                                          IDebugProcess2**ppDebugProcess)  
    {  
        // do stuff here to set up for a launch (such as handling the other parameters)  
        ...  
  
        // Now get the IPortNotify2 interface so we can register a program node  
        // in CDebugEngine::ResumeProcess.  
        CComPtr<IDebugDefaultPort2> spDefaultPort;  
        HRESULT hr = pPort->QueryInterface(&spDefaultPort);  
        if (SUCCEEDED(hr))  
        {  
            CComPtr<IDebugPortNotify2> spPortNotify;  
            hr = spDefaultPort->GetPortNotify(&spPortNotify);  
            if (SUCCEEDED(hr))  
            {  
                // Remember the port notify so we can use it in ResumeProcess.  
                m_spPortNotify = spPortNotify;  
  
                // Now launch the process in a suspended state and return the  
                // IDebugProcess2 interface  
                CComPtr<IDebugPortEx2> spPortEx;  
                hr = pPort->QueryInterface(&spPortEx);  
                if (SUCCEEDED(hr))  
                {  
                    // pass on the parameters we were given (omitted here)  
                    hr = spPortEx->LaunchSuspended(/* omitted paramters */,ppDebugProcess)  
                }  
            }  
        }  
        return(hr);  
    }  
  
    HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)  
    {  
        // Make a program node for this process  
        HRESULT hr;  
        CComPtr<IDebugProgramNode2> spProgramNode;  
        hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);  
        if (SUCCEEDED(hr))  
        {  
            hr = m_spPortNotify->AddProgramNode(spProgramNode);  
            if (SUCCEEDED(hr))  
            {  
                // resume execution of the process using the port given to us earlier.  
               // (Querying for the IDebugPortEx2 interface is valid here since  
               // that's how we got the IDebugPortNotify2 interface in the first place.)  
                CComPtr<IDebugPortEx2> spPortEx;  
                hr = m_spPortNotify->QueryInterface(&spPortEx);  
                if (SUCCEEDED(hr))  
                {  
                    hr  = spPortEx->ResumeProcess(pDebugProcess);  
                }  
            }  
        }  
        return(hr);  
    }  
  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do portu](../../extensibility/debugger/getting-a-port.md)   
 [Włączanie debugowania programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)