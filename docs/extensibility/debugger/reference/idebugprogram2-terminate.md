---
title: IDebugProgram2::Terminate | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::Terminate
helpviewer_keywords: IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fea9b99fc597a75e93392b14fe40a1be87072602
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Kończy program.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli to możliwe program zostanie zakończony i zwolniona z procesu; w przeciwnym razie aparat debugowania (DE) będzie wykonywać żadnych cleanup konieczne.  
  
 Ta metoda lub [przerwania](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) metoda jest wywoływana przez środowisko IDE, zwykle w odpowiedzi na użytkownika zatrzymywanie debugowania wszystkie. Implementacja tej metody należy zakończyć w idealnym przypadku program w ramach procesu. Jeśli nie jest to możliwe, DE należy uniemożliwić uruchamianie więcej w tym procesie programu (i wykonanie oczyszczania konieczne). Jeśli `IDebugProcess2::Terminate` wywołano metodę IDE, cały proces zostanie zakończony pewnego czasu po `IDebugProgram2::Terminate` metoda jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Zakończenie](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)