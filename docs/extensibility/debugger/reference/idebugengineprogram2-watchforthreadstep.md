---
title: IDebugEngineProgram2::WatchForThreadStep | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords: IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3ca2e5eff223a22a3359f6fc4a391d2102f31b67
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Oczekuje na wykonanie (lub zatrzymuje oczekiwania na wykonanie) występuje dla danego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```csharp  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pOriginatingProgram`  
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt reprezentujący ten program jest przeprowadził.  
  
 `dwTid`  
 [in] Określa identyfikator wątku, aby obejrzeć.  
  
 `fWatch`  
 [in] Niezerowa (`TRUE`) oznacza start oczekiwania na wykonanie wątku identyfikowane przez `dwTid`; w przeciwnym razie wartość zero (`FALSE`) oznacza, że zatrzymać oczekiwania na wykonanie na `dwTid`.  
  
 `dwFrame`  
 [in] Określa indeks ramki, który określa typ kroku. Gdy jest to wartość zero (0), typ kroku jest "Wkrocz" i program ma zostać zatrzymana, gdy wątek identyfikowane przez `dwTid` wykonuje. Gdy `dwFrame` jest różna od zera, typ kroku jest "Przekrocz nad" i programu należy zatrzymać tylko wtedy, gdy wątek identyfikowane przez `dwTid` działa w ramce, którego indeks jest równa lub wyższa na stosie niż `dwFrame`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Gdy Menedżer debugowania sesji (SDM) kroki programu identyfikowane przez `pOriginatingProgram` parametru, powiadomi wszystkie inne programy dołączone przez wywołanie tej metody.  
  
 Ta metoda ma zastosowanie tylko do tego samego wątku wykonywanie krok po kroku.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)