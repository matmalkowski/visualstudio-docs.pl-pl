---
title: Interfejs IActiveScriptErrorDebug | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug interface
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ff2dda33c1e406f87a157173c41015acf96e62a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793318"
---
# <a name="iactivescripterrordebug-interface"></a>Interfejs IActiveScriptErrorDebug
Udostępnia informacje o kontekście dokumentu dla kompilacji błędy i wyjątki czasu wykonywania. `IActiveScriptError::QueryInterface` Metoda obsługuje `IActiveScriptErrorDebug` interfejsu.  
  
 Oprócz dziedziczone z metody `IActiveScriptError`, `IActiveScriptErrorDebug` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|Udostępnia kontekst dokumentu dla tego błędu.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|Udostępnia ramki stosu, które są włączone dla błędów czasu wykonywania.|