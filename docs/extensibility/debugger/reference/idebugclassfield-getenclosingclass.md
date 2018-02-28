---
title: IDebugClassField::GetEnclosingClass | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 440b9845ae7f3dd57b34b4ce25f48bea3aaa7e80
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Pobiera klasę, która obejmuje tej klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppClassField`  
 [out] Zwraca [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) obiekt reprezentujący otaczającej klasy. Zwraca wartość null, jeśli nie otaczającą klasę.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli klasa reprezentowany przez to [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) obiekt jest klasą zagnieżdżoną, a następnie `ppClassField` zwraca parametr `IDebugClassField` obiekt reprezentujący otaczającej klasy. Przykładowo podana tej definicji klasy:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Wywoływanie `GetEnclosingClass` metoda `IDebugClassField` reprezentujący obiekt `NestedClass` klasy zwraca `IDebugClassField` obiekt reprezentujący klasę `RootClass`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)