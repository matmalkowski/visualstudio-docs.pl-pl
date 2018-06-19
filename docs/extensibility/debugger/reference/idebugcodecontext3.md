---
title: IDebugCodeContext3 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 451e61ab7d6f74c83898987cdbecad2a9e13b06c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108511"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Rozszerza [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interfejsu, aby włączyć pobieranie interfejsów modułu i procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Implementowany przez aparaty debugowania i używane przez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pakietu debugowania.  
  
## <a name="methods"></a>Metody  
 Oprócz metod na `IDebugCodeContext2` interfejsu, tego interfejsu implementuje następujących metod:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Pobiera odwołanie do interfejsu debugowania modułu.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Pobiera odwołanie do interfejsu debugowania procesu.|  
  
## <a name="remarks"></a>Uwagi  
 Jest to opcjonalne interfejsu, która zazwyczaj nie muszą być wykonywane.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll