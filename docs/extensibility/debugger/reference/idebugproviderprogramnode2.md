---
title: IDebugProviderProgramNode2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8c083d9b054ecde18d1e1fff8ca5bb8cbb6be659
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Ten interfejs marshals interfejsy związane z przekraczaniem granic procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProviderProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs dla tego samego obiektu, który implementuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) do obsługi organizowania interfejsy przez granice procesu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [QueryInterface](/cpp/atl/queryinterface) na `IDebugProgramNode2` interfejs do uzyskania tego interfejsu. Jeśli nie można uzyskać interfejsu, DE nie obsługuje przekazywanie interfejsów.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Ten interfejs implementuje następującą metodę:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Pobiera określonego interfejsu przez granice procesu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest wdrażany, gdy DE uruchamia się w innej przestrzeni procesu z debugowanego programu: na przykład, gdy DE jest uruchomiona w obszarze procesu Visual Studio zamiast obszaru procesu debugowany program.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)