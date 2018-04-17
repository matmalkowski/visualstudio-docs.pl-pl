---
title: Projektant działań stan końcowy | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 6360be9522fd8a3640780407cb5252da41515536
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="finalstate-activity-designer"></a>Projektant działań stan końcowy
<xref:System.Activities.Core.Presentation.FinalState> Projektant służy do tworzenia <xref:System.Activities.Statements.State> kończy się wystąpieniem komputera stanu.

## <a name="using-the-finalstate-activity-designer"></a>Przy użyciu narzędzia Projektant działań stan końcowy
 **Stan końcowy** Projektant służy do tworzenia <xref:System.Activities.Statements.State> który jest wstępnie skonfigurowana jako powodujący przerwanie stan komputera stanu. A <xref:System.Activities.Statements.State> utworzonego przy użyciu <xref:System.Activities.Core.Presentation.FinalState> ma Projektant działań jego <xref:System.Activities.Statements.State.IsFinal%2A> ustawioną właściwość **true**, nie ma <xref:System.Activities.Statements.State.Exit%2A> działania i żadnych przejść pochodzącego od niego. Aby użyć <xref:System.Activities.Core.Presentation.FinalState> Projektant działań, aby dodać <xref:System.Activities.Statements.State> przeciągnij działanie, które jest wstępnie konfigurowany jako powodujący przerwanie stan w automacie stanów **stan końcowy** Projektant działań z **automatu stanów**części **przybornika** i upuścić projektanta przepływów pracy. <xref:System.Activities.Core.Presentation.FinalState> Projektant działań mogą być upuszczone na <xref:System.Activities.Statements.StateMachine> i przejść, dodane później; lub przejście może zostać utworzony jako <xref:System.Activities.Core.Presentation.FinalState> Projektant działań zostało porzucone. Aby uzyskać więcej informacji na temat tworzenia przejścia, zobacz [przejścia](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Właściwości stanu aktywności w Projektancie przepływów pracy
 W poniższej tabeli przedstawiono właściwości, które można ustawić za pomocą <xref:System.Activities.Core.Presentation.FinalState> projektanta i opisuje, jak są używane w projektancie. Niektóre z tych właściwości można edytować w siatce właściwości i niektóre można edytowane na powierzchnię projektanta.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.State> Projektant działań w nagłówku. Wartość domyślna to **stanu**. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku Projektant działań. <xref:System.Activities.Statements.State.DisplayName%2A> Jest używany w nadrzędnych, który jest wyświetlany w górnej części projektanta przepływów pracy.<br /><br /> Mimo że <xref:System.Activities.Statements.State.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jej użyć.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Określa akcję wykonywaną, gdy ten stan jest optymalizowane pod. Tę wartość można ustawić przez przeciągnięcie działania z **przybornika** i upuszczanie go na <xref:System.Activities.Statements.State.Entry%2A> sekcji stanu.|

## <a name="see-also"></a>Zobacz także

- [Obiekt StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [Stan](../workflow-designer/state-activity-designer.md)
- [przejścia](../workflow-designer/transition-activity-designer.md)