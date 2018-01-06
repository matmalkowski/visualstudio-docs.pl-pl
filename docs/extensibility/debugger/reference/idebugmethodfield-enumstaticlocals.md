---
title: IDebugMethodField::EnumStaticLocals | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField::EnumStaticLocals
helpviewer_keywords: IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0aa4a5e044dfc28302735e058c8863d4eb683670
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
Tworzy moduł wyliczający dla statycznych zmiennych lokalnych metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumStaticLocals(   
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumStaticLocals(  
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppLocals`  
 [out] Zwraca [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt reprezentujący listę statycznych zmiennych lokalnych. Zwraca wartość null, jeśli nie ma żadnych statycznych zmiennych lokalnych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartości S_FALSE, jeśli nie ma żadnych statycznych zmiennych lokalnych. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Każdy element jest [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiekt reprezentujący różnych typów statycznych zmiennych lokalnych. Wywołanie [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) metody dla każdego obiektu, aby określić dokładnie jakiego rodzaju statycznych lokalny obiekt reprezentuje.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)