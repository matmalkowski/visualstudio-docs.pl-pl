---
title: IEnumDebugModules2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugModules2
helpviewer_keywords: IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 481a9c04b56ad330731b1c5a06863eb7b3f0f8e2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Ten interfejs wylicza listę modułów.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs reprezentujący listę modułów ładowanych w programie.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Visual Studio wywołania [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) uzyskanie tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IEnumDebugModules2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dalej](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Pobiera określoną liczbę modułów w kolejności wyliczenia.|  
|[Pomiń](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Pomija określoną liczbę modułów w kolejności wyliczenia.|  
|[Resetowanie](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Resetuje sekwencję wyliczenia na początku.|  
|[Klonowania](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Tworzy moduł wyliczający, który zawiera takim samym stanie wyliczenie jako bieżący modułu wyliczającego.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Pobiera liczbę modułów.|  
  
## <a name="remarks"></a>Uwagi  
 Visual Studio będzie korzystać głównie w celu aktualizacji tego interfejsu **modułów** okna.  
  
 Dla celów debugowania w programie Visual Studio, program jest logiczną sekwencji instrukcji kodu, które mogą przechodzić przez granice modułu, dlatego potrzebę listę modułów z jednym [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsu. Moduł pierwszy na liście zwykle zawiera punkt wejścia początkowej dla skojarzonego programu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)