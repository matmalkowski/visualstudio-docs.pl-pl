---
title: IDebugReference2::GetDerivedMostReference | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fa6c15c59a025f4b031765b620083b7b3369c7c8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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