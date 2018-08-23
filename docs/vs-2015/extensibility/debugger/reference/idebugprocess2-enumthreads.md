---
title: IDebugProcess2::EnumThreads | Dokumentacja firmy Microsoft
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
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30fb71dbb1fa6edbce9201cd757dd96f401f1e5e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679088"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugProcess2::EnumThreads](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocess2-enumthreads).  
  
Pobiera listę wszystkich wątków, uruchomiony w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 [out] Zwraca [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) obiektu, który zawiera listę wszystkich wątków we wszystkich programach w procesie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wylicza wątki uruchomione w każdym programie i łączy je w widoku proces wątków. Pojedynczy wątek może działać w wielu programach; Ta metoda wylicza wątek tylko raz.  
  
 Ta metoda Wyświetla listę wątków procesu bez duplikatów. W przeciwnym razie można wyliczyć wątki uruchomione w szczególności program, należy użyć [enumthreads —](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Enumthreads —](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)

