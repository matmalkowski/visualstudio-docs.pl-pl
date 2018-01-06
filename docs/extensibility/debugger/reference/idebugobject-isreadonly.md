---
title: IDebugObject::IsReadOnly | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::IsReadOnly
helpviewer_keywords: IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f1bcd4dc3f23a5305a2b40ee19affb8ae28ffd6f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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