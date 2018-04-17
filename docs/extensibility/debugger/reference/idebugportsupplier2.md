---
title: IDebugPortSupplier2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4aa26aa37b40c0e483342e6eb93cbac15bbbfc2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Ten interfejs udostępnia porty do menedżera sesji debugowania (SDM).  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawcy niestandardowego numeru portu implementuje ten interfejs reprezentujący dostawcę portu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie `CoCreateInstance` z dostawcą portu `GUID` zwraca tego interfejsu (jest to typowy sposób uzyskać ten interfejs). Na przykład:  
  
```cpp  
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)  
{  
    IDebugPortSupplier2 *pPS = NULL;  
    if (pPortSupplierGuid != NULL) {  
        CComPtr<IDebugPortSupplier2> spPortSupplier;  
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);  
        if (spPortSupplier != NULL) {  
            pPS = spPortSupplier.Detach();  
        }  
    }  
    return (pPS);  
}  
```  
  
 Wywołanie [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) zwraca ten interfejs reprezentujący bieżącego dostawcy port używany przez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) zwraca ten interfejs reprezentujący dostawcę portu utworzony port.  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) reprezentuje listę `IDebugPortSupplier` interfejsów ( `IEnumDebugPortSuppliers` interfejsu są uzyskiwane z [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), reprezentujący wszyscy dostawcy portu zarejestrowany [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]).  
  
 Aparat debugowania zwykle nie wchodzi w interakcję z dostawcą portu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugPortSupplier2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Pobiera nazwę dostawcy portu.|  
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Pobiera identyfikator dostawcy portów.|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Pobiera portu od dostawcy portu.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Wylicza portów, które już istnieją.|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Sprawdza, czy dostawca portu obsługuje dodawanie nowych portów.|  
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Dodaje port.|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Usuwa portu.|  
  
## <a name="remarks"></a>Uwagi  
 Dostawca portu można identyfikacji według nazwy i Identyfikatora, dodawania i usuwania portów oraz wyliczyć wszystkie porty, które zapewnia portu dostawcy.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)