---
title: IDebugDisassemblyStream2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c1598ec8a6e5fca5275384c00433d74d22ce3505
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107897"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Ten interfejs reprezentuje strumienia instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania implementuje ten interfejs obsługuje dezasemblacji kod programu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) metoda zwraca tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugDisassemblyStream2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Odczyt](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Odczytuje instrukcje począwszy od bieżącej pozycji w strumieniu dezasemblacji.|  
|[Wyszukiwanie](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Przesuwa kursor odczytu w strumieniu dezasemblacji daną liczbę instrukcji względem określonej pozycji.|  
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Zwraca identyfikator lokalizacji kodu dla kontekstu określonego kodu.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Zwraca obiekt kontekstu kodu odpowiadający identyfikator lokalizacji określony kod.|  
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Zwraca identyfikator lokalizacji kodu, który reprezentuje bieżącej lokalizacji kodu.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Pobiera dokument źródłowy skojarzony z tym strumieniu dezasemblacji.|  
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Pobiera zakres tego strumienia dezasemblacji.|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Pobiera rozmiaru tego strumienia dezasemblacji.|  
  
## <a name="remarks"></a>Uwagi  
 Można utworzyć strumienia dezasemblacji do reprezentacji całej przestrzeni lub po prostu funkcji lub moduł w przestrzeni. Każda instrukcja jest reprezentowana przez [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury zwrócony przez wywołanie do [odczytu](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)