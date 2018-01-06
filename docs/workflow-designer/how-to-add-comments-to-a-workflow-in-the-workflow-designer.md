---
title: "Porady: dodawanie komentarzy do przepływu pracy w Projektancie przepływów pracy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
caps.latest.revision: "7"
ms.author: sdanie
manager: erikre
ms.workload: multiple
ms.openlocfilehash: e4d547fed57abf11194b35bcd3ac42f12322374b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Porady: dodawanie komentarzy do przepływu pracy w Projektancie przepływów pracy
Aby ułatwić tworzenie większych i bardziej skomplikowanych przepływów pracy, [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] umożliwia deweloperowi dodawać adnotacje do następujących typów elementów w Projektancie:  
  
-   <xref:System.Activities.Activity>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
-   Klasy wyprowadzone z<xref:System.Activities.Statements.FlowNode>  
  
-   <xref:System.Activities.Variable>  
  
-   <xref:System.Activities.Argument>  
  
> [!IMPORTANT]
>  Zawartość adnotacji są zapisywane w postaci zwykłego tekstu w pliku XAML skojarzonego z przepływem pracy i mogą zostać odczytane przez innych użytkowników. Należy zachować ostrożność podczas wprowadzania informacji poufnych w adnotacji.  
  
### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Dodawanie adnotacji do działania w Projektancie  
  
1.  W Projektancie przepływów pracy, kliknij prawym przyciskiem myszy element w przepływie pracy projektanta i wybierz pozycję **adnotacje**, **Dodawanie adnotacji**.  
  
2.  Dodaj tekst adnotacji w odpowiednim miejscu.  
  
3.  Element pojawi się ikona adnotacji. Kursor myszy na ikonie adnotacji wyświetli tekst adnotacji.  
  
     ![Sekwencja działań adnotacja przedstawiający](../debugger/debug-interface-access/annotation.md "adnotacji")  
  
### <a name="displaying-an-annotation-in-an-activitys-designer"></a>Wyświetlanie w Projektant działań adnotacja  
  
1.  Projektant działań, którego adnotacji wyświetlanie poza danym działaniem, kliknij polecenie **numeru Pin** ikonę w moduł definiowania układu adnotacji.  
  
2.  Adnotacja zostanie wyświetlony w Projektancie działania. Na poniższym zrzucie ekranu adnotacja "Rozpoczęcia działania w przepływie pracy" jest wyświetlany w Projektancie działania.  
  
     ![Widoczne w Projektancie działań adnotacja](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")  
  
3.  Aby wyświetlić poza Projektant działań adnotacja, umieść kursor nad obszarem adnotacji w Projektancie działania, a następnie kliknij przycisk **Odepnij** ikony  
  
     ![Wyświetlane poza designe działań adnotacja](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")  
  
### <a name="showing-or-hiding-all-annotations"></a>Pokazywanie lub ukrywanie wszystkie adnotacje  
  
1.  Kliknij prawym przyciskiem myszy działanie, które ma adnotację. Wybierz **adnotacje**, **Pokaż wszystkie adnotacje**.  
  
2.  Wszystkie adnotacje będą wyświetlane w projektantach działania.  
  
3.  Aby wyświetlić wszystkie adnotacje poza projektantów działań, kliknij prawym przyciskiem myszy działanie i wybierz **adnotacje**, **Ukryj wszystkie adnotacje**.  
  
### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Edytowanie lub usuwanie adnotacji dla działania  
  
1.  Kliknij prawym przyciskiem myszy na działanie, które ma adnotację.  
  
2.  Wybierz **adnotacje**, **Edytuj adnotację** lub **Usuń adnotację**.  
  
3.  Adnotacja zostanie otwarty do edycji lub usunięty.  
  
4.  Aby usunąć wszystkie adnotacje jednocześnie, kliknij prawym przyciskiem myszy przepływu pracy projektanta i wybierz pozycję **adnotacji**, **usunąć wszystkie adnotacje**.  
  
### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Dodawanie, edytowanie i usuwanie adnotacji dla zmiennej lub argumentu  
  
1.  Kliknij prawym przyciskiem myszy na zmiennej lub argumentu i wybierz opcję Dodaj adnotację.  
  
2.  Wprowadź tekst adnotacji. Wyświetla ikonę adnotacji zmiennej lub argumentu.  
  
3.  Kliknij prawym przyciskiem myszy na zmiennej lub argumentu, który ma adnotację. Wybierz pozycję Edytuj adnotacji.  
  
4.  Adnotacja zostanie otwarty do edycji.  
  
5.  Kliknij prawym przyciskiem myszy na zmiennej lub argumentu, który ma adnotację. Wybierz Usuń adnotację.  
  
6.  Adnotacja zostaną usunięte.