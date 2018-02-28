---
title: IDebugEngineLaunch2::LaunchSuspended | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b9c05a566c62df63ebabebab287188011e4f1ca5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Ta metoda uruchamia proces, za pomocą aparatu debugowania (DE).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT LaunchSuspended (   
   LPCOLESTR             pszMachine,  
   IDebugPort2*          pPort,  
   LPCOLESTR             pszExe,  
   LPCOLESTR             pszArgs,  
   LPCOLESTR             pszDir,  
   BSTR                  bstrEnv,  
   LPCOLESTR             pszOptions,  
   LAUNCH_FLAGS          dwLaunchFlags,  
   DWORD                 hStdInput,  
   DWORD                 hStdOutput,  
   DWORD                 hStdError,  
   IDebugEventCallback2* pCallback,  
   IDebugProcess2**      ppDebugProcess  
);  
```  
  
```csharp  
int LaunchSuspended(  
   string               pszServer,   
   IDebugPort2          pPort,   
   string               pszExe,   
   string               pszArgs,   
   string               pszDir,   
   string               bstrEnv,   
   string               pszOptions,   
   enum_LAUNCH_FLAGS    dwLaunchFlags,   
   uint                 hStdInput,   
   uint                 hStdOutput,   
   uint                 hStdError,  
   IDebugEventCallback2 pCallback,   
   out IDebugProcess2   ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszMachine`  
 [in] Nazwa komputera, w którym można uruchomić procesu. Użyj wartości null, aby określić komputer lokalny.  
  
 `pPort`  
 [in] [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfejs reprezentujący port, którego program ma być uruchamiany w.  
  
 `pszExe`  
 [in] Nazwa pliku wykonywalnego do uruchomienia.  
  
 `pszArgs`  
 [in] Argumenty do przekazania do pliku wykonywalnego. Może być wartością null, jeśli nie wymaga argumentów.  
  
 `pszDir`  
 [in] Nazwa katalogu roboczego używane przez plik wykonywalny. Może być wartością null, jeśli katalog roboczy nie jest wymagane.  
  
 `bstrEnv`  
 [in] Blok środowiska ciągi zakończone wartością NULL, następuje dodatkowe terminatorem NULL.  
  
 `pszOptions`  
 [in] Opcje dla pliku wykonywalnego.  
  
 `dwLaunchFlags`  
 [in] Określa [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) sesji.  
  
 `hStdInput`  
 [in] Dojście do alternatywnego strumienia wejściowego. Może być 0, jeśli przekierowanie nie jest wymagana.  
  
 `hStdOutput`  
 [in] Dojście do strumienia wyjściowego alternatywny. Może być 0, jeśli przekierowanie nie jest wymagana.  
  
 `hStdError`  
 [in] Dojście do strumienia wyjściowego błąd alternatywny. Może być 0, jeśli przekierowanie nie jest wymagana.  
  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) obiekt, który odbiera zdarzenia debugera.  
  
 `ppDebugProcess`  
 [out] Zwraca powstałe w ten sposób [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) obiekt, który reprezentuje uruchomionego procesu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zwykle [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uruchamia program używając [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) — metoda, a następnie dołącza debuger do programu zawieszone. Istnieją jednak okoliczności, w których trzeba uruchomić program (na przykład, jeśli aparat debugowania jest częścią tłumacza, a program debugowany jest interpretowany język), w którym to przypadku aparat debugowania [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] używa `IDebugEngineLaunch2::LaunchSuspended` — metoda .  
  
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) metoda jest wywoływana, aby uruchomić proces po procesie została pomyślnie uruchomiona w stanie wstrzymania.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)