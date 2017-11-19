---
title: IDebugMemoryContext2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMemoryContext2
helpviewer_keywords: IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6d0f631d1cb41a0882dcf4d67754df24e6e83f23
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Ten interfejs reprezentuje pozycję w przestrzeni adresowej w komputerze, na którym działa program debugowany.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs reprezentuje adres w pamięci.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) lub [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) zwraca tego interfejsu. Ponadto wywołań [Dodaj](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) i [Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) zwrócić nowe kopie tego interfejsu, po zastosowaniu odpowiednich operacji arytmetycznej.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugMemoryContext2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Pobiera nazwę użytkownika wyświetlanej dla tego kontekstu.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Pobiera informacje, które opisano w tym kontekście.|  
|[Dodaj](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Dodaje określoną wartość do bieżącego kontekstu adres, aby utworzyć nowy kontekst.|  
|[Odejmowanie](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Odejmuje określoną wartość z bieżącego kontekstu adres, aby utworzyć nowy kontekst.|  
|[Porównaj](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Porównuje dwa kontekstów w ten sposób wskazywanym przez porównanie flagi.|  
  
## <a name="remarks"></a>Uwagi  
 Visual Studio **pamięci** wywołań okna [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) uzyskanie `IDebugMemoryContext2` interfejsu, który zawiera obliczane wyrażenie używane dla adresu pamięci. Ten kontekst są następnie przekazywane do [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) i [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) określenie adresu do odczytu lub zapisu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)