---
title: "Działania ParallelForEach&lt;T&gt; Projektant działań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 56a20f6e29f0f1bd6e071e6d3b48442c0bf02e77
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="parallelforeachlttgt-activity-designer"></a>Działania ParallelForEach&lt;T&gt; Projektant działań
<xref:System.Activities.Statements.ParallelForEach%601> Działanie wylicza elementów kolekcji i wykonuje instrukcję embedded dla każdego elementu w kolekcji równolegle, co jest asynchronicznie, w tym samym wątku. Użyj tego działania kontroli przepływu zamiast <xref:System.Activities.Statements.Sequence> działania, jeśli działania podrzędne tego działania powinny przejść w stanie bezczynności.  
  
 <xref:System.Activities.Statements.ParallelForEach%601> Działanie ma <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> właściwość, która zawiera określonego przez użytkownika [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] wyrażenia. <xref:System.Activities.Statements.ParallelForEach%601> Działanie ocenia tej właściwości po zakończeniu każdej gałęzi. Jeśli daje w wyniku **true**, a następnie <xref:System.Activities.Statements.ParallelForEach%601> kończy działanie bez wykonywania innych działów. Jeśli <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> nie zwraca **true**, a następnie <xref:System.Activities.Statements.ParallelForEach%601> zakończeniu działania, gdy wszystkie działania podrzędne zostaną zakończone.  
  
## <a name="the-parallelforeacht-activity"></a>Działania ParallelForEach < T\> działania  
 <xref:System.Activities.Statements.ParallelForEach%601>Wylicza jego wartości i harmonogramy <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> dla każdej wartości on wylicza na. Tylko zaplanowane <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. Jak wykonuje treść jest zależny od tego, czy <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> przechodzi bezczynności.  
  
 Jeśli <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> nie przechodzi bezczynny, wykonywania w odwrotnej kolejności ponieważ zaplanowanych działań są obsługiwane jako stos, najpierw wykonana ostatnim zaplanowanym działaniem. Na przykład, jeśli masz kolekcję {1,2,3,4} w <xref:System.Activities.Statements.ParallelForEach%601> i użyj **WriteLine** jako treść zapisać wartość. Masz 4, 3, 2, 1 drukowany w konsoli. Jest to spowodowane **WriteLine** nie przechodzi w stanie bezczynności, po 4 **WriteLine** otrzymano zaplanowanych działań, są wykonywane przy użyciu zachowanie stosu (pierwszy w ostatnim poza).  
  
 Ale jeśli masz działań w <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> który Przejdź bezczynny, takich jak <xref:System.ServiceModel.Activities.Receive> działania lub <xref:System.Activities.Statements.Delay> działania. Oznacza to, że nie trzeba czekać na ich zakończenie. <xref:System.Activities.Statements.ParallelForEach%601>zbliża się do następnego zaplanowane działanie dotyczące treści i spróbować ją wykonać. Jeśli danego działania bezczynności, <xref:System.Activities.Statements.ParallelForEach%601> przenosi na ponownie następne działanie treści.  
  
### <a name="using-the-parallelforeacht-activity-designer"></a>Za pomocą działania ParallelForEach\<T > Projektant działań  
 **Działania ParallelForEach\<T >** Projektant działań można znaleźć w **przepływ sterowania** kategorii **przybornika**, które jest dostępne po kliknięciu  **Przybornik** karcie po lewej stronie [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)  
  
 **Działania ParallelForEach\<T >** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni wszędzie tam, gdzie są zazwyczaj umieszczone projektantów działań, dla przykład, wewnątrz **sekwencji** Projektant działań. Po usunięcie go do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], tworzy <xref:System.Activities.Statements.ParallelForEach%601> działania, która domyślnie zawiera <xref:System.Activities.Activity.DisplayName%2A> z **działania ParallelForEach < Int32\>.**  
  
### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>Działania ParallelForEach < T\> właściwości w Projektancie przepływów pracy  
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.ParallelForEach%601> właściwości działania i w tym artykule opisano, jak są używane w projektancie.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę wyświetlaną projektanta działania w nagłówku. Wartość domyślna to **działania ParallelForEach\<Int32 >**. Wartość może być opcjonalnie edytowany w **właściwości** siatki lub bezpośrednio w nagłówku projektanta działania.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Działanie do wykonania dla każdego elementu w kolekcji. Aby dodać <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> działania, Porzuć działanie z przybornika do **treści** polu na **działania ParallelForEach\<T >** Projektant działań z tekstu podpowiedzi "Upuść tutaj działanie".|  
|**Elementu TypeArgument**|Wartość true|Typ elementów w <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> kolekcji określonej przez parametr ogólny *T*. Domyślnie **elementu TypeArgument** ustawiono **Int32**. Aby zmienić typ T w **działania ParallelForEach < T\>**  Projektant działań, zmień wartość **elementu TypeArgument** pola kombi w siatce właściwości.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|Wartość true|Kolekcja elementów w celu wykonania iteracji. Aby ustawić <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, wpisz [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] wyrażenie w **wartości** polu na **ForEach < T\>**  Projektant działań w polu z tekstu podpowiedzi "Wprowadź wyrażenia języka VB." lub w **Wartości** polu na **właściwości** okna.|  
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Oceniane, po zakończeniu każdej iteracji. Jeśli go daje w wyniku wartość true, a następnie według harmonogramu oczekujące zostały anulowane iteracji. Jeśli ta właściwość nie jest ustawiona, wszystkie instrukcje zaplanowane wykonanie do momentu zakończenia.|  
  
 Domyślnie sterująca pętli nosi nazwę elementu. Można zmienić nazwę zmiennej iteracyjnej w **ForEach** polu **działania ParallelForEach\<T >** Projektant działań. Sterująca pętli można używać w wyrażeniach w elementów podrzędnych <xref:System.Activities.Statements.ParallelForEach%601> działania.  
  
## <a name="see-also"></a>Zobacz też  
 [Sekwencja](../workflow-designer/sequence-activity-designer.md)   
 [Równoległe](../workflow-designer/parallel-activity-designer.md)   
 [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)