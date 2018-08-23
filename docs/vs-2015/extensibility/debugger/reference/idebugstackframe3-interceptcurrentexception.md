---
title: IDebugStackFrame3::InterceptCurrentException | Dokumentacja firmy Microsoft
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
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80bb98c22ecd220b4dbb8d817eb8bad6351e37bc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678446"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugStackFrame3::InterceptCurrentException](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception).  
  
Jest wywoływana przez debuger w bieżącej ramki stosu, gdy chce przechwycić bieżący wyjątek.  
  
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
 [out] Unikatowa wartość identyfikujący określony wyjątek.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
 Poniżej przedstawiono najbardziej typowe zwraca błąd.  
  
|Błąd|Opis|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Nie można przechwytywać bieżący wyjątek.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Bieżąca ramka wykonanie nie zostało jeszcze przeszukiwane obsługi.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Ta metoda nie jest obsługiwana dla tej ramki.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy wyjątek jest zgłaszany, debuger przejmie kontrolę, w czasie wykonywania w kluczowych punktach podczas procesu obsługi wyjątków. Podczas tych kluczowymi momentami debugera można zadawać bieżącej ramki stosu Jeśli ramki chce, aby przechwycić wyjątek. W ten sposób przechwycone wyjątek jest przede wszystkim na bieżąco aparatu obsługi wyjątków ramkę stosu, nawet jeśli tej ramki stosu nie ma obsługi wyjątków (na przykład bloku try/catch w kodzie programu).  
  
 Gdy debuger chce wiedzieć, jeśli wyjątek powinien zostać przechwycone, wywołuje tę metodę w bieżącym obiekcie ramki stosu. Ta metoda jest odpowiedzialna za obsługę wszystkich szczegółów wyjątku. Jeśli [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) nie zaimplementowano interfejsu lub `InterceptStackException` metoda zwraca wszelkie błędy, a następnie Debuger kontynuuje normalne przetwarzanie wyjątku.  
  
> [!NOTE]
>  Wyjątki mogą zostać przechwycone tylko w kodzie zarządzanym, oznacza to, gdy debugowanego jest uruchomiona w ramach platformy .NET, w czasie wykonywania. Oczywiście można zaimplementować implementacji języka innych firm `InterceptStackException` w ich własnych silniki debugowania, jeśli dokonają takiego wyboru.  
  
 Po zakończeniu przechwytywaniu [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) jest sygnalizowane.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)

