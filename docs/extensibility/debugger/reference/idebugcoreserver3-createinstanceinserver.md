---
title: IDebugCoreServer3::CreateInstanceInServer | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: cbd287f5ab75374a3272ecbb34c36ffdf384ba84
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Tworzy wystąpienie aparatu debugowania na serwerze.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```csharp  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szDll`  
 [in] Ścieżka do pliku dll, który implementuje identyfikator CLSID określony w `clsidObject` parametru. Jeśli jest to `NULL`, następnie modelu COM `CoCreateInstance` funkcja jest wywoływana.  
  
 `wLangId`  
 [in] Ustawienia regionalne aparat debugowania. Może to być 0, jeśli [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) nie można wywołać metody.  
  
 `clsidObject`  
 [in] Identyfikator CLSID aparat debugowania do utworzenia.  
  
 `riid`  
 [in] Identyfikator interfejsu określonego interfejsu, aby pobrać z obiektu klasy.  
  
 `ppvObject`  
 [out] `IUnknown` interfejsu z wystąpień obiektu. Rzutowanie lub kierować tego obiektu do żądanego interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)