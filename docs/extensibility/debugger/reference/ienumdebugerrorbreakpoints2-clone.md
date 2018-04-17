---
title: IEnumDebugErrorBreakpoints2::Clone | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugErrorBreakpoints2::Clone
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2::Clone
ms.assetid: f6fb4985-8dd6-4a9b-98e0-15dbc64cc9ec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7e8b5e1c4c0b5c4f52e6b9af6b673d6d78c03ea9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugerrorbreakpoints2clone"></a>IEnumDebugErrorBreakpoints2::Clone
Zwraca kopię bieżącego wyliczenie jako oddzielny obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Clone(  
   IEnumDebugErrorBreakpoints2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugErrorBreakpoints2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Zwraca kopię tego wyliczenia jako oddzielny obiekt.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Kopiuj wyliczenia ma takim samym stanie, co oryginalne w czasie, gdy ta metoda zostanie wywołana. Jednak kopiowania i oryginalny stan są oddzielone i można zmieniać pojedynczo.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)