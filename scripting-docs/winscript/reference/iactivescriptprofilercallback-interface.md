---
title: Interfejs IActiveScriptProfilerCallback | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4dc4b9d4e3b1f83a37e64e3a85387fd378d3ca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793459"
---
# <a name="iactivescriptprofilercallback-interface"></a>Interfejs IActiveScriptProfilerCallback
Udostępnia metody, które są używane przez aparat skryptów do powiadamiania obiektu profilera po wystąpieniu zdarzenia. Ten interfejs jest implementowany przez obiekt profilera.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Wywoływana w celu zainicjowania obiektu profilera po każdym uruchomieniu profilowania na aparatu skryptów.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Wywołuje się, by Zwolnij i zwolnij obiektu profilera zawsze, gdy profilowania jest zatrzymana na aparatu skryptów.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Powiadamia profilera dla obiekt, który aparat skryptów skompilowany skrypt.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Powiadamia profilera dla obiekt, który aparat skryptów napotkał funkcji podczas kompilowania skryptu.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Powiadamia obiektu profilera, które ma wykonać wywołania funkcji, która nie jest wywołaniem do modelu DOM (Document Object) aparatu skryptów.|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Powiadamia profilera obiektu czy zakończono wykonywanie funkcji aparatu skryptów wywołaniu, które nie jest wywołaniem do modelu DOM.|  
  
## <a name="remarks"></a>Uwagi  
 Powiadomienie o wywołania funkcji do modelu DOM (Document Object) są dostarczane przez [interfejs IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
>  Aby dodać możliwości do uruchamiania i zatrzymywania profilowania po uruchomieniu skryptu, wywołaj następujące metody. Za pomocą tych metod, można uzyskać stosu wywołań pełną, jeśli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] jest uruchomiona, uruchomienie lub zatrzymanie profilowania.  
>   
>  -   Wywołanie [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) powiadomiono profilera rozpoczęto profilowanie.  
> -   Wywołanie [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) powiadomiono profilera zostanie wkrótce zatrzymania profilowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilera aktywnego skryptu](../../winscript/reference/active-script-profiler-interfaces.md)