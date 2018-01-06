---
title: Uruchamianie aplikacji platformy uniwersalnej systemu Windows na komputerze lokalnym | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 63cb81c9bc168ad0bda8d675c0bf0bbde3759eff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="run-uwp-apps-on-the-local-machine"></a>Uruchamianie aplikacji platformy uniwersalnej systemu Windows na komputerze lokalnym
![Dotyczy tylko systemów Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Aby debugować, test lub uruchomienie analizy wydajności w aplikacji platformy uniwersalnej systemu Windows, można uruchomić aplikacji na tym samym komputerze obsługującego programu Visual Studio. Jeśli są wyświetlane na urządzeniu z obsługą dotyku, można korzystać z pełnej funkcjonalności aplikacji; w przeciwnym razie będzie ograniczony do gesty myszy i klawiatury.  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a>Jak uruchomić na komputerze lokalnym  
 Aby uruchomić aplikację na komputerze lokalnym, zaznacz **komputera lokalnego** z listy rozwijanej obok przycisku Rozpocznij debugowanie debugera **standardowe** paska narzędzi.  
  
 ![Uruchom na komputerze lokalnym](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
 Jeśli nie widzisz **standardowe** narzędzi kliknij przycisk **widoku** menu wskaż **paski narzędzi**, a następnie kliknij przycisk **standardowe**.  
  
 Wybór dokonany na liście rozwijanej w pliku właściwości projektu jest trwały i staje się wartością domyślną Uruchom docelowej.  
  
 Element docelowy uruchomienia można również ustawić bezpośrednio w pliku właściwości projektu. Kliknij prawym przyciskiem myszy nazwę projektu w **Eksploratora rozwiązań** , a następnie wybierz **właściwości**. Następnie wykonaj jedną z następujących czynności:  
  
-   W projektach C# i Visual Basic, kliknij przycisk **debugowania** , a następnie wybierz **komputera lokalnego** z **urządzenie docelowe** listy rozwijanej.  
  
     ![K & 35; Strona właściwości projektu Visual Basic i](../debugger/media/vsrun_cs_vb_projprop_local.png "VSRUN_CS_VB_ProjProp_Local")  
  
-   W projektach C++ i JavaScript, rozwiń węzeł **właściwości konfiguracji** węzła, kliknij przycisk **debugowanie**, a następnie wybierz **lokalnego debugera** z **debugera Aby uruchomić** listy.  
  
     ![& C &43; 43; Strona właściwości projektu języka JavaScript i](../debugger/media/vsrun_cpp_js_projprop_local.png "VSRUN_CPP_JS_ProjProp_Local")  