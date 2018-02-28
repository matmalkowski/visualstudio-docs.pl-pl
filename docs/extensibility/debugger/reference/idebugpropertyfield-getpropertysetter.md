---
title: IDebugPropertyField::GetPropertySetter | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPropertyField::GetPropertySetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertySetter method
ms.assetid: 744d76fd-2bcc-4917-a040-ce4cc714ef61
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ef75352e971753887afb960b47a751031b4ea5a7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpropertyfieldgetpropertysetter"></a>IDebugPropertyField::GetPropertySetter
Pobiera metodę ustawiającą właściwość.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetPropertySetter(   
   IDebugMethodField** ppField  
);  
```  
  
```csharp  
int GetPropertySetter(  
   out IDebugMethodField ppField  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppField`  
 [out] Zwraca [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) obiekt reprezentujący metodę ustawiającą właściwość.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Aby pobrać metodę, która pobiera właściwość, należy wywołać [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)