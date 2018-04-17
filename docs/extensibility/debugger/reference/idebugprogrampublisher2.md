---
title: IDebugProgramPublisher2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f927a3215a415745c2e9004573810101c229ab5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Ten interfejs umożliwia aparat debugowania (DE) lub dostawcy niestandardowego numeru portu do zarejestrowania programy do debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProgramPublisher2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Visual Studio implementuje ten interfejs, aby zarejestrować programy debugowany aby stały się widoczne dla debugowania wielu procesom.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołania modelu COM `CoCreateInstance` działać z `CLSID_ProgramPublisher` uzyskanie tego interfejsu (Zobacz przykład). Niemcy lub dostawcy niestandardowego numeru portu używa tego interfejsu zarejestrować program węzły, które reprezentują debugowane programy.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Ten interfejs implementuje następujących metod:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Udostępnia węzła programu DEs i sesja debugowania Menedżera (SDM).|  
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Usunięcie węzła programu tak, aby nie jest już dostępne.|  
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Udostępnia program DEs i SDM.|  
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Usuwa program, aby nie jest już dostępne.|  
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Ustawia flagę wskazującą, czy jest obecny debuger.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs udostępnia programy i węzły programu (to znaczy "" je opublikował) dla DEs i Menedżer debugowania sesji (SDM). Aby uzyskać dostęp do programów publikowanych i węzły program, należy użyć [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interfejsu. Jest to tylko sposób Visual Studio może rozpoznać jest debugowany program.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób tworzenia wystąpienia wydawca programu i zarejestrować węzła programu. To jest pobierana z samouczka [publikowania w węźle programu](http://msdn.microsoft.com/en-us/d0100e02-4e2b-4e72-9e90-f7bc11777bae).  
  
```cpp  
// This is how m_srpProgramPublisher is defined in the class definition:  
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.  
  
void CProgram::Start(IDebugEngine2 * pEngine)  
{  
    m_spEngine = pEngine;  
  
    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);  
    if ( FAILED(hr) )  
    {  
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);  
        return;  
    }  
  
    // Register ourselves with the program publisher. Note that  
    // CProgram implements the IDebgProgramNode2 interface, hence  
    // the static cast on "this".  
    hr = m_srpProgramPublisher->PublishProgramNode(  
        static_cast<IDebugProgramNode2*>(this));  
    if ( FAILED(hr) )  
    {  
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);  
        m_srpProgramPublisher.Release();  
        return;  
    }  
  
    ATLTRACE("Added program node.\n");  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)