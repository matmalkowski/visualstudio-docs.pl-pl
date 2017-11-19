---
title: Interfejs IActiveScriptDebug | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptDebug interface
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1e1d0c1cf51c63f1bb3fcd90ae72520da907e50
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebug-interface"></a>Interfejs IActiveScriptDebug
Implementowana przez aparatów skryptów, w tym obsługi debugowania. Zazwyczaj obiekt, który implementuje `IActiveScriptDebug` również interfejs implementuje `IActiveScript` interfejsu. Jeśli jest to możliwe, należy wywołać `IActiveScript::QueryInterface` metodę, aby uzyskać `IActiveScriptDebug` interfejsu.  
  
 `IActiveScriptDebug` Interfejsu udostępnia środki do:  
  
-   Hostów inteligentnych na przejęcie zarządzania dokumentu.  
  
-   Menedżera debugowania procesu synchronizacji debugowania z wielu aparatów skryptów.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IActiveScriptDebug` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|Zwraca atrybuty tekstu dla dowolnego bloku skryptu tekstu.|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|Zwraca atrybuty tekstu dla dowolnego skryptlet.|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|Deleguje do `IDebugDocumentContext::EnumCodeContexts`.|