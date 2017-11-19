---
title: IDebugThread2::EnumFrameInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::EnumFrameInfo
helpviewer_keywords: IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 15e775af8f04e52b5cb1329312c1e0226a14c733
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Pobiera listę ramek stosu dla tego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFieldSpec`  
 [in] Kombinacja flag z [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) wyliczenia, która określa, które pola [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury mają zostać wypełnione. Określ `FIF_FUNCNAME_FORMAT` flagi format nazwy funkcji w jednym ciągu.  
  
 `nRadix`  
 [in] Podstawa używaną w formatowaniu liczbowych zawartych w moduł wyliczający.  
  
 `ppEnum`  
 [out] Zwraca [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) obiekt, który zawiera listę [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury opisujące ramki stosu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ramki wątku znajduje się w kolejności, z bieżącej ramki wyliczyć najpierw i najstarsze ramki wyliczyć ostatnio.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)