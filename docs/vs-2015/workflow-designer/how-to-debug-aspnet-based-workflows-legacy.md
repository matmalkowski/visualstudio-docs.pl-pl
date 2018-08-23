---
title: 'Porady: debugowanie przepływów pracy opartych na programie ASP.NET (starsza wersja) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: d30cb54ea035dfac63cf3ab4761c2c7cb5376314
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678464"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Porady: debugowanie przepływów pracy opartych na programie ASP.NET (starsza wersja)
W tym temacie opisano sposób debugowania [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]— na podstawie [!INCLUDE[wf](../includes/wf-md.md)] aplikacji przeznaczonych dla albo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] w starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)].  
  
 Można debugować starszej wersji przepływów pracy, które są uruchamiane w ASP.NET lub starszej wersji przepływów pracy, które są publikowane jako usługi sieci Web przez dołączenie do procesu, w którym znajduje się przepływ pracy.  
  
### <a name="to-debug-an-aspnet-based-workflow"></a>Aby debugować przepływ pracy oparty na programie ASP.NET  
  
1.  Włącz debugowanie aplikacji ASP.NET, ustawiając **debug = true** w pliku web.config.  
  
2.  Ustaw biblioteki przepływu pracy jako projekt startowy, a następnie ustawić punkty przerwania w przepływie pracy.  
  
3.  Wprowadź adres URL domyślnej strony sieci Web we właściwościach projektu przepływu pracy **debugowania** opcji **uruchamiania przeglądarki za pomocą zewnętrznego adresu URL** pola tekstowego.  
  
4.  Wybierz **dołączyć do procesu** na **debugowania** menu.  
  
5.  Wybierz proces do dołączenia z **dostępne procesy** listy.  
  
     Dołącz do procesu w3wp.exe, webdev.webserver lub aspnet_wp, w którym znajduje się przepływ pracy.  
  
6.  Kliknij przycisk **wybierz** obok **dołączyć do** pola tekstowego.  
  
     **Wybieranie typu kodu** pojawi się okno dialogowe.  
  
7.  Wybierz **debugowania tych typów kodu** i wybierz **przepływu pracy**.  
  
8.  Kliknij przycisk **OK**.  
  
9. Kliknij przycisk **dołączyć**.  
  
10. Otwórz domyślną stronę sieci Web w przeglądarce i uruchomić przepływ pracy.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsza wersja)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Porady: Ustawianie punktów przerwania w przepływach pracy (starsza wersja)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Debugowanie starszych wersji przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)