---
title: IDebugProgramNodeAttach2::OnAttach | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords: IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a6b0f74ef5b14fb9e8971c0d539cc2e875658341
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Dołącza do skojarzonego programu lub różni się proces attach [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```csharp  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidProgramId`  
 [in] `GUID` można przypisać do skojarzonego programu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) nie można wywołać metody. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana podczas procesu dołączania przed [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metoda jest wywoływana. `OnAttach` Metodę można wykonać sam proces attach (w takim przypadku ta metoda zwraca `S_FALSE`) lub odroczenie proces attach `IDebugEngine2::Attach` — metoda ( `OnAttach` metoda zwraca `S_OK`). W obu przypadkach `OnAttach` można ustawić metody `GUID` programu debugowanego danego `GUID`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)