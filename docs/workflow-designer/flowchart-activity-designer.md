---
title: Schemat blokowy działania projektanta | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f7db449f538f09a247bc3c67ee26f487a6c81eb0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="flowchart-activity-designer"></a>Schemat blokowy Projektant działań
<xref:System.Activities.Statements.Flowchart> To działanie służy do tworzenia przepływów pracy, zdefiniuj i zarządzać związanymi z formantów złożonych przepływu. A <xref:System.Activities.Statements.Flowchart> można tworzyć w kodzie lub za pomocą [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Ten temat dokumenty [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] wystąpić. Projektant działań przepływu pracy projektanta przepływów pracy systemu Windows umożliwia deweloperom tworzyć przepływy pracy w sposób fizycznych.

## <a name="the-flowchart-activity"></a>Schemat blokowy działania
 <xref:System.Activities.Statements.Flowchart> Określa unikatową <xref:System.Activities.Statements.Flowchart.StartNode%2A> który jest wykonywany podczas uruchamiania przepływu pracy i używa połączone z siecią <xref:System.Activities.Statements.Flowchart.Nodes%2A> do utworzenia dowolnego pętli lub przekierowywać przepływ wykonania do dowolnej lokalizacji w przepływie pracy w danym momencie.

### <a name="using-the-flowchart-activity-designer"></a>Przy użyciu narzędzia Projektant działań schematu blokowego
 **Schemat blokowy** Projektant działań można znaleźć w **schemat blokowy** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karcie na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)

 **Schemat blokowy** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni wszędzie tam, gdzie projektantów działań są zazwyczaj umieszczone, jako działania głównego lub jako element podrzędny z innego działania przepływu sterowania. Jeśli **schemat blokowy** upuszczeniu Projektant działań na pusty [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] tworzy powierzchni, <xref:System.Activities.Statements.Flowchart> działania, które domyślnie wyświetla się w widoku rozwiniętego, w którym jest węzeł początkowy, który inicjuje wykonywania reprezentowany jako piłka zielony. Jeśli **schemat blokowy** Projektant działań są przenoszone do innego działania przepływu sterowania, wyświetla się w trybie zminimalizowanym widoku, który można rozszerzać przez dwukrotne kliknięcie **schemat blokowy** Projektant działań. Wszystkie działania w **przybornika** mogą być przeciągnięte bezpośrednio na **schemat blokowy** Projektant działań, włącznie z innymi działaniami przepływu sterowania.

 Po różnych projektantów działań na przeciąganie [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] kanwy, <xref:System.Activities.Activity> reprezentują obiekty mogą być połączone ze sobą, aby określić kolejność wykonywania. Aby utworzyć łącze między działaniem źródła i działanie docelowe, myszą projektanta działania źródłowego i kwadratowe uchwyty są wyświetlane na każdej stronie. Jednym z kwadratowych uchwytów kliknij i przeciągnij go, przytrzymując przycisk myszy, aby jeden dojść, które jest wyświetlany w podobny sposób wokół działania docelowego, gdy kursor myszy nad nim przy użyciu myszy. Zwolnij przycisk myszy, a tworzone jest połączenie tych dwóch działań, które jest reprezentowany jako strzałka z projektanta źródła do projektanta docelowego.

### <a name="flowchart-activity-properties"></a>Schemat blokowy działania właściwości
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Flowchart> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchnię projektanta.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa nazwę wyświetlaną Projektant działań w nagłówku. Wartość domyślna to schemat blokowy. Wartość można edytować w **właściwości** okna lub bezpośrednio w nagłówku projektanta działania.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jej użyć.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|False|Kolekcja zmiennych, które są ograniczone w ramach tego <xref:System.Activities.Statements.Flowchart> udostępniania stanu między działania podrzędne.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|False|<xref:System.Activities.Statements.FlowNode> Który jest wykonywane, kiedy <xref:System.Activities.Statements.Flowchart> uruchamia.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|False|Zawiera kolekcję <xref:System.Activities.Statements.FlowNode> obiekty w <xref:System.Activities.Statements.Flowchart>.|

## <a name="see-also"></a>Zobacz także

- [Schemat blokowy](../workflow-designer/flowchart-activity-designers.md)
- [Elementu FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)