---
title: IDebugPortNotify2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortNotify2
helpviewer_keywords: IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e913a26d35d7207193d5086b68c785f737f8bfee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Ten interfejs rejestruje lub wyrejestrowuje program, który może być debugowany z portem, którym jest uruchomiona.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawcy niestandardowego numeru portu implementuje ten interfejs obsługuje dodawanie i usuwanie programów z portu. Jest on zwykle implementowany na ten sam obiekt, który implementuje [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [QueryInterface](/cpp/atl/queryinterface) na `IDebugPort2` interfejsu zwraca tego interfejsu. Ponadto wywołanie [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) zwraca tego interfejsu. Aparat debugowania można zobaczyć ten interfejs jako parametr [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugPortNotify2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Rejestruje port, który jest uruchomiony na program, który może być debugowany.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Wyrejestrowuje program, który może być debugowany z portu, którym jest uruchomiona.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli port debugowania nie ma sposobu na określenie, kiedy załadowany lub zwalnianie programy, dostawcy niestandardowego numeru portu musi zawierać implementację tego interfejsu. Wszystkie programy, które są ładowane do debugowania za pośrednictwem określonego portu są śledzone za pomocą tego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)