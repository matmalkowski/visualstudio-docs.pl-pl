---
title: "Debugowanie przepływów pracy starszego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2253eb414e58d5168cf6e1d2f4c22880d18d1bd6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="debugging-legacy-workflows"></a>Debugowanie przepływów pracy starsza wersja
Jeśli używasz starszego [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] w [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] do tworzenia [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplikacji czy target.NET Framework 3.0 lub 3.5 może debugować przepływy pracy, takich jak inny program Ustawianie punktów przerwania, dołączanie do procesów i wątków badanie i stos wywołań. Istnieje również możliwość debugowania zdalnego.  
  
> [!NOTE]
>  Jeśli wiele wersji programu Visual Studio zostały zainstalowane i odinstalować na komputerze, debugowanie WF3 może zakończyć się niepowodzeniem z jednym z dwóch następujące możliwości:  
>   
>  -   Punkty przerwań nie są osiągane.  
> -   Zostanie wyświetlony następujący komunikat:  
>   
>  **Nie można rozpocząć debugowania na serwerze sieci web. Debuger nie jest poprawnie zainstalowany.  Nie można debugować żądanego typu kodu.  Uruchom Instalatora, aby zainstalować lub naprawić debuger.**  
>   
>  W przypadku jednego z tych scenariuszy podczas debugowania środowiska .NET Framework 3.0 lub 3.5 przepływy pracy, wykonaj naprawę instalacji programu Visual Studio.  
  
 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)]integruje się z następujących standard [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugowania systemu windows:  
  
-   **Punkt przerwania**: działa zgodnie z oczekiwaniami, ale Określ działanie dla nazwy funkcji.  
  
-   **Stos wywołań**: zmodyfikowane w celu zapewnienia konspektu działań, które zostały wykonane w wystąpieniu przepływu pracy. Wpisy w **stos wywołań** okna są pierwszy głębokość wyszukiwania wykonywanych działań. Możesz kliknąć dwukrotnie wpis, aby umieścić fokus na działanie wybranego.  
  
-   **Wątki**: zawiera identyfikator wystąpienia wystąpienia przepływu pracy, które jest debugowane.  
  
 Visual Studio dla systemu Windows Workflow Foundation nie obsługuje debugowania następujące funkcje:  
  
-   Warunkowe punkty przerwania na powierzchnię projektanta.  
  
-   QuickWatch.  
  
-   Ustaw następną instrukcję.  
  
-   Uruchom do kursora.  
  
-   Edytuj i Kontynuuj.  
  
-   Debugowanie just in time.  
  
-   Debugowanie w trybie mieszanym.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wywoływanie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsze)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Wyłączenie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsze)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Porady: debugowanie przepływów pracy opartych na programie ASP.NET (starsze)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)  
  
 [Porady: Ustawianie punktów przerwania w przepływach pracy (starsze)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)  
  
 [Debugowanie przepływów pracy na komputerze zdalnym (starsze)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)  
  
 [Debugowanie wykonywania krokowego opcje (starsze)](../workflow-designer/debug-stepping-options-legacy.md)  
  
 [Porady: Zmień opcję krokowe wykonywanie debugowania (starsze)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)