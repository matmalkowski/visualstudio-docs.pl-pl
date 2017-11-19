---
title: IDebugAlias::GetICorDebugValue | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAlias::GetICorDebugValue
helpviewer_keywords: IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 603f24f89463b9eb9f7c67ed3d05662870e41bf3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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