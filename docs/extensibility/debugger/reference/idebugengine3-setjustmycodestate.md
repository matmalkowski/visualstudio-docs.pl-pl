---
title: IDebugEngine3::SetJustMyCodeState | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fda672cc9d6861520b9da3a894b94d51f4100683
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Ta metoda określa, że aparat debugowania o JustMyCode informacje o stanie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fUpdate`  
 [in] Różna od zera (`TRUE`) aby zaktualizować aktualne informacje, zero (`FALSE`) do resetowania wszystkich informacji (nie dotyczy żadnych wcześniej ustawione).  
  
 `dwModules`  
 [in] Liczba struktur informacji w `rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in] Tablica [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) struktury do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 JustMyCode to pojęcie debugowania tylko kodu, który należy do użytkownika i ignoruje wszystkie pośrednie kodu na przykład kod systemu — nawet, jeśli kod źródłowy jest niedostępny dla tego kodu systemu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)