---
title: Interfejs IActiveScriptProfilerCallback2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dc9fcd8ca4afec0fb474c0f3a7317b608c7c9f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793486"
---
# <a name="iactivescriptprofilercallback2-interface"></a>Interfejs IActiveScriptProfilerCallback2
Udostępnia metody, które są używane przez aparat skryptów do powiadamiania obiektu profilera po wystąpieniu zdarzenia modelu DOM (Document Object). Ten interfejs jest implementowany przez obiekt profilera.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Powiadamia obiekt profilera, który będzie aparat skryptów do uruchomienia wywołanie funkcji modelu DOM.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Powiadamia profilera dla obiekt, który aparat skryptów zamknięte DOM wywołania funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 `IActiveScriptProfilerCallback2` Interfejsu pierwszy z programu Internet Explorer 9.  
  
 Powiadomienia o wywołania funkcji, które nie są wywołaniami do modelu DOM jest zapewniana przez [interfejs IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
>  Aby dodać możliwości do uruchamiania i zatrzymywania profilowania po uruchomieniu skryptu, wywołaj następujące metody. Za pomocą tych metod, można uzyskać stosu wywołań pełną, jeśli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] jest uruchomiona, uruchomienie lub zatrzymanie profilowania.  
>   
>  -   Wywołanie [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) powiadomiono profilera rozpoczęto profilowanie.  
> -   Wywołanie [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) powiadomiono profilera zostanie wkrótce zatrzymania profilowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilera aktywnego skryptu](../../winscript/reference/active-script-profiler-interfaces.md)