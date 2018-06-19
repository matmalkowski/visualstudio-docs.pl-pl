---
title: IEEVisualizerDataProvider::SetObjectForVisualizer | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0d1a6272f8a04316c8695f301d5c45512b05f2d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120731"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Ta metoda zmienia obiekt, który reprezentuje wizualizatora.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```csharp  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pNewObject`  
 [in] Obiekt do ustawienia.  
  
 `error`  
 [out] Jeśli wystąpił błąd podczas ustawiania obiektu, ten ciąg zawiera komunikat o błędzie.  
  
 `pException`  
 [out] Jeśli wystąpił błąd, ten obiekt przechowuje informacje o wyjątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jest czynności, aby określić, jak informacje o błędzie jest zwracany. Jednak jest możliwe, że niektóre elementy wywołujące mogą tylko wyglądu, aby zobaczyć, jeśli obiekt wyjątku został zwrócony wiedzieć, były wystąpił błąd, dlatego ta metoda powinna zawsze zwraca obiekt wyjątku, jeśli wystąpił błąd. Ciąg błędu należy dostarczyć także, w przypadku, gdy obiekt wywołujący chce z niego korzystać.  
  
## <a name="see-also"></a>Zobacz też  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)