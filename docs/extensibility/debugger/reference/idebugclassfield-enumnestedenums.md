---
title: IDebugClassField::EnumNestedEnums | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::EnumNestedEnums
helpviewer_keywords: IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7667e21f57f3fc2844800e498d9519ddf9929f85
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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