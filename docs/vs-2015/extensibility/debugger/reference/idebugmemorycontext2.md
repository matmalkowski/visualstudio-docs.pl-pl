---
title: IDebugMemoryContext2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc5237fe22b2720f326cffa6b8df2f639e7c5ef7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677169"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugMemoryContext2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmemorycontext2).  
  
Ten interfejs reprezentuje pozycję w przestrzeni adresowej maszyny z uruchomionym programem debugowanego programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs reprezentujący adres w pamięci.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) lub [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) zwraca ten interfejs. Ponadto wywołania [Dodaj](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) i [Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) zwracają nowe kopie tego interfejsu, po zastosowaniu odpowiednich operacji arytmetycznej.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugMemoryContext2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Getname —](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Pobiera nazwę użytkownika zawiera dla tego kontekstu.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Pobiera informacje z opisem w tym kontekście.|  
|[Dodaj](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Dodaje określoną wartość do adresu bieżącego kontekstu, aby utworzyć nowy kontekst.|  
|[Odejmowanie](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Odejmuje określoną wartość z bieżącego kontekstu adres, aby utworzyć nowy kontekst.|  
|[Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Porównuje dwa konteksty w sposób wskazany przez porównanie flag.|  
  
## <a name="remarks"></a>Uwagi  
 Visual Studio **pamięci** wywołania okna [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) uzyskać `IDebugMemoryContext2` interfejsu, który zawiera obliczane wyrażenie używane dla adresu pamięci. Ten kontekst jest następnie przekazywany do [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) i [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) do określenia adresu do odczytu lub zapisu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)

