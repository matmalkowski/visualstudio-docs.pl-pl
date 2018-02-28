---
title: IDebugAlias::GetICorDebugValue | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4e23641f246d064dc65c01788bdfb780c0f09869
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Pobiera interfejs kodu zarządzanego, który reprezentuje wartość skojarzoną z tego aliasu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppUnk`  
 [out] `IUnknown` interfejs, który reprezentuje wartość skojarzoną z tego aliasu. Ten interfejs może być badana dla `ICorDebugValue` interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda ma zastosowanie tylko do zarządzanych wartości ( `ICorDebugValue` jest dostępna w interfejsie [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] i jest zdefiniowany w [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] zestawu SDK w pliku cordebug.idl).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)