---
title: IDebugEngineLaunch2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b4f70dac4d8831b02e458be3b8b4e38e5703b5d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679584"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugEngineLaunch2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugenginelaunch2).  
  
Używane przez aparat debugowania (DE) do uruchomienia, a następnie Zakończ działanie programów.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez niestandardowe DE, jeśli ma on specjalnych wymagań co do uruchamiania procesu, który nie może być obsługiwane wyłącznie przez port niestandardowy. Jest to typowe w przypadku, gdy DE jest częścią tłumacza debugowanego procesu jest skryptem: interpreter musi być uruchamiany najpierw, a następnie załadować i uruchomić skrypt. Port można uruchomić interpretera, ale skrypt mogą wymagać specjalnej obsługi, (czyli gdzie DE rolę). Ten interfejs jest implementowany tylko wtedy, gdy istnieją unikatowe wymagania dotyczące uruchamiania programu, który nie może obsługiwać port niestandardowy.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest wywoływana przez Menedżer debugowania sesji (SDM) Jeśli SDM znajdziesz ten interfejs z [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfejs (przy użyciu funkcji QueryInterface). Jeśli ten interfejs można uzyskać, SDM wie, że Niemcy ma specjalne wymagania i wywołuje ten interfejs, aby uruchomić program zamiast port, uruchom ją.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugEngineLaunch2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Uruchamia proces, za pomocą DE.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Wznawia wykonanie procesu.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Określa, proces może zostać zakończone.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Kończy proces.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

