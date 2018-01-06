---
title: IDebugPointerObject::Dereference | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPointerObject::Dereference
helpviewer_keywords: IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3e743f5a312e437ca48a5e36fb202783f41b934d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Pobiera obiekt wskazywał.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwIndex`  
 [in] Przesunięcie bajtów proste, od początku obiektu wskazywał.  
  
 `ppObject`  
 [out] Zwraca [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiekt reprezentujący obiekt wskazywał plus przesunięcia, jeśli istnieje.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu. Zwraca E_FAIL, jeśli ten obiekt nie wskazuje innego obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt wskazywał może być typu pierwotnego lub typem bardziej złożonych, takich jak klasy lub struktury.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)