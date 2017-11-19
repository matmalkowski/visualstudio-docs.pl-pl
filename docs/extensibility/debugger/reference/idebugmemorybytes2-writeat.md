---
title: IDebugMemoryBytes2::WriteAt | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb9b887ff8501516ea063dccf0247b0915de1d63
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Zapisuje określoną liczbę bajtów pamięci, zaczynając od określonego adresu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT WriteAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory  
);  
```  
  
```csharp  
int WriteAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStartContext`  
 [in] [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) obiekt, który określa lokalizację teraz wysyłali bajtów.  
  
 `dwCount`  
 [in] Liczba bajtów do zapisania.  
  
 `rgbMemory`  
 [in] Bajty do zapisania. Ta tablica zakłada, że co najmniej `dwCount` rozmiar bajtów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` nie wszystkie bajty może być zapisany lub zwraca kod błędu (zazwyczaj `E_FAIL`).  
  
## <a name="remarks"></a>Uwagi  
 Jeśli adres początkowy nie jest w oknie pamięci reprezentowany przez to [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) obiekt występuje nie zapisywania i z kodem błędu `E_FAIL` jest zwracany — nawet wtedy, gdy wartość do zapisania nakłada się w pamięci.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)