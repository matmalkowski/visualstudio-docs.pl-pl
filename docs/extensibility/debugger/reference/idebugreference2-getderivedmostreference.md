---
title: IDebugReference2::GetDerivedMostReference | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cfa0e6b6755ea884b6dd9b6ba0409a614e80e290
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Pobiera odwołanie pochodzi większość odwołania. Zarezerwowane do użytku w przyszłości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetDerivedMostReference(   
   IDebugReference2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostReference(   
   out IDebugReference2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppDerivedMost`  
 [out] Zwraca [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) obiekt, który reprezentuje właściwość najbardziej pochodnej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca `E_NOTIMPL`.  
  
## <a name="remarks"></a>Uwagi  
 Na przykład, jeśli ta właściwość określa obiekt, który implementuje `ClassRoot` , lecz faktycznie instancją typu `ClassDerived` która pochodzi z `ClassRoot`, a następnie ta metoda zwraca [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) obiektu Odwołanie do reprezentujący `ClassDerived` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)