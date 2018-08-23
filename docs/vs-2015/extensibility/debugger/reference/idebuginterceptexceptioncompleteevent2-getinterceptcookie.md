---
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 10496d6e371d32fe4ee76ae6c3360e228053b43d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42690084"
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2-getinterceptcookie).  
  
Wywołuje się, gdy przetwarzanie przechwycone wyjątku zostało zakończone.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetInterceptCookie(  
   UINT64* pqwCookie  
);  
```  
  
```csharp  
int GetInterceptCookie(  
   out ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pqwCookie`  
 [out] Unikatowa wartość, która jest skojarzona z wyjątku, który został przechwycony.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Po [interceptcurrentexception —](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) metoda zakończeniu obsługi wyjątku przechwycone wysyła [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) zdarzeń. Można użyć programu obsługi `GetInterceptCookie` metodę, która pobierze unikatową wartość skojarzony z wyjątkiem (taką samą wartość przekazywana do `InterceptCurrentException` metody).  
  
## <a name="see-also"></a>Zobacz też  
 [Interceptcurrentexception —](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)

