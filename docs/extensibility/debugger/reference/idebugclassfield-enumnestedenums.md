---
title: IDebugClassField::EnumNestedEnums | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ea28f2a455d3528f083ba2acb2e9e4ad8989319
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Tworzy moduł wyliczający dla zagnieżdżonej moduły wyliczające tej klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumNestedEnums(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumNestedEnums(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Zwraca [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt reprezentujący listę wyliczeń zagnieżdżonych. Zwraca wartość null, jeśli nie ma żadnych wyliczeń zagnieżdżonych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartości S_FALSE, jeśli nie ma żadnych zagnieżdżonych moduły wyliczające. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Każdy element wyliczenia jest [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) Obiekt opisujący zagnieżdżonych wyliczenia.  
  
 Wyliczenie zadeklarowana w klasie jest traktowany jako zagnieżdżony wyliczenia. Przykładowo podana:  
  
```  
class RootClass {  
   enum NestedEnum { EnumValue = 0 }  
};  
```  
  
 `EnumNestedEnums` Zwróci metoda [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt, który zawiera jeden [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) obiekt, który reprezentuje `NestedEnum` wyliczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)