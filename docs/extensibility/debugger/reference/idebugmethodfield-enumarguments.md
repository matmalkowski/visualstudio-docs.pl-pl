---
title: IDebugMethodField::EnumArguments | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 515897838b2061a04479a69f5118f69a72e89f86
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Tworzy moduł wyliczający dla typu argumentu wymaganych do wywołania metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumArguments(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumArguments(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppParams`  
 [out] Zwraca [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt reprezentujący listę typy argumentów. Zwraca wartość null, jeśli nie wymaga argumentów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartości S_FALSE, jeśli nie wymaga argumentów. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Każdy element jest [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiekt reprezentujący typy każdego parametru. Wywołanie [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) metody do pobierania informacji o typie każdego parametru.  
  
 Jeśli nazwa parametru nie jest konieczne wraz z typem, następnie wywołaj [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)