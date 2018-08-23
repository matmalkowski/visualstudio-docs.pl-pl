---
title: IDebugObject::GetManagedDebugObject | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 60ca763d11bf0a095569350f06fd4e14df876cb6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42632055"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugObject::GetManagedDebugObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject-getmanageddebugobject).  
  
Tworzy kopię obiektu zarządzanego w przestrzeni adresowej aparatu debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```csharp  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppObject`  
 [out] Zwraca [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) obiekt reprezentujący nowo utworzonego obiektu zarządzanego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu. Zwraca E_FAIL, jeśli [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nie reprezentuje wystąpienie klasy zarządzanej wartości.  
  
## <a name="remarks"></a>Uwagi  
 To [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiektu musi reprezentować wartość zarządzanego wystąpienia klasy, takie jak `System.Decimal` wystąpienia. Dzięki kopii lokalnej obciążenie związane z wywołaniem [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) wyeliminowania.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)

