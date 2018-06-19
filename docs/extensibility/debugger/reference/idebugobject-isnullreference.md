---
title: IDebugObject::IsNullReference | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a886bf56cfafc615099aa489f9d329229ea8727
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113711"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Sprawdza, czy ten obiekt jest odwołaniem o wartości zerowej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```csharp  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pfIsNull`  
 [out] Zwraca wartość inną niż zero (`TRUE`) Jeśli ten obiekt jest odwołanie o wartości null; w przeciwnym wypadku zwraca wartość zero (`FALSE`).  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Pusty obiekt lub obiekt, który nie został przypisany do, oznacza to odwołanie o wartości null.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)