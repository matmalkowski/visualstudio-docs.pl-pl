---
title: Projektant przepływu pracy — starsze działania przepływu pracy
ms.date: 01/18/2017
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 45c24c0be518e58ce87af11a38486818ca4a3ac7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="legacy-workflow-activities"></a>Działania przepływu pracy w starszej wersji

Windows Workflow Foundation (WF) zawiera domyślny zestaw działań, które zapewnienia funkcji przepływu sterowania, warunki obsługi zdarzeń, zarządzanie stanem i komunikacji z aplikacjami i usługami. Podczas projektowania przepływów pracy, można użyć działania dostarczane przez system, które są udostępniane przez projektanta przepływów pracy systemu Windows lub utworzeniu własnych działań niestandardowych.

W poniższej tabeli wymieniono zestawu działań out-of-box framework Windows Workflow Foundation. Wiele, ale nie wszystkich tych działań są reprezentowane przez projektantów działań, które są dostępne z **przybornika** z projektanta przepływów pracy. Aby utworzyć działanie, przeciągnij jego projektanta z **przybornika** i upuść ją na powierzchni projektu.

|Działanie|Opis|
|--------------|-----------------|
|<xref:System.Workflow.Activities.CallExternalMethodActivity>|Używane z **działanie HandleExternalEventActivity** działania wejściowymi i wyjściowymi komunikacji z lokalną usługą. Aby uzyskać więcej informacji, zobacz [za pomocą działania CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|
|**System.Workflow.Activities.CancellationHandlerActivity**|Zawiera logikę oczyszczania dla działań złożonych anulowana, zanim wszystkie działania złożonego jego elementy podrzędne są gotowe wykonywania. Aby uzyskać więcej informacji, zobacz [za pomocą działania CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|
|<xref:System.Workflow.Activities.CodeActivity>|Umożliwia dodanie kodu języka Visual Basic lub C# do przepływu pracy. Aby uzyskać więcej informacji, zobacz [za pomocą działania z typu CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|
|<xref:System.Workflow.Activities.CompensatableSequenceActivity>|Możliwy do kompensacji wersji <xref:System.Workflow.Activities.SequenceActivity>. Aby uzyskać więcej informacji, zobacz [za pomocą działania CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|
|**System.Workflow.Activities.CompensatableTransactionScopeActivity**|Możliwy do kompensacji wersji **działania TransactionScopeActivity**. Aby uzyskać więcej informacji, zobacz [za pomocą działania CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|
|**System.Workflow.Activities.CompensateActivity**|Umożliwia wywołanie kodu cofnąć lub kompensacji operacje już wykonywane przez przepływ pracy po wystąpieniu błędu. Aby uzyskać więcej informacji, zobacz [za pomocą działania Działanie CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|
|**System.Workflow.Activities.CompensationHandlerActivity**|Otoka dla jednego lub kilku działań wykonujących kompensację ukończone działaniu TransactionScopeActivity, aby uzyskać więcej informacji, zobacz [za pomocą działania CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|
|<xref:System.Workflow.Activities.ConditionedActivityGroup>|Wykonuje działania podrzędnego, na podstawie warunku, który dotyczy <xref:System.Workflow.Activities.ConditionedActivityGroup> działania samego i na podstawie warunków, które są stosowane osobno do każdego elementu podrzędnego. Aby uzyskać więcej informacji, zobacz [za pomocą działania grupy ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|
|<xref:System.Workflow.Activities.DelayActivity>|Umożliwia tworzenie opóźnień w przepływie pracy, które są oparte na interwał limitu czasu. Aby uzyskać więcej informacji, zobacz [przy użyciu Działanie DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|
|<xref:System.Workflow.Activities.EventDrivenActivity>|Opakowuje jedno lub więcej działań, które są wykonywane, gdy wystąpi określone zdarzenie. Aby uzyskać więcej informacji, zobacz [przy użyciu działanie EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|
|<xref:System.Workflow.Activities.EventHandlersActivity>|Zapewnia platformę do kojarzenia zdarzenia z działania. Aby uzyskać więcej informacji, zobacz [przy użyciu działanie EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|
|<xref:System.Workflow.Activities.EventHandlingScopeActivity>|Wykonuje jego działanie podrzędne głównego równocześnie z <xref:System.Workflow.Activities.EventHandlersActivity>. Aby uzyskać więcej informacji, zobacz [za pomocą działania EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|
|**System.Workflow.Activities.FaultHandlerActivity**|Używane do obsługi wyjątku typu, który określisz. Aby uzyskać więcej informacji, zobacz [przy użyciu działanie FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|
|**System.Workflow.Activities.FaultHandlersActivity**|Reprezentuje złożonego działanie, które ma uporządkowaną listę działań podrzędnych typu **System.Workflow.Activities.FaultHandlerActivity**. Aby uzyskać więcej informacji, zobacz [przy użyciu działanie FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|
|<xref:System.Workflow.Activities.HandleExternalEventActivity>|Używane w połączeniu z <xref:System.Workflow.Activities.CallExternalMethodActivity> działania wejściowymi i wyjściowymi komunikacji z lokalną usługą. Aby uzyskać więcej informacji, zobacz [za pomocą działania działanie HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|
|<xref:System.Workflow.Activities.IfElseActivity>|Sprawdza stan każdej gałęzi i wykonuje działania na pierwszej gałęzi, dla którego warunku jest równe **true**. Aby uzyskać więcej informacji, zobacz [przy użyciu działanie IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|
|<xref:System.Workflow.Activities.IfElseBranchActivity>|Reprezentuje gałąź <xref:System.Workflow.Activities.IfElseActivity>. Aby uzyskać więcej informacji, zobacz [za pomocą działania IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|
|<xref:System.Workflow.Activities.InvokeWebServiceActivity>|Umożliwia przepływ pracy do wywołania usługi sieci Web. Aby uzyskać więcej informacji, zobacz [za pomocą działania działaniu InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|
|<xref:System.Workflow.Activities.InvokeWorkflowActivity>|Umożliwia przepływ pracy do wywołania innego przepływu pracy. Aby uzyskać więcej informacji, zobacz [za pomocą działania działania InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|
|<xref:System.Workflow.Activities.ListenActivity>|Działanie złożone, który zawiera tylko <xref:System.Workflow.Activities.EventDrivenActivity> działań podrzędnych. Aby uzyskać więcej informacji, zobacz [za pomocą działania Działanie ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|
|<xref:System.Workflow.Activities.ParallelActivity>|Umożliwia zaplanowanie dwóch lub więcej podrzędnych **to SequenceActivity** gałęzie działania do przetworzenia w tym samym czasie. Aby uzyskać więcej informacji, zobacz [za pomocą działania ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|
|<xref:System.Workflow.Activities.PolicyActivity>|Używany do reprezentowania kolekcji reguł. Reguła składa się z warunków i wynikowy akcji. Aby uzyskać więcej informacji, zobacz [za pomocą działania działania PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|
|<xref:System.Workflow.Activities.ReplicatorActivity>|Tworzy wiele wystąpień działaniem podrzędnym jednego. Aby uzyskać więcej informacji, zobacz [przy użyciu działanie ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|
|<xref:System.Workflow.Activities.SequenceActivity>|Zapewnia prosty sposób łączenia wielu działań do wykonywania sekwencyjnego. Aby uzyskać więcej informacji, zobacz [za pomocą działania to SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|
|<xref:System.Workflow.Activities.SetStateActivity>|Określa przejście do nowego stanu. Aby uzyskać więcej informacji, zobacz [za pomocą działania SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|
|<xref:System.Workflow.Activities.StateActivity>|Reprezentuje stan w przepływ pracy automatu stanów. Aby uzyskać więcej informacji, zobacz [za pomocą działania działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|
|<xref:System.Workflow.Activities.StateFinalizationActivity>|Używane w <xref:System.Workflow.Activities.StateActivity> działania jako kontener dla działania podrzędne, które są wykonywane podczas opuszczania **działanie StateActivity** działania. Aby uzyskać więcej informacji, zobacz [za pomocą działania StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|
|<xref:System.Workflow.Activities.StateInitializationActivity>|Używane w <xref:System.Workflow.Activities.StateActivity> działania jako kontener dla działania podrzędne, które są wykonywane podczas wprowadzania **działanie StateActivity** działania. Aby uzyskać więcej informacji, zobacz [za pomocą działania StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|
|**System.Workflow.Activities.SuspendActivity**|Wstrzymuje działanie do przepływu pracy, aby włączyć interwencji w przypadku niektórych warunek błędu, który wymaga specjalnej uwagi. Aby uzyskać więcej informacji, zobacz [za pomocą działania działanie SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|
|**System.Workflow.Activities.SynchronizationScopeActivity**|Wykonuje zawarte działania sekwencyjnie w zsynchronizowanej domenie. Aby uzyskać więcej informacji, zobacz [za pomocą działania SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|
|**System.Workflow.Activities.TerminateActivity**|Umożliwia natychmiastowe zakończenie działania przepływu pracy w przypadku warunek błędu. Aby uzyskać więcej informacji, zobacz [za pomocą działania TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|
|**System.Workflow.Activities.ThrowActivity**|Umożliwia przechwytywanie wyjątków firm zgłoszonych jako część procesu metadanych dla przepływu pracy. Aby uzyskać więcej informacji, zobacz [za pomocą działania ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|
|**System.Workflow.Activities.TransactionScopeActivity**|Dostarcza strukturę dla transakcji i obsługi wyjątków. Aby uzyskać więcej informacji, zobacz [przy użyciu działaniu TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|
|<xref:System.Workflow.Activities.WebServiceFaultActivity>|Umożliwia to model wystąpienie awarii usługi sieci Web. Aby uzyskać więcej informacji, zobacz [za pomocą działania WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|
|<xref:System.Workflow.Activities.WebServiceInputActivity>|Odbiera dane z usługi sieci Web. Aby uzyskać więcej informacji, zobacz [za pomocą działania działania WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|
|<xref:System.Workflow.Activities.WebServiceOutputActivity>|Odpowiada na żądanie usługi sieci Web do przepływu pracy. Aby uzyskać więcej informacji, zobacz [za pomocą działania WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|
|<xref:System.Workflow.Activities.WhileActivity>|Umożliwia przepływu pracy w pętli do momentu spełnienia warunku. Aby uzyskać więcej informacji, zobacz [za pomocą działania Działanie WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|

Aby uzyskać więcej informacji na temat tworzenia niestandardowych działań, zobacz [tworzenia działań niestandardowych](http://go.microsoft.com/fwlink?LinkID=65023) i [przy użyciu narzędzia Projektant działań starszych](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="see-also"></a>Zobacz także

- [Działań w systemie Windows Workflow Foundation](http://go.microsoft.com/fwlink?LinkID=65005)
- [Tworzenie przepływów pracy](http://go.microsoft.com/fwlink?LinkID=65010)
- [Tworzenie działań przepływu pracy](http://go.microsoft.com/fwlink?LinkID=65023)