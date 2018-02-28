---
title: IDebugProgramEx2::GetProgramNode | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 1545ffbf-1422-4b5d-9bb9-314ba8665041
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a0d4f697bff8d46bbfb856441034a379796b9851
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramex2getprogramnode"></a>IDebugProgramEx2::GetProgramNode
Pobiera węzeł program skojarzony z programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetProgramNode(   
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```csharp  
int GetProgramNode(   
   out IDebugProgramNode2 ppProgramNode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppProgramNode`  
 [out] Zwraca [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) obiekt, który reprezentuje węzeł program skojarzony z tym programem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)