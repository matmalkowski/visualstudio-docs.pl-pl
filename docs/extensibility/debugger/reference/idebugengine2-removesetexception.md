---
title: IDebugEngine2::RemoveSetException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::RemoveSetException
helpviewer_keywords: IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 01d7f2ac15475e5d7d984e7e1624749d2b633195
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Usuwa określony wyjątek, aby nie jest już obsługiwany przez aparat debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT RemoveSetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```csharp  
int RemoveSetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pException`  
 [in] [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struktury opisujący wyjątek, który ma zostać usunięty.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wyjątek usuwana musi wcześniej skonfigurowane przez wywołanie wcześniejszych [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) metody.  
  
 Aby usunąć wszystkie wyjątki zestawu jednocześnie, należy wywołać [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)