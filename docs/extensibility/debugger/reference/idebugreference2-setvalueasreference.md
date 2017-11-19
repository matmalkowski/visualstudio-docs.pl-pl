---
title: IDebugReference2::SetValueAsReference | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugReference2::SetValueAsReference
helpviewer_keywords: IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7b684f540bf5488f1febc93228c73259ccf03c77
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Ustawia wartość odwołania z innego odwołania. Zarezerwowane do użytku w przyszłości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetValueAsReference (   
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```cpp  
int SetValueAsReference (   
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rgpArgs`  
 [in] Tablica [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) używanych do określania, jak ustawić wartość odwołania do obiektów.  
  
 `dwArgCount`  
 [in] Liczba odwołań w tablicy.  
  
 `pValue`  
 [in] [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) obiektu, z którego można ustawić wartości właściwości.  
  
 `dwTimeout`  
 [in] Maksymalny czas (w milisekundach) oczekiwania przed powrotem z tej metody. Użyj `INFINITE` będzie czekać w nieskończoność.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca `E_NOTIMPL`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)