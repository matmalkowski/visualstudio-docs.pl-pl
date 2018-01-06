---
title: IEnumDebugBoundBreakpoints2::Next | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugBoundBreakpoints2::Next
helpviewer_keywords: IEnumDebugBoundBreakpoints2::Next
ms.assetid: cb3a249f-2282-4bdc-b6d8-a4ee4bfb8365
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 13fb11be68bf2801f9a9ca88856a5ae7e2801e70
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugboundbreakpoints2next"></a>IEnumDebugBoundBreakpoints2::Next
Zwraca następny zestaw elementów z wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next(  
   ULONG                    celt,  
   IDebugBoundBreakpoint2** rgelt,  
   ULONG*                   pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint                     celt,  
   IDebugBoundBreakpoint2[] rgelt,  
   ref uint                 pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba elementów do pobrania. Określa maksymalny rozmiar `rgelt` tablicy.  
  
 `rgelt`  
 [w, out] Tablica [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) elementy do wypełnienia.  
  
 `pceltFetched`  
 [out] Zwraca liczbę elementów, w rzeczywistości zwracane w `rgelt`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli mniej niż żądana liczba elementów mogą być zwracane; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)   
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)