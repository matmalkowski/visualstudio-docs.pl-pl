---
title: IDebugField::GetInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::GetInfo
helpviewer_keywords: IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ff061a73de70918480450ea8763f9eea2fc34cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
Ta metoda pobiera zawiera informacje o polu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetInfo(   
   FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO* pFieldInfo  
);  
```  
  
```csharp  
int GetInfo(  
   enum_FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO[] pFieldInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFields`  
 [in] Kombinację [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) stałe, które wybiera informacje, które mają być wyświetlane. Jeśli pole reprezentuje symbol, jest to zazwyczaj nazwa symbolu i typu.  
  
 `pFieldInfo`  
 [out] Zwraca informacje podane [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)