---
title: IDebugProgramEx2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramEx2
helpviewer_keywords: IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ea614bee34911d2cd919ce3ca67a00834a6132c4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Ten interfejs umożliwia sesji debugowania Menedżera (SDM) dołączyć do programu i uzyskać węzła programu skojarzonego z programem.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawcy niestandardowego numeru portu implementuje ten interfejs dla tego samego obiektu jako [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsu, aby umożliwić SDM dołączyć do programu, w tym samym czasie co dostawcy portu śledzić wszystkie sesje dołączony do Program. Jeśli wybiera dostawcy niestandardowego numeru portu może zawierać implementację tego interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołania SDM [QueryInterface](/cpp/atl/queryinterface) na `IDebugProgram2` interfejsu można uzyskać interfejsu do śledzenia sesji, które zostały dołączone do programów.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugProgramEx2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Dołącza program do sesji.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Pobiera węzeł program skojarzony z programu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest prywatny między SDM i programem.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)