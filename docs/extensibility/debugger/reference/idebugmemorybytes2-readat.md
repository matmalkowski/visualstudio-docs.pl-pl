---
title: IDebugMemoryBytes2::ReadAt | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 612a065286723e3c2b68a9ce5bd31c850d030959
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114089"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Odczytuje sekwencję bajtów, rozpoczynając od podanej lokalizacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```csharp  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStartContext`  
 [in] [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) obiekt, który określa, gdzie należy rozpocząć odczyt bajtów.  
  
 `dwCount`  
 [in] Liczba bajtów do odczytania. Określa również długość `rgbMemory` tablicy.  
  
 `rgbMemory`  
 [w, out] Tablicy wypełnione bajtów odczytanych w rzeczywistości.  
  
 `pdwRead`  
 [out] Zwraca liczbę bajtów ciągłe faktycznie odczytu.  
  
 `pdwUnreadable`  
 [w, out] Zwraca liczbę bajtów nie można go odczytać. Może być wartością null, jeśli klient jest zainteresowany liczba bajtów nie można go odczytać.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wnosi 100 bajtów i odczytanie jest pierwszym 50, 20 dalej są nieczytelne, a pozostałe 30 można odczytać, ta metoda zwraca:  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 W takim przypadku ponieważ `*pdwRead + *pdwUnreadable < dwCount`, wywołujący musi wywoływania dodatkowe pozostałe 30 bajtów 100 oryginalne żądanie odczytu i [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) przekazano obiekt `pStartContext` parametru musi być zaawansowane przez 70.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)