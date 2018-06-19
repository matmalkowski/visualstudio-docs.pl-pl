---
title: Wprowadzenie do portu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c20b3e3bdc2644e7af7d9a35de06af7f96d7680
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102996"
---
# <a name="getting-a-port"></a>Wprowadzenie do portu
Port reprezentuje połączenie z komputerem, na którym są uruchomione procesy. Ten komputer może być komputer lokalny lub zdalny komputer (które można prawdopodobnie korzystać z systemu operacyjnego systemu Windows, zobacz [porty](../../extensibility/debugger/ports.md) Aby uzyskać więcej informacji).  
  
 Port jest reprezentowana przez [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfejsu. Służy do uzyskiwania informacji na temat procesów uruchomionych na komputerze, na którym port jest połączony.  
  
 Aparat debugowania musi mieć dostęp do portu, aby zarejestrować program węzłów z portem i można zrealizować żądań dla informacji o procesie. Na przykład, jeśli implementuje aparat debugowania [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) interfejsu implementację [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) metody poprosić port na potrzeby procesu informacje, które ma zostać zwrócona.  
  
 Visual Studio dostarcza niezbędne port aparat debugowania i uzyska tego portu od dostawcy portu. Jeśli program jest podłączony do (albo z debugera lub ze względu na wyjątek został zgłoszony, który wyzwala okno dialogowe Just in Time [JIT]), użytkownik otrzymuje wybór transportu (inną nazwę dla dostawcy portu) do użycia. W przeciwnym razie jeśli użytkownik uruchamia program z poziomu debugera, system projektu określa dostawcy port do użycia. W obu przypadkach program Visual Studio tworzy wystąpienie dostawcy portu, reprezentowany przez [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfejsu i prosi o nowy port wywołując [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) z [ IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) interfejsu. Tego portu są następnie przekazywane do aparatu debugowania w postaci jednego lub drugiego.  
  
## <a name="example"></a>Przykład  
 Ten fragment kodu przedstawia sposób użycia portu dostarczony do [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) zarejestrować program węzła w [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Dla jasności zostały pominięte parametry niepowiązane bezpośrednio z tę koncepcję.  
  
> [!NOTE]
>  W tym przykładzie używa portu do uruchomienia i wznowić proces i przy założeniu, że [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) interfejs jest wdrażany na porcie. W żadnym wypadku nie jest jedynym sposobem, aby wykonać te zadania, a jest to możliwe, że port nie nawet zajmuje innych niż zostanie automatycznie [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) nadane.  
  
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
 [Rejestrowanie programu](../../extensibility/debugger/registering-the-program.md)   
 [Włączanie programu do debugowania](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Port dostawcy](../../extensibility/debugger/port-suppliers.md)   
 [Porty](../../extensibility/debugger/ports.md)