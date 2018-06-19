---
title: IDebugProcessEx2::AddImplicitProgramNodes | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22f6cadaa88d6cc87ec70451d9da850cd49b7753
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31117023"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Ta metoda dodaje węzeł program dla każdego aparat debugowania (DE) określony.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```csharp  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidLaunchingEngine`  
 [in] `GUID` Z URZ, który ma być używany do uruchamiania programów (przyjęto, że można dodać własną węzłów program).  
  
 `rgguidSpecificEngines`  
 [in] Tablica `GUID`s DEs dla programu, które będzie można dodać węzłów.  
  
 `celtSpecificEngines`  
 [in] Liczba `GUID`s w `rgguidSpecificEngines` tablicy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 [Program węzłów](../../../extensibility/debugger/program-nodes.md) zostanie dodana dla każdego DE wymienionych w `rgguidSpecificEngines`— z wyjątkiem uruchamiania aparatu (podaną w `guidLaunchingEngine`), który zakłada się, że dodanie własne węzła program jest uruchamiany program.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Węzły programu](../../../extensibility/debugger/program-nodes.md)