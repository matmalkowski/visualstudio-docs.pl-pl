---
title: IDebugProcess2::Detach | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::Detach
helpviewer_keywords: IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c308dae9b324871f8604b6bedecf3d297f3eacd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
Odłącza debugera z tego procesu przez odłączenie wszystkich programów w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Detach(   
   void   
);  
```  
  
```csharp  
int Detach();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie programy, a proces nadal działać, ale nie są już częścią sesji debugowania. Po operacji odłączania jest pełna, ma więcej debugowania zdarzenia dla tego procesu (i jego programów) zostanie wysłany.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)