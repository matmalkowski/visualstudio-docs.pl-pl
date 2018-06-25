---
title: Projektant przepływu pracy — Projektant działań StateMachine
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9c7afb2131ae6e05c8232eb8dc735e5131698a69
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758235"
---
# <a name="statemachine-activity-designer"></a>StateMachine, projektant działań

<xref:System.Activities.Statements.StateMachine> Działanie zawiera kolekcję stanów i modele przepływów pracy za pomocą modelu maszyny znanego stanu.

## <a name="using-the-statemachine-activity-designer"></a>Przy użyciu narzędzia Projektant działań StateMachine

Aby dodać <xref:System.Activities.Statements.StateMachine> działania, przeciągnij **StateMachine** Projektant działań z **automatu stanów** sekcji **przybornika** i upuść go do projektanta przepływów pracy powierzchni. Aby dodać stan podrzędnych do tego <xref:System.Activities.Statements.StateMachine> działania, przeciągnij <xref:System.Activities.Statements.State> lub <xref:System.Activities.Core.Presentation.FinalState> z **przybornika** i upuść ją na **StateMachine**.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Obiekt StateMachine właściwości działania w Projektancie przepływów pracy

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.StateMachine> właściwości, które można ustawić za pomocą projektanta przepływów pracy i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości i niektóre można edytowane na powierzchnię projektanta.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.StateMachine> Projektant działań w nagłówku. Wartość domyślna to **StateMachine**. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku Projektant działań. <xref:System.Activities.Activity.DisplayName%2A> Jest używany w nadrzędnych, który jest wyświetlany w górnej części projektanta przepływów pracy.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jej użyć.|

## <a name="see-also"></a>Zobacz także

- [Schemat blokowy](../workflow-designer/flowchart-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)