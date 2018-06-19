---
title: IDebugObject::IsReadOnly | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84cac5c66dd20dc9641fee7f05b456b25cbe2ffc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113666"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Określa, czy ten obiekt jest tylko do odczytu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsReadOnly(   
   BOOL* pfIsReadOnly  
);  
```  
  
```csharp  
int IsReadOnly(  
   out int pfIsReadOnly  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pfIsReadOnly`  
 [out] Zwraca wartość inną niż zero (`TRUE`) Jeśli ten obiekt jest tylko do odczytu; w przeciwnym razie, zwraca zero (`FALSE`).  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt tylko do odczytu nie może mieć wartość zmienić po jego utworzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)