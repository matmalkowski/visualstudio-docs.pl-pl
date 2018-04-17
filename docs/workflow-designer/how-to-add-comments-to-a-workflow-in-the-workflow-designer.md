---
title: 'Porady: dodawanie komentarzy do przepływu pracy w Projektancie przepływów pracy | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: fb7505d773f26a26df0b31477d99f7f5636d8c40
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Porady: dodawanie komentarzy do przepływu pracy w Projektancie przepływów pracy

Aby ułatwić tworzenie większych i bardziej skomplikowanych przepływów pracy, [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] umożliwia deweloperowi dodawać adnotacje do następujących typów elementów w Projektancie:

-   <xref:System.Activities.Activity>

-   <xref:System.Activities.Statements.State>

-   <xref:System.Activities.Statements.Transition>

-   Klasy wyprowadzone z <xref:System.Activities.Statements.FlowNode>

-   <xref:System.Activities.Variable>

-   <xref:System.Activities.Argument>

> [!IMPORTANT]
> Zawartość adnotacji są zapisywane w postaci zwykłego tekstu w pliku XAML skojarzonego z przepływem pracy i mogą zostać odczytane przez innych użytkowników. Należy zachować ostrożność podczas wprowadzania informacji poufnych w adnotacji.

### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Dodawanie adnotacji do działania w Projektancie

1. W Projektancie przepływów pracy, kliknij prawym przyciskiem myszy element w przepływie pracy projektanta i wybierz pozycję **adnotacje**, **Dodawanie adnotacji**.

1. Dodaj tekst adnotacji w odpowiednim miejscu.

   Element zawiera ikonę adnotacji. Kursor myszy na ikonie adnotacji Wyświetla tekst adnotacji.

### <a name="displaying-an-annotation-in-an-activitys-designer"></a>Wyświetlanie w Projektant działań adnotacja

1.  Projektant działań, którego adnotacji wyświetlanie poza danym działaniem, kliknij polecenie **numeru Pin** ikonę w moduł definiowania układu adnotacji.

   Adnotacja jest wyświetlany w Projektancie działania. Na poniższym zrzucie ekranu adnotacja "Rozpoczęcia działania w przepływie pracy" jest wyświetlany w Projektancie działania.

   ![Widoczne w Projektancie działań adnotacja](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")

1. Aby wyświetlić poza Projektant działań adnotacja, umieść kursor nad obszarem adnotacji w Projektancie działania, a następnie kliknij przycisk **Odepnij** ikony

   ![Wyświetlane poza designe działań adnotacja](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")

### <a name="showing-or-hiding-all-annotations"></a>Pokazywanie lub ukrywanie wszystkie adnotacje

1. Kliknij prawym przyciskiem myszy działanie, które ma adnotację. Wybierz **adnotacje**, **Pokaż wszystkie adnotacje**.

   Wszystkie adnotacje są wyświetlane w projektantach działania.

1. Aby wyświetlić wszystkie adnotacje poza projektantów działań, kliknij prawym przyciskiem myszy działanie i wybierz **adnotacje**, **Ukryj wszystkie adnotacje**.

### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Edytowanie lub usuwanie adnotacji dla działania

1. Kliknij prawym przyciskiem myszy na działanie, które ma adnotację.

1. Wybierz **adnotacje**, **Edytuj adnotację** lub **Usuń adnotację**.

   Adnotacja jest otwarty do edycji lub usunięty.

1. Aby usunąć wszystkie adnotacje jednocześnie, kliknij prawym przyciskiem myszy przepływu pracy projektanta i wybierz pozycję **adnotacji**, **usunąć wszystkie adnotacje**.

### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Dodawanie, edytowanie i usuwanie adnotacji dla zmiennej lub argumentu

1. Kliknij prawym przyciskiem myszy na zmiennej lub argumentu i wybierz opcję Dodaj adnotację.

1. Wprowadź tekst adnotacji. Wyświetla ikonę adnotacji, zmiennej lub argumentu.

1. Kliknij prawym przyciskiem myszy na zmiennej lub argumentu, który ma adnotację. Wybierz pozycję Edytuj adnotacji.

   Adnotacja jest otwarty do edycji.

1. Kliknij prawym przyciskiem myszy na zmiennej lub argumentu, który ma adnotację. Wybierz Usuń adnotację.

   Adnotacja jest usuwany.