---
title: Projektant działań TerminateWorkflow | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 444ea597fd6c76c8312369afcbc497e640bace6f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="terminateworkflow-activity-designer"></a>Projektant działań TerminateWorkflow
**TerminateWorkflow** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.TerminateWorkflow> działania.

## <a name="the-terminateworkflow-activity"></a>Działanie TerminateWorkflow
 <xref:System.Activities.Statements.TerminateWorkflow> Działanie kończy wykonywanie przepływu pracy.

### <a name="using-the-terminateworkflow-activity-designer"></a>Przy użyciu narzędzia Projektant działań TerminateWorkflow
 **TerminateWorkflow** Projektant działań można znaleźć w **środowiska uruchomieniowego** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** kartę (można także wybrać **przybornika** z **widoku** menu lub CTRL + ALT + X.)

 **TerminateWorkflow** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań zwykle są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.TerminateWorkflow> działania z domyślną **DisplayName** z TerminateWorkflow. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **TerminateWorkflow** Projektant działań lub **DisplayName** pola siatki właściwości.

### <a name="the-terminateworkflow-properties"></a>Właściwości TerminateWorkflow
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.TerminateWorkflow> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości i niektóre z nich można edytowane na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.TerminateWorkflow> działania. Wartość domyślna to TerminateWorkflow. Wyświetlana nazwa nie jest ściśle wymagane, jest najlepszym rozwiązaniem, aby użyć nazwy wyświetlanej.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Wyjątek, który ma zostać zgłoszony, gdy przepływ pracy zostanie zakończony. Tę właściwość można ustawić w siatce właściwości.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Przyczyna wyjaśniający, dlaczego przepływu pracy zostało zakończone. Tę właściwość można ustawić w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [Środowisko uruchomieniowe](../workflow-designer/runtime-activity-designers.md)
- [Utrwalanie](../workflow-designer/persist-activity-designer.md)