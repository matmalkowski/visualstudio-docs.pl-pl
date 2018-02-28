---
title: IDebugEngine2::Attach | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fb45d2196a9f84b8f956b8ede665df6e3ed249c2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Dołącza aparat debugowania (DE), programów lub programu. Wywoływane przez menedżera sesji debugowania (SDM), gdy DE jest uruchomiony w procesie do SDM.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```csharp  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProgram`  
 [in] Tablica [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekty reprezentujące programy jest dołączony do. Są to programy portu.  
  
 `rgpProgramNodes`  
 [in] Tablica [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) obiekty reprezentujące węzłów programu, po jednej dla każdego programu. Węzły programu tej tablicy reprezentują te same programy, podobnie jak w `pProgram`. Węzły programu podano tak, aby DE można zidentyfikować programy do dołączenia do.  
  
 `celtPrograms`  
 [in] Liczba programów i/lub program węzłów w `pProgram` i `rgpProgramNodes` tablic.  
  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) obiekt używany do wysyłania zdarzeń debugowania do SDM.  
  
 `dwReason`  
 [in] Wartość z zakresu od [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) wyliczenie określający przyczynę dołączanie tych programów. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Istnieją trzy ze względu na dołączenie do programu, w następujący sposób:  
  
-   `ATTACH_REASON_LAUNCH`Wskazuje, że DE jest dołączania do programu, ponieważ użytkownik uruchomić proces, który go zawiera.  
  
-   `ATTACH_REASON_USER`Wskazuje, że użytkownik zażądał jawnie DE, aby dołączyć do programu (lub proces, który zawiera program).  
  
-   `ATTACH_REASON_AUTO`Wskazuje, że DE jest dołączenie do określonego programu, ponieważ jest on już debugowania innych programów w danym procesie. Jest to również automatyczne dołączanie.  
  
 Gdy ta metoda jest wywoływana, DE musi wysłać tych zdarzeń w sekwencji:  
  
1.  [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (Jeśli nie został już został wysłany do konkretnego wystąpienia aparatu debugowania)  
  
2.  [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3.  [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
 Ponadto, jeśli Przyczyna dołączanie `ATTACH_REASON_LAUNCH`, DE musi wysłać [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) zdarzeń.  
  
 Raz pobiera DE [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) obiekt odpowiadający debugowany, program może być badana dla dowolnego interfejsu prywatnego.  
  
 Przed wywołaniem metody węzła programu w tablicy przez `pProgram` lub `rgpProgramNodes`, personifikacja, jeśli jest to wymagane, powinna być włączona na `IDebugProgram2` interfejs, który reprezentuje węzeł programu. Zwykle jednak ten krok nie jest konieczne. Aby uzyskać więcej informacji, zobacz [problemy z zabezpieczeniami](../../../extensibility/debugger/security-issues.md).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)