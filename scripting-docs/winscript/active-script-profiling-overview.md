---
title: "Aktywnego skryptu profilowania — omówienie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Active Script Profiling
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9413e8b6e6db0c81eb1853c24506d20c8d06f3e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-profiling-overview"></a>Przegląd profilowania aktywnego skryptu
[Active interfejsy profilera skryptu](../winscript/reference/active-script-profiler-interfaces.md) włączyć profilowanie aparatu skryptów. Profilowanie aktywnego skryptu składa się z następujących elementów:  
  
-   Aparat języka  
  
-   Host  
  
-   Profiler  
  
## <a name="language-engine"></a>Aparat języka  
 Aparat języka wykonuje skryptu. Zapewnia metodę umożliwiającą profilowania kodu skryptu, jak wykonania. Po włączeniu profilowania aparat języka ma identyfikator klasy (CLSID) profilera obiektu modelu COM jako argument. Tworzy wystąpienie obiektu COM profilera, a następnie wywołuje profilera w przypadku wystąpienia różnych zdarzeń.  
  
 Implementuje aparat języka [interfejs IActiveScriptProfilerControl](../winscript/reference/iactivescriptprofilercontrol-interface.md).  
  
> [!NOTE]
>  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] Środowisko uruchomieniowe języka sprawdza zmienną środowiskową JS_PROFILER na tworzenie, aby określić, czy powinno być włączone profilowania. Jeśli ta zmienna jest ustawiona na identyfikator CLSID profilera, środowisko uruchomieniowe języka tworzy wystąpienie obiektu COM profilera, przy użyciu wartości zmiennej w celu określenia profilera, które można utworzyć.  
  
## <a name="host"></a>Host  
 Host tworzy aparat języka i zapewnia aparat język skryptów do wykonania. Host inteligentny także kontekstu dokumentu, używany przez debuger lub profiler w celu zapewnienia lepszej informacji podczas debugowania i profilowania.  
  
## <a name="profiler"></a>Profiler  
 Profiler odbiera wywołania z aparatu języka w przypadku wystąpienia różnych zdarzeń. Musi zostać zarejestrowany jako obiektu COM profilera, którą należy wdrożyć [interfejs IActiveScriptProfilerCallback](../winscript/reference/iactivescriptprofilercallback-interface.md) interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy profilera aktywnego skryptu](../winscript/reference/active-script-profiler-interfaces.md)