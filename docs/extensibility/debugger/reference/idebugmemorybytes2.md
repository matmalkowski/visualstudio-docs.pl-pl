---
title: IDebugMemoryBytes2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMemoryBytes2
helpviewer_keywords: IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80e60a6cfb31532c04963e0347fe95e415d32af4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Ten interfejs reprezentuje liczbę bajtów pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania bajtów w pamięci.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) zwraca ten interfejs w celu zapewnienia dostępu do pamięci. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) i [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) zwracać ten interfejs w celu zapewnienia dostępu do obiektu bajtów.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugMemoryBytes2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Odczytuje sekwencję bajtów, rozpoczynając od podanej lokalizacji.|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Zapisuje `dwCount` bajtów, zaczynając od `pStartContext`.|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Pobiera rozmiar w bajtach pamięci reprezentowany przez ten interfejs.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku właściwości [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) udostępnia interfejs reprezentujący tablicy `IDebugMemoryBytes2` interfejsu, aby uzyskać dostęp do wartości w tablicy.  
  
 Visual Studio **widoku pamięci** wywołania [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) można pobrać `IDebugMemoryBytes2` interfejs do uzyskiwania dostępu do pamięci systemowej. Adres, aby można było uzyskać dostęp jest uzyskiwany przez analizowania wyrażenia wprowadzana jako adres do widoku pamięci i ocenę przy użyciu analizowanej wyrażenie [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) uzyskanie `IDebugProperty2` interfejsu. Wywołanie [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) zwraca [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , który opisuje adres pamięci. Ten kontekst pamięci są następnie przekazywane do [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) i [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)