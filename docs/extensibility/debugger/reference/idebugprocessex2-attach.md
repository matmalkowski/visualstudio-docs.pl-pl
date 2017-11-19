---
title: IDebugProcessEx2::Attach | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcessEx2::Attach
helpviewer_keywords: IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 111895b73ee9685b9608be9812452d04d84cd48c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Ta metoda informuje proces czy sesji jest teraz debugowania procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Attach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Attach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSession`  
 [in] Wartość, która unikatowo identyfikuje sesji dołączenie do tego procesu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Przekazany interfejs `pSession` powinien być traktowany jako plik cookie, który unikatowo identyfikuje Menedżera debugowania sesji dołączenie do tego procesu; wartość żaden z metod interfejsu podany nie jest funkcjonalności.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)