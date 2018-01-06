---
title: IDebugProcessEx2::AddImplicitProgramNodes | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords: IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: adc3f54188e57bd5453703c0aa68fe281fd2ca5e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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