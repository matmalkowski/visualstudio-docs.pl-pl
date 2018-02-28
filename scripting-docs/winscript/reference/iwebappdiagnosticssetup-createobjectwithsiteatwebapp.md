---
title: IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1442297fcacb3a9464f9ea67489c91c8ab64ad78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Ta metoda tworzy wspólnie klasy o identyfikatorze przekazać przy użyciu `rclsid` przy użyciu `dwClsContext`. Jest to w sposób podobny do [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) działa, chyba że w przypadku elementu `CreateObjectWithSiteAtWebApp` obiekt jest tworzony asynchronicznie w wątku interfejsu użytkownika aplikacji sieci web. Obiekt określony przez identyfikator klasy należy zaimplementować [interfejs IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). Po utworzeniu obiektu [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) jest wywoływana z odwołaniem do debugowania aplikacji PDM i `hPassToObject` parametr `CreateObjectWithSiteAtWebApp`. Ta metoda służy do przekazania do aplikacji dojścia do anonimowego potoku, która została skopiowana przy użyciu [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450).  
  
> [!IMPORTANT]
>  [Interfejs IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) jest implementowany przez PDM v11.0 i większa. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>Parametry  
 `rclsid`  
 Identyfikator klasy klasy do utworzenia.  
  
 `dwClsContext`  
 Kontekst, w którym będzie uruchamiany kod. W większości przypadków jest CLSCTX_INPROC_SERVER.  
  
 `riid`  
 Nie używany.  
  
 `hPassToObject`  
 Wartość, która zostanie przekazany do obiektu utworzone w wątku interfejsu użytkownika, jeśli obiekt implementuje [interfejs IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).