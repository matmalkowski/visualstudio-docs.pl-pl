---
title: Tworzenie projektu programu Workflow Foundation
ms.date: 06/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a4f8ed1effbc459bd2a17e3433738c1b461513b
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755657"
---
# <a name="workflow-project-templates"></a>Szablony projektu przepływu pracy

Przepływy pracy, usługi przepływu pracy Windows Communication Foundation (WCF), niestandardowych działań i projektantów działań niestandardowych można utworzyć przy użyciu szablonów projektu programu Visual Studio. W tym artykule opisano sposób tworzenia bibliotek i aplikacji z szablonów projektu dostępnych w programie Visual Studio.

## <a name="create-a-workflow-project"></a>Tworzenie projektu przepływu pracy

Program Visual Studio oferuje cztery różne szablonów projektu przepływu pracy:

- Aplikacja konsoli przepływu pracy

- Aplikacja usługi przepływu pracy WCF

- Biblioteka działań

- Biblioteka projektanta działań

Aby uzyskać dostęp do tych szablonów, należy najpierw zainstalować **Windows Workflow Foundation** składnika programu Visual Studio 2017 r. Aby uzyskać szczegółowe instrukcje, zobacz [zainstalować program Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Po zainstalowaniu **Windows Workflow Foundation** składników, otwórz **nowy projekt** okna dialogowego, wybierając **pliku** > **nowy**  >  **Projektu**.

1. W okienku po lewej stronie wybierz **Visual C#** > **przepływu pracy** kategorii (lub **Visual Basic** > **przepływu pracy**Jeśli wolisz Visual Basic).

1. W środkowym okienku, wybierz szablon projektu, takie jak **Aplikacja konsoli przepływu pracy**.

1. W **nazwa** wprowadź opisową nazwę projektu ułatwić jego późniejszą identyfikację.

1. W **lokalizacji** wprowadź katalog, w którym chcesz zapisać projekt lub wybierz **Przeglądaj** można przejść do niego.

1. W **rozwiązania** wprowadź nazwę dla nowego rozwiązania. Wybierz **OK** do tworzenia aplikacji.

   > [!NOTE]
   > Jeśli chcesz dodać nowy projekt do istniejącego rozwiązania, otworzyć tego rozwiązania w programie Visual Studio, kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań**i wybierz **Dodaj** > **nowy Projekt** otworzyć **nowy projekt** okno dialogowe.

## <a name="workflow-console-app"></a>Aplikacja konsoli przepływu pracy

Jeśli wybierzesz **Aplikacja konsoli przepływu pracy** szablon, Visual Studio tworzy definicji przepływu pracy w języku XAML. Projektant przepływu pracy otwiera i wyświetla obszar roboczy dla przepływu pracy, który został utworzony. Utworzenie przepływu pracy, przeciągnij działania lub innych elementów przepływu pracy z **przybornika** na powierzchnię projektu.

## <a name="wcf-workflow-service-app"></a>Aplikacja usługi przepływu pracy WCF

Jeśli wybierzesz **aplikacji usługi przepływu pracy WCF** szablon, Visual Studio tworzy definicji usługi jako XAML. Otwiera projektanta przepływów pracy do widoku projektu z <xref:System.Activities.Statements.Sequence> działanie, które zawiera zestaw <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> działań.

## <a name="activity-library"></a>Biblioteka działań

Jeśli wybierzesz **Biblioteka działań** szablon, Visual Studio tworzy definicji działania w języku XAML. Projektant przepływów pracy otwiera i wyświetla obszar roboczy dla działania niestandardowego. Przeciągnij działanie z **przybornika** na powierzchnię projektu, aby objąć działania niestandardowego.

> [!NOTE]
> Możesz tylko jeden element podrzędny działania w treści działania niestandardowego. Jednak tego działania podrzędnego może być złożonego działania, takie jak <xref:System.Activities.Statements.Sequence> działania lub <xref:System.Activities.Statements.Flowchart> działania.

## <a name="activity-designer-library"></a>Biblioteka projektanta działań

Jeśli wybierzesz **Biblioteka Projektant działań** szablon, Visual Studio tworzy definicji działania projektanta XAML i pliku implementacji związane z kodem. Projektanta przepływów pracy otwiera i wyświetla obszaru roboczego dla programu Projektant działań. Przeciągnij Windows Presentation Foundation (WPF) formantów **przybornika** na powierzchnię projektu z nich korzystać w Projektancie Twoje działania niestandardowego.

Na przykład sposobu wdrażania Projektant działań niestandardowych, zobacz [jak: utworzyć designer działania niestandardowego](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Projektanci działania niestandardowego można dla działań niestandardowych i domyślnych działań .NET Framework.

## <a name="see-also"></a>Zobacz także

- [Za pomocą projektanta przepływów pracy](../workflow-designer/using-the-workflow-designer.md)
- [Projektowanie przepływów pracy (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)