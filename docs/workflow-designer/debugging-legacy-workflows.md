---
title: Debugowanie przepływów pracy starszego | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2710266446e285d9107f4450c09ffe2e8e87e090
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="debugging-legacy-workflows"></a>Debugowanie przepływów pracy starsza wersja

Jeśli używasz starszej wersji projektanta przepływów pracy systemu Windows w [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] do tworzenia [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] czy target.NET Framework 3.0 lub 3.5 może debugować przepływy pracy, takich jak inny program Ustawianie punktów przerwania, dołączanie do procesu i badanie aplikacji wątki i stosu wywołań. Istnieje również możliwość debugowania zdalnego.

> [!NOTE]
> Jeśli wiele wersji programu Visual Studio zostały zainstalowane i odinstalować na komputerze, debugowanie WF3 może zakończyć się niepowodzeniem z jednym z dwóch następujące możliwości:
>
> -   Punkty przerwań nie są osiągane.
> -   Zostanie wyświetlony następujący komunikat:
>
> **Nie można rozpocząć debugowania na serwerze sieci web. Debuger nie jest poprawnie zainstalowany.  Nie można debugować żądanego typu kodu.  Uruchom Instalatora, aby zainstalować lub naprawić debuger.**
>
> W przypadku jednego z tych scenariuszy podczas debugowania środowiska .NET Framework 3.0 lub 3.5 przepływy pracy, wykonaj naprawę instalacji programu Visual Studio.

 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] integruje się z następujących standard [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugowania systemu windows:

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