---
title: IDebugProgramPublisher2::UnpublishProgram | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords: IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 14fd0c09d9a654e8d8ff7097a8974142f0317901
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Powoduje, że program jest niedostępny do debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT UnpublishProgram(  
   IUnknown* pDebuggeeInterface  
);  
```  
  
```csharp  
int UnpublishProgram(  
   object pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pDebuggeeInterface`  
 [in] `IUnknown` Interfejs do programu. To jest taka sama wartość dostarczony do [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) — metoda i unikatowo identyfikuje program usuwana (to znaczy, że jest używany jako plik cookie).  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Aby udostępnić program aparatami debugowania i Menedżera sesji debugowania, należy użyć [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)