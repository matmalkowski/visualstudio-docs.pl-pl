---
title: IDebugProcess2::CauseBreak | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::CauseBreak
helpviewer_keywords: IDebugProcess2::CauseBreak
ms.assetid: efda8865-2319-4d53-90bf-6d9d74cd5195
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 99047f7703f39a04049162686079ed26ad9b30f8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess2causebreak"></a>IDebugProcess2::CauseBreak
Żądania następnej program jest uruchomiony kod w tym procesie zatrzymanie i wysyłać [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) obiekt zdarzenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CauseBreak(   
   void  
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)