---
title: IDebugContainerField::EnumFields | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0af939253de7b592e7c0ec35be9ea2b9bbff2b0f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Tworzy moduł wyliczający dla pól kontenera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwKindFilter`  
 [in] Kombinację [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) stałe, które wybierz pola, które mają zostać wyliczone. Typy pól można opisać typów pamięci masowej, takich jak klasa lub pierwotnych lub określone informacje, takie jak lokalny, parametr lub wskaźnika "this".  
  
 `dwModifiersFilter`  
 [in] Kombinację [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) stałe, które wybierz pola, które mają zostać wyliczone. Modyfikatory pole może mieć uprawnienia dostępu, takich jak publicznych lub prywatnych lub magazynu informacje, takie jak wirtualne, statyczne lub końcowego.  
  
 `pszNameFilter`  
 [in] Nazwa pola, które mają zostać wyliczone. Może to być wartość null, jeśli wszystkie pola, które mają zostać zwrócone.  
  
 `nameMatch`  
 [in] Wartość z zakresu od [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) wyliczenia, która określa, czy wyszukiwanie jest rozróżniana wielkość liter, czy nie.  
  
 `ppEnum`  
 [out] Zwraca [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt reprezentujący listę pól. Zwraca wartość null, jeśli nie ma żadnych pól.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK lub S_FALSE, jeśli nie ma żadnych pól. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 `dwKindFilter`, `dwModifiersFilter`, I `pszNameFilter` parametrów można łączyć, na przykład, aby wybrać wszystkie metody wirtualne publicznej o nazwie "MyMethod".  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)