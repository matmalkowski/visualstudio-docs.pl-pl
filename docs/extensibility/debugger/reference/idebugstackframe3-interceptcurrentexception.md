---
title: IDebugStackFrame3::InterceptCurrentException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords: IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9631f2206705ef6daf36b355aa6cb1d5be6458d4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Wywoływane przez debuger na bieżącej ramki stosu, gdy chce się przechwycić bieżącego wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```csharp  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFlags`  
 [in] Określa różne akcje. Obecnie tylko [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) wartość `IEA_INTERCEPT` jest obsługiwana i musi być określona.  
  
 `pqwCookie`  
 [out] Unikatowa wartość identyfikujący określonego wyjątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
 Poniżej przedstawiono najbardziej typowe zwraca błąd.  
  
|Błąd|Opis|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Bieżący wyjątek nie może zostać przechwycony.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Bieżąca ramka wykonywania nie jeszcze przeszukiwane obsługi.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Ta metoda nie jest obsługiwana dla tej ramki.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy jest zgłaszany wyjątek, debuger uzyska kontrolę w czasie wykonywania w punktach klucza podczas procesu obsługi wyjątków. Podczas tych kluczy momentach debuger poproś bieżącej ramki stosu, jeśli ramki chce przechwycenia wyjątek. W ten sposób przechwycone wyjątek jest zasadniczo obsługi wyjątków na bieżąco ramki stosu, nawet jeśli tą ramką stosu nie ma obsługi wyjątków (na przykład blok try/catch w kodzie programu).  
  
 Gdy debuger chce wiedzieć, jeśli wyjątek powinien zostać przechwycone, wywołuje tę metodę w bieżącym obiekcie ramki stosu. Ta metoda jest odpowiedzialna za obsługę wszystkie szczegóły wyjątku. Jeśli [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) interfejsu nie jest zaimplementowana lub `InterceptStackException` metoda zwraca wszelkie błędy, a następnie debuger nadal normalnie przetwarzania wyjątek.  
  
> [!NOTE]
>  Wyjątki mogą zostać przechwycone tylko w kodzie zarządzanym, oznacza to, gdy debugowany program działa w ramach wykonawczego platformy .NET. Oczywiście można zaimplementować implementacje języka innych firm `InterceptStackException` w ich własnych aparatami debugowania, gdy wybiera on.  
  
 Po zakończeniu zatrzymania [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) zostanie zasygnalizowane.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)