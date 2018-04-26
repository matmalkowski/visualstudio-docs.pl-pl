---
title: Tworzenie aplikacji za pomocą projektanta przepływów pracy
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
ms.openlocfilehash: ecc9e42146bfa7de259551ff1c90d27201db5725
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="developing-applications-with-the-workflow-designer"></a>Tworzenie aplikacji za pomocą projektanta przepływów pracy

Projektant przepływu pracy systemu Windows jest Projektant wizualny oraz debugera dla konstrukcji graficznego i debugowanie aplikacji systemu Windows Workflow Foundation (WF) w programie .NET Framework 4 jest hostowany w środowisku projektowym Visual Studio 2010. Umożliwia utworzenie aplikacji złożonych przepływu pracy, biblioteka działań lub usługi Windows Communication Foundation (WCF) przy użyciu szablonów i projektantów działań. Aby uzyskać więcej informacji o przepływach pracy, zobacz [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Poniżej przedstawiono kilka nowych funkcji projektowania, które ustawić tej nowej wersji projektanta przepływów pracy, oprócz starsze wersje projektanta przepływów pracy:

-   Projektant przepływu pracy jest utworzony przy użyciu systemu Windows Presentation Foundation (WPF). Podnosi poziom obsługi projektanta działania i zwiększa wydajność w przypadku dużych i złożonych przepływów pracy.

-   Działania niestandardowe są wyposażone [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)], przy użyciu języka XAML i modelu programowania do tworzenia projektantów działań zostały uproszczone.

-   Działanie flowchart został zaimplementowany, więc można zwizualizować przepływem programu przy użyciu znanych schemat blokowy modelowania stylu.

-   Projektanta przepływów pracy ma nowej zmiennej projektanta umożliwiający deklarowanie i zakres zmiennych w ramach przepływów pracy, powiązanie ich działania.

-   W programie Visual Studio 2010 projektanta przepływów pracy zapewnia pełne możliwości funkcji IntelliSense podczas tworzenia wyrażenia języka Visual Basic w ramach przepływów pracy programu .NET Framework 4.

-   Działanie debugowania została rozszerzona w języku XAML, dzięki czemu można ustawić punktów przerwania w definicji przepływu pracy XAML i Wkrocz do kodu XAML w czasie wykonywania, która zapewnia środowisko, podobnie jak w kodzie zarządzanym.

-   Rehosting projektanta przepływów pracy poza Visual Studio jest znacznie uproszczone porównaniu z poprzednimi wersjami, teraz wymagające tylko kilka wierszy kodu.

-   Nowy <xref:System.Activities.Statements.Flowchart> działanie i jego [schemat blokowy](../workflow-designer/flowchart-activity-designer.md) pozwala na wizualizowanie z przepływem programu przy użyciu znanych schemat blokowy modelowania stylu.

-   Zostały rozszerzone działania obsługi wiadomości, co umożliwia zapis w pełni deklaracyjnego (Brak kodu) usług Windows Communication Foundation (WCF).

-   **Dodać odwołania do usługi...**  funkcjonalność umożliwia generowanie działania automatycznie uzyskiwać dostęp do usług sieci Web.