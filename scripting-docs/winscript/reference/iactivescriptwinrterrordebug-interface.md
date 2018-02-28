---
title: Interfejs IActiveScriptWinRTErrorDebug | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug Interface
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 34fcc4f1dc3ebc21f9303ba49f1709f2d023a29a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptwinrterrordebug-interface"></a>Interfejs IActiveScriptWinRTErrorDebug
Zaimplementowane przez aparat JavaScript, aby zapewnić rozszerzone informacje o błędzie środowiska wykonawczego systemu Windows z [wyliczenie BREAKREASON](../../winscript/reference/breakreason-enumeration.md) zdarzeń. Możliwość QueryInterface go z [IActiveScriptError](../../winscript/reference/iactivescripterror.md) obiektu.  
  
> [!IMPORTANT]
>  Interfejs jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="methods"></a>Metody  
 `IActiveScriptWinRTErrorDebug` Interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|Zwraca możliwości identyfikatora SID dla błąd środowiska uruchomieniowego systemu Windows, jeśli jest dostępna.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|Zwraca środowiska uruchomieniowego systemu Windows ograniczony ciąg odwołania błędu, jeśli jest dostępna.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|Zwraca środowiska uruchomieniowego systemu Windows ograniczony ciąg błędu, jeśli jest dostępna.|