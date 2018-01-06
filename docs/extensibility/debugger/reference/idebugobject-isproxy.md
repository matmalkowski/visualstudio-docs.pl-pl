---
title: IDebugObject::IsProxy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugObject::IsProxy
- IsProxy
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 00262d39bc5a70ad24dc599f3c174ec5fe826f50
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobjectisproxy"></a>IDebugObject::IsProxy
Określa, czy obiekt jest przezroczystego obiektu pośredniczącego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsProxy (  
   BOOL* pfIsProxy  
);  
```  
  
```csharp  
int IsProxy (  
   out bool pfIsProxy  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pfIsProxy`  
 [out] `TRUE` Jeśli obiekt jest przezroczystego obiektu pośredniczącego; w przeciwnym razie `FALSE`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest implementowana przez domyślny aparat debugowania języka C++.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)