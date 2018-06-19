---
title: IDebugField::GetInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6738306abd991062c5091f95375972ffe0d3384e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116597"
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