---
title: IDebugBreakpointChecksumRequest2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cb319b14e1d373abe3c0634c768bfe1dcb04f539
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101121"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Reprezentuje dokumentu sumy kontrolnej dla żądania punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Zaimplementowane przez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugowania pakietu i używane przez aparaty debugowania.  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `IDebugBreakpointChecksumRequest2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Pobiera sumy kontrolnej dokumentu dla żądania przerwania podane Unikatowy identyfikator algorytmu sumy kontrolnej do użycia.|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Określa, czy suma kontrolna jest włączone dla tego dokumentu.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll