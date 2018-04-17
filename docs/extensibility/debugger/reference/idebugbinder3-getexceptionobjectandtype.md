---
title: IDebugBinder3::GetExceptionObjectAndType | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 519281487e85ec7dffc0e7bb470d044dc2bae885
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Ta metoda pobiera wyjątku skojarzonego z obiektem, jeśli istnieje.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```csharp  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppException`  
 [out] Zwraca obiekt reprezentujący wyjątek.  
  
 `ppField`  
 [out] Zwraca obiekt reprezentujący określonego pola, którego może spowodować wyjątek (może to być wartość null).  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
> [!NOTE]
>  Aby sprawdzić, czy jest to wyjątek, sprawdź wartość zwrócona przez `ppException`: Jeśli jest to wartość null, a następnie wyjątku nie jest skojarzony z tym obiektem.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)