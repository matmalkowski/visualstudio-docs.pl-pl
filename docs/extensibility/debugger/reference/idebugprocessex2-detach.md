---
title: IDebugProcessEx2::Detach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0423ae28bfee6e9acf10e2a9682e58a973c37d70
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Ta metoda informuje procesu, czy sesja jest już debugowania procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSession`  
 [in] Wartość, która unikatowo identyfikuje sesję, aby odłączyć ten proces z.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Przekazany interfejs `pSession` jest traktowane jako plik cookie wartość, która unikatowo identyfikuje Menedżera sesji debugowania, który pierwotnie dołączony do tego procesu; żadna z metod interfejsu podany nie ma funkcjonalnych.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)