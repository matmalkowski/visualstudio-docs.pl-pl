---
title: IDebugCodeContext2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b46ec36a93ac91647a3f17aac28187519ca2447
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Ten interfejs reprezentuje pozycję początkową instrukcji kodu. Dla większości architektur środowiska wykonawczego dzisiaj, kontekst kodu można traktować jako adresu w strumieniu wykonywania programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania implementuje ten interfejs powiązać pozycja instrukcję kodu położenie dokumentu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 W wielu interfejsach zwracają ten interfejs najbardziej popularnych [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Jest również używany często [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) interfejsu także jak informacji o rozpoznawaniu punktu przerwania.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Oprócz metod na [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interfejsu, tego interfejsu implementuje następujących metod:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Pobiera kontekst dokumentu umożliwiająca kontekstu active kodu.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Pobiera informacje o języku dla tego kontekstu kodu.|  
  
## <a name="remarks"></a>Uwagi  
 Najważniejsza różnica między `IDebugCodeContext2` interfejsu i [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interfejsu jest to, że `IDebugCodeContext2` zawsze jest wyrównany do instrukcji. Oznacza to, że `IDebugCodeContext2` zawsze wskazuje na początku instrukcji, podczas gdy `IDebugMemoryContext2` mogą wskazywać na dowolnym bajtów pamięci w architekturze środowiska wykonawczego. `IDebugCodeContext2` jest zwiększany instrukcje, a nie rozmiaru magazynu podstawowego (zwykle bajtów).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [Dalej](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)