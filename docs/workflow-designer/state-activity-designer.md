---
title: Projektant przepływu pracy — Projektant stanu działania
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 41abc73cce121ae4ebc247e20c0fcd2c60b8ec56
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="state-activity-designer"></a>Projektant działań stanu

A <xref:System.Activities.Statements.State> reprezentuje stan, w którym mogą mieć automatu stanów.

## <a name="using-the-state-activity-designer"></a>Przy użyciu narzędzia Projektant stanu działania

Aby dodać <xref:System.Activities.Statements.State> do przepływu pracy, przeciągnij **stanu** Projektant działań z **automatu stanów** sekcji **przybornika** i upuść ją na do <xref:System.Activities.Statements.StateMachine> działanie na powierzchni projektanta przepływów pracy systemu Windows. A <xref:System.Activities.Statements.State> działania mogą być upuszczone na <xref:System.Activities.Statements.StateMachine> i przejść, dodane później; lub przejście może zostać utworzony jako <xref:System.Activities.Statements.State> działanie zostało porzucone. Aby dodać <xref:System.Activities.Statements.State> działania i utworzyć przejście w jednym kroku, przeciągnij **stanu** działania z **automatu stanów** sekcji **przybornika** i aktywuj go innym Stan w Projektancie przepływów pracy. Gdy przeciąganego <xref:System.Activities.Statements.State> znajduje się nad innym <xref:System.Activities.Statements.State>, cztery trójkąty pojawi się wokół innych <xref:System.Activities.Statements.State>. Jeśli <xref:System.Activities.Statements.State> jest przerywane na jedną z czterech trójkąty, jest ona dodawana do automatu stanów i utworzeniu przejście ze źródła <xref:System.Activities.Statements.State> porzuconych docelowego <xref:System.Activities.Statements.State>. Aby uzyskać więcej informacji, zobacz [przejścia](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Właściwości stanu aktywności w Projektancie przepływów pracy

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.State> właściwości, które można ustawić za pomocą projektanta przepływów pracy i w tym artykule opisano, jak są używane w projektancie. Niektóre z tych właściwości można edytować w siatce właściwości i niektóre można edytowane na powierzchnię projektanta.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.State> Projektant działań w nagłówku. Wartość domyślna to **stanu**. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku Projektant działań. <xref:System.Activities.Statements.State.DisplayName%2A> Jest używany w nadrzędnych, który jest wyświetlany w górnej części projektanta przepływów pracy.<br /><br /> Mimo że <xref:System.Activities.Statements.State.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jej użyć.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Określa akcję wykonywaną, gdy ten stan jest optymalizowane pod. Gdy <xref:System.Activities.Statements.State> działania jest rozwinięty, tę wartość można ustawić przez przeciągnięcie działania z **przybornika** i upuszczanie go na **wpis** sekcji stanu.|
|<xref:System.Activities.Statements.State.Exit%2A>|False|Określa akcję wykonywaną, gdy ten stan jest optymalizowane od. Gdy <xref:System.Activities.Statements.State> działania jest rozwinięty, tę wartość można ustawić przez przeciągnięcie działania z **przybornika** i upuszczanie go na **zakończenia** sekcji stanu.|
|<xref:System.Activities.Statements.State.Transitions%2A>|False|Wyświetla listę możliwości przejścia, które pochodzą ze <xref:System.Activities.Statements.State>. Każdy element na liście znajduje się łącze do skojarzonego <xref:System.Activities.Statements.Transition> i miejsce docelowe <xref:System.Activities.Statements.State>. Kliknięcie łącza przechodzi do rozwiniętego widoku Projektanta <xref:System.Activities.Statements.Transition> lub <xref:System.Activities.Statements.State>.|

## <a name="see-also"></a>Zobacz także

- [Obiekt StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [Stan końcowy](../workflow-designer/finalstate-activity-designer.md)
- [przejścia](../workflow-designer/transition-activity-designer.md)