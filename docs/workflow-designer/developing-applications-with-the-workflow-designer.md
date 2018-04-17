---
title: Tworzenie aplikacji za pomocą projektanta przepływów pracy | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DefaultWorkflowDesigner
- DefaultWorkflowDesigner.UI
helpviewer_keywords:
- Visual Studio 2010 Workflow Designer [WFD], overview
- Workflow Designer [WFD]
- Visual Studio 2010 Workflow Designer [WFD]
- Workflow Designer [WFD], overview
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c48e7b43b23e7bfe8887f437cc17e6db077c0e4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="developing-applications-with-the-workflow-designer"></a>Tworzenie aplikacji za pomocą projektanta przepływów pracy

Projektant przepływu pracy systemu Windows jest Projektant wizualny oraz debugera dla konstrukcji graficznego i debugowanie [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplikacji w [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] jest hostowana w [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] Środowisko deweloperskie. Umożliwia utworzenie aplikacji złożonych przepływu pracy, biblioteka działań lub [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] usługi przy użyciu szablonów i projektantów działań. Aby uzyskać więcej informacji o przepływach pracy, zobacz [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Poniżej przedstawiono kilka nowych funkcji projektowania, które ustawić tej nowej wersji [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] oprócz starsze wersje [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]:

-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] Jest utworzony przy użyciu [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)]. Podnosi poziom obsługi projektanta działania i zwiększa wydajność w przypadku dużych i złożonych przepływów pracy.

-   Działania niestandardowe są wyposażone [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)], przy użyciu języka XAML i modelu programowania do tworzenia projektantów działań zostały uproszczone.

-   Działanie flowchart został zaimplementowany, więc można zwizualizować przepływem programu przy użyciu znanych schemat blokowy modelowania stylu.

-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] Ma nowej zmiennej projektanta umożliwiający deklarowanie i zakres zmiennych w ramach przepływów pracy, powiązanie ich działania.

-   W [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] zapewnia pełne możliwości funkcji IntelliSense, podczas tworzenia wyrażenia języka Visual Basic w ramach Twojej [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] przepływów pracy.

-   Działanie debugowania została rozszerzona w języku XAML, dzięki czemu można ustawić punktów przerwania w definicji przepływu pracy XAML i Wkrocz do kodu XAML w czasie wykonywania, która zapewnia środowisko, podobnie jak w kodzie zarządzanym.

-   Rehosting [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] została uproszczona znacznie w porównaniu z poprzednimi wersjami, teraz wymagające tylko kilka wierszy kodu.

-   Nowy <xref:System.Activities.Statements.Flowchart> działanie i jego [schemat blokowy](../workflow-designer/flowchart-activity-designer.md) pozwala na wizualizowanie z przepływem programu przy użyciu znanych schemat blokowy modelowania stylu.

-   Zostały rozszerzone działania obsługi wiadomości, co umożliwia zapis w pełni deklaracyjnego (Brak kodu) [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] usług.

-   **Dodać odwołania do usługi...**  funkcjonalność umożliwia generowanie działania automatycznie uzyskiwać dostęp do usług sieci Web.