---
title: IDebugProcess2::EnumThreads | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 786a3b4b5988b66e1fccc624154eeef67285ec84
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116698"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
Pobiera listę wszystkie wątki uruchomione w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Zwraca [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) obiekt, który zawiera listę wszystkich wątków w wszystkie programy w procesie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wylicza wątki uruchomione w każdym program i łączy je do widoku wątków procesu. Pojedynczy wątek może działać w wielu programach; Ta metoda wylicza wątek tylko raz.  
  
 Ta metoda Wyświetla listę wątków procesu bez duplikaty. W przeciwnym razie wyliczyć wątki uruchomione w szczególności program, użyj [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)