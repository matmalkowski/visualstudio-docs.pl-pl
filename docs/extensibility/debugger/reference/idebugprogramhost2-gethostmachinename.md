---
title: IDebugProgramHost2::GetHostMachineName | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramHost2::GetHostMachineName
helpviewer_keywords: IDebugProgramHost2::GetHostMachineName
ms.assetid: 4677ffe4-aa9b-4450-a63b-74cd3984d956
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 730b80f4d103770c556cd91ad4924ca8a81e826a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramhost2gethostmachinename"></a>IDebugProgramHost2::GetHostMachineName
Pobiera nazwę komputera, na którym uruchomiono proces obsługujący ten program.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetHostMachineName(   
   BSTR* pbstrHostMachineName  
);  
```  
  
```csharp  
int GetHostMachineName(   
   out string pbstrHostMachineName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrHostMachineName`  
 [out] Zwraca nazwę komputera.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)