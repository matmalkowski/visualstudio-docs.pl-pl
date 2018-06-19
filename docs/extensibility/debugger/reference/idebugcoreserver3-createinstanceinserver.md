---
title: IDebugCoreServer3::CreateInstanceInServer | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 71995e38cf58c23437cbb9a6d6973fbd09cab8ab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105849"
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