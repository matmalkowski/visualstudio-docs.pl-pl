---
title: Projektant przepływu pracy — Projektant działań schematu blokowego
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
ms.openlocfilehash: 4dd44a91ac2a3d823c5a5690edbdd57422857ea9
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755631"
---
# <a name="flowchart-activity-designer"></a>Flowchart, projektant działań

<xref:System.Activities.Statements.Flowchart> To działanie służy do tworzenia przepływów pracy, zdefiniuj i zarządzać związanymi z formantów złożonych przepływu. A <xref:System.Activities.Statements.Flowchart> można tworzyć w kodzie lub za pomocą projektanta przepływów pracy. W tym temacie opisano środowisko projektanta przepływów pracy. Projektant działań przepływu pracy projektanta przepływów pracy umożliwia deweloperom tworzenie przepływów pracy w sposób fizycznych.

## <a name="the-flowchart-activity"></a>Schemat blokowy działania

<xref:System.Activities.Statements.Flowchart> Określa unikatową <xref:System.Activities.Statements.Flowchart.StartNode%2A> który jest wykonywany podczas uruchamiania przepływu pracy i używa połączone z siecią <xref:System.Activities.Statements.Flowchart.Nodes%2A> do utworzenia dowolnego pętli lub przekierowywać przepływ wykonania do dowolnej lokalizacji w przepływie pracy w danym momencie.

### <a name="using-the-flowchart-activity-designer"></a>Przy użyciu narzędzia Projektant działań schematu blokowego

**Schemat blokowy** Projektant działań można znaleźć w **schemat blokowy** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karty w Projektancie przepływów pracy. Można także wybrać **przybornika** z **widoku** menu lub naciśnij klawisz **Ctrl**+**Alt** + **X**.

**Schemat blokowy** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie projektantów działań są zazwyczaj umieszczone, jako działania głównego lub element podrzędny innego działania przepływu sterowania. Jeśli **schemat blokowy** Projektant działań jest przerywane na pusty powierzchnię projektanta przepływów pracy, tworzy <xref:System.Activities.Statements.Flowchart> działania, które domyślnie wyświetla się w widoku rozwiniętego, w którym jest węzeł początkowy, który inicjuje wykonywania reprezentowany jako piłka zielony. Jeśli **schemat blokowy** Projektant działań są przenoszone do innego działania przepływu sterowania, wyświetla się w trybie zminimalizowanym widoku, który można rozszerzać przez dwukrotne kliknięcie **schemat blokowy** Projektant działań. Wszystkie działania w **przybornika** mogą być przeciągnięte bezpośrednio na **schemat blokowy** Projektant działań, włącznie z innymi działaniami przepływu sterowania.

Po przeciąganie różnych projektantów działań na kanwie projektanta przepływów pracy <xref:System.Activities.Activity> reprezentują obiekty mogą być połączone ze sobą, aby określić kolejność wykonywania. Aby utworzyć łącze między działaniem źródła i działanie docelowe, myszą projektanta działania źródłowego i kwadratowe uchwyty są wyświetlane na każdej stronie. Jednym z kwadratowych uchwytów kliknij i przeciągnij go, przytrzymując przycisk myszy, aby jeden dojść, które jest wyświetlany w podobny sposób wokół działania docelowego, gdy kursor myszy nad nim przy użyciu myszy. Zwolnij przycisk myszy, a tworzone jest połączenie tych dwóch działań, które jest reprezentowany jako strzałka z projektanta źródła do projektanta docelowego.

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