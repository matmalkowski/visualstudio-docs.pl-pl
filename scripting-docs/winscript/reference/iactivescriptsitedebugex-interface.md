---
title: Interfejs IActiveScriptSiteDebugEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cf5849ff1fca282bace97774c6b7ac9e4510226
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793627"
---
# <a name="iactivescriptsitedebugex-interface"></a>Interfejs IActiveScriptSiteDebugEx
Implementuje ten interfejs wraz z programem `IActiveScriptSiteDebug` interfejsu podczas pisania hosta, który ma uzyskać powiadomienie z informacją o błędów czasu wykonywania w aplikacji i opcjonalnie dołączyć do aplikacji do debugowania. Menedżer debugowania procesu zapewnia powiadomienie za pośrednictwem `IActiveScriptDebug` Jeśli debugera skryptów Just In Time znajduje się na komputerze. Jeśli debugera skryptów nie Just In Time został znaleziony, PDM zapewnia powiadomienie za pośrednictwem `IActiveScriptDebugEx` zamiast tego.  
  
 Aby uzyskać powiadomienie z informacją o błędów czasu wykonywania, host musi obsługiwać [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/en-us/cf7639f9-a699-4571-9f3a-82ef52c0b5f4). Oparte na akcję użytkownika, następnie można zdecydować, czy dołączyć debuger wewnętrzny i wrócić, czy zwracać uruchamiania w debugerze programu OnScriptErrorDebug `pfEnterDebugger` parametru.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Informuje, że host o błędów czasu wykonywania skryptu, gdy proces debugowania Manager nie znalazł zewnętrznego debugera tylko w czasie.|