---
title: "Porady: debugowanie przepływów pracy opartych na programie ASP.NET (starsze) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0eb248f04119f8f0ad70b9a09a4fb22c73399233
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Porady: debugowanie przepływów pracy opartych na programie ASP.NET (starsze)
W tym temacie opisano sposób debugowania [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]— na podstawie [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplikacje, które odnoszą się do jednego [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] w starszych [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
 Można debugować starszych przepływy pracy, które są uruchamiane w ASP.NET lub starszego przepływów pracy, które są publikowane jako usługę sieci Web przez dołączenie do procesu, w którym jest hostowany przepływ pracy.  
  
### <a name="to-debug-an-aspnet-based-workflow"></a>Aby debugować przepływ pracy oparty na programie ASP.NET  
  
1.  Włącz debugowanie aplikacji ASP.NET przez ustawienie **debug = true** w pliku web.config.  
  
2.  Ustaw jako projekt startowy biblioteki przepływu pracy i ustawić punkty przerwania w przepływie pracy.  
  
3.  Wprowadź adres URL domyślnej strony sieci Web we właściwościach projektu przepływu pracy **debugowania** opcji **Start przeglądarki za pomocą zewnętrznego adresu URL** pola tekstowego.  
  
4.  Wybierz **dołączyć do procesu** na **debugowania** menu.  
  
5.  Wybierz proces, aby dołączyć do z **dostępne procesy** listy.  
  
     Dołączanie do procesu w3wp.exe, webdev.webserver lub aspnet_wp, w którym jest hostowany przepływ pracy.  
  
6.  Kliknij przycisk **wybierz** obok **dołączyć do** pola tekstowego.  
  
     **Wybór typu kodu** zostanie wyświetlone okno dialogowe.  
  
7.  Wybierz **Debuguj te typy kodu** i wybierz **przepływu pracy**.  
  
8.  Kliknij przycisk **OK**.  
  
9. Kliknij przycisk **dołączyć**.  
  
10. Otwórz w przeglądarce domyślnej strony sieci Web i Uruchom przepływ pracy.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsze)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Porady: Ustawianie punktów przerwania w przepływach pracy (starsze)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Debugowanie przepływów pracy starsza wersja](../workflow-designer/debugging-legacy-workflows.md)