---
title: IDebugProperty2::GetDerivedMostProperty | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords: IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ac691b8e1c2d28477eb8c07f760eae8909a9633
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Pobiera właściwość pochodnych większość właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppDerivedMost`  
 [out] Zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który reprezentuje właściwość najbardziej pochodnej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `S_GETDERIVEDMOST_NO_DERIVED_MOST` Jeśli nie ma właściwości najbardziej pochodnej do pobrania.  
  
## <a name="remarks"></a>Uwagi  
 Na przykład, jeśli ta właściwość określa obiekt, który implementuje `ClassRoot` , lecz faktycznie instancją typu `ClassDerived` która pochodzi z `ClassRoot`, a następnie ta metoda zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiektu opisujące `ClassDerived` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)