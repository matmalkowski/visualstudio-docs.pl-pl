---
title: IDebugArrayObject::GetElements | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae1d22af6796c2de72c763137c8f96feb7885407
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099818"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Pobiera moduł wyliczający wszystkie elementy tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```csharp  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Zwraca [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) obiekt, który umożliwia wyliczania przez wszystkie elementy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Alternatywnie, użyj [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) i [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) metody do iterowania po elementach.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)