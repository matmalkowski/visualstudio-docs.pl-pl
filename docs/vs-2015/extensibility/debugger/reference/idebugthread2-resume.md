---
title: IDebugThread2::Resume | Dokumentacja firmy Microsoft
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
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a3591ff3363a267b65c41093b18ff8d3ed154d6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679262"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugThread2::Resume](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugthread2-resume).  
  
Wznawia wykonanie wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwSuspendCount`  
 [out] Zwraca wstrzymania liczenia przez operację wznawiania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Każdy wywołanie tej metody zmniejsza wstrzymania liczenia aż do napotkania 0 w tym czasie faktycznie wznowiono wykonywanie. Ten licznik Wstrzymaj jest wyświetlana w **wątków** okna debugowania.  
  
 Dla każdego wywołania tej metody musi być poprzednie wywołanie [Wstrzymaj](../../../extensibility/debugger/reference/idebugthread2-suspend.md) metody. Wstrzymania liczenia Określa, ile razy `IDebugThread2::Suspend` do tej pory została wywołana metoda.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Wstrzymywanie](../../../extensibility/debugger/reference/idebugthread2-suspend.md)

