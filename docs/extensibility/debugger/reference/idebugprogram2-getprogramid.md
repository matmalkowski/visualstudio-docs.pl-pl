---
title: IDebugProgram2::GetProgramId | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::GetProgramId
helpviewer_keywords: IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 094dde4330775b77a50ce98451fc9dafcd3bd23b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Pobiera identyfikator GUID dla tego programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetProgramId(   
   GUID* pguidProgramId  
);  
```  
  
```csharp  
int GetProgramId(   
   out Guid pguidProgramId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pguidProgramId`  
 [out] Zwraca `GUID` dla tego programu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Aparat debugowania (DE) musi zwracać identyfikatora programu oryginalnie przekazana do [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) lub [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metody. Dzięki temu identyfikacji programu przez debuger składników.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)