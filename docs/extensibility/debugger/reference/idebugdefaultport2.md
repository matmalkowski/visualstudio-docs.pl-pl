---
title: IDebugDefaultPort2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c6d131ab24cc57af1846f89b61afa2d89ae2cacb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31106906"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Ten interfejs zapewnia kilka metod dostępu do portu serwera i powiadomień urządzenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Visual Studio implementuje ten interfejs do reprezentowania port debugowania, aby uzyskać dostęp do programów. Dostawcy niestandardowego numeru portu można też wdrożyć ten interfejs, jeśli obsługi debugowania zdalnego.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Argument do metody [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interfejsu dostarcza tego interfejsu. Wywoływanie [QueryInterface](/cpp/atl/queryinterface) na [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfejsu można również uzyskać tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Oprócz metody zdefiniowane w [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), implementuje ten interfejs następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Pobiera interfejs powiadomień portu z tego portu.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Pobiera interfejs do serwera obsługującego ten port.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Określa, czy ten port jest uruchomiony na komputerze lokalnym.|  
  
## <a name="remarks"></a>Uwagi  
 Nazwa "`IDebugDefaultPort2`" jest nieco misnomer, ponieważ nie reprezentuje domyślny port. Można nadać mu "IDebugPort3."  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)