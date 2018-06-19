---
title: Interfejs IActiveScriptProfilerControl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0d598302ae78ca0b2a1e7c1f94c949800378a2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793495"
---
# <a name="iactivescriptprofilercontrol-interface"></a>Interfejs IActiveScriptProfilerControl
Wykonywane przez aparat skryptów, który obsługuje profilowania. Zazwyczaj obiekt, który implementuje `IActiveScriptProfilerControl` implementuje również [IActiveScript](../../winscript/reference/iactivescript.md) interfejsu. W takim przypadku można uzyskać dojścia do `IActiveScriptProfilerControl` interfejsu, wywołując `IUnknown::QueryInterface` metody dla obiekt. Interfejs zawiera metody niezbędne do zatrzymywania i uruchamiania profilowania na aparatu skryptów.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Uruchamia profilowanie na aparatu skryptów.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Umożliwia ustawienie maski zdarzeń profilera w aparatu skryptów.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Zatrzymuje profilowanie na aparatu skryptów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilera aktywnego skryptu](../../winscript/reference/active-script-profiler-interfaces.md)