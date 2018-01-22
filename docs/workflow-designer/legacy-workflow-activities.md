---
title: "Działania przepływu pracy starszego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: ae0cef2943abffe947c179f9cfcd6c2223931337
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2018
---
# <a name="legacy-workflow-activities"></a>Działania przepływu pracy w starszej wersji
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]zawiera zestaw domyślne działania udostępniające funkcje dla przepływu sterowania, warunki obsługi zdarzeń, zarządzanie stanem i komunikacji z aplikacjami i usługami. Podczas projektowania przepływów pracy, można użyć działania dostarczane przez system, które są udostępniane przez [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)], lub utworzyć własne niestandardowe działania.  
  
 W poniższej tabeli wymieniono [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] zestawu działań out-of-box framework. Wiele, ale nie wszystkich tych działań są reprezentowane przez projektantów działań, które są dostępne z **przybornika** z [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Aby utworzyć działanie, przeciągnij jego projektanta z **przybornika** i upuść ją na powierzchni projektu.  
  
|Działanie|Opis|  
|--------------|-----------------|  
|<xref:System.Workflow.Activities.CallExternalMethodActivity>|Używane z **działanie HandleExternalEventActivity** działania wejściowymi i wyjściowymi komunikacji z lokalną usługą. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|  
|**System.Workflow.Activities.CancellationHandlerActivity**|Zawiera logikę oczyszczania dla działań złożonych anulowana, zanim wszystkie działania złożonego jego elementy podrzędne są gotowe wykonywania. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|  
|<xref:System.Workflow.Activities.CodeActivity>|Umożliwia dodanie kodu języka Visual Basic lub C# do przepływu pracy. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania z typu CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|  
|<xref:System.Workflow.Activities.CompensatableSequenceActivity>|Możliwy do kompensacji wersji <xref:System.Workflow.Activities.SequenceActivity>. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|  
|**System.Workflow.Activities.CompensatableTransactionScopeActivity**|Możliwy do kompensacji wersji **działania TransactionScopeActivity**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|  
|**System.Workflow.Activities.CompensateActivity**|Umożliwia wywołanie kodu cofnąć lub kompensacji operacje już wykonywane przez przepływ pracy po wystąpieniu błędu. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania Działanie CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|  
|**System.Workflow.Activities.CompensationHandlerActivity**|Otoka dla jednego lub kilku działań wykonujących kompensację ukończone działaniu TransactionScopeActivity [!INCLUDE[crdefault](../test/includes/crdefault_md.md)] [za pomocą działania CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|  
|<xref:System.Workflow.Activities.ConditionedActivityGroup>|Wykonuje działania podrzędnego, na podstawie warunku, który dotyczy <xref:System.Workflow.Activities.ConditionedActivityGroup> działania samego i na podstawie warunków, które są stosowane osobno do każdego elementu podrzędnego. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania grupy ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|  
|<xref:System.Workflow.Activities.DelayActivity>|Umożliwia tworzenie opóźnień w przepływie pracy, które są oparte na interwał limitu czasu. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Przy użyciu Działanie DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|  
|<xref:System.Workflow.Activities.EventDrivenActivity>|Opakowuje jedno lub więcej działań, które są wykonywane, gdy wystąpi określone zdarzenie. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Przy użyciu działanie EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
|<xref:System.Workflow.Activities.EventHandlersActivity>|Zapewnia platformę do kojarzenia zdarzenia z działania. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Przy użyciu działanie EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|  
|<xref:System.Workflow.Activities.EventHandlingScopeActivity>|Wykonuje jego działanie podrzędne głównego równocześnie z <xref:System.Workflow.Activities.EventHandlersActivity>. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|  
|**System.Workflow.Activities.FaultHandlerActivity**|Używane do obsługi wyjątku typu, który określisz. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Przy użyciu działanie FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|  
|**System.Workflow.Activities.FaultHandlersActivity**|Reprezentuje złożonego działanie, które ma uporządkowaną listę działań podrzędnych typu **System.Workflow.Activities.FaultHandlerActivity**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Przy użyciu działanie FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|  
|<xref:System.Workflow.Activities.HandleExternalEventActivity>|Używane w połączeniu z <xref:System.Workflow.Activities.CallExternalMethodActivity> działania wejściowymi i wyjściowymi komunikacji z lokalną usługą. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania działanie HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|  
|<xref:System.Workflow.Activities.IfElseActivity>|Sprawdza stan każdej gałęzi i wykonuje działania na pierwszej gałęzi, dla którego warunku jest równe **true**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Przy użyciu działanie IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|  
|<xref:System.Workflow.Activities.IfElseBranchActivity>|Reprezentuje gałąź <xref:System.Workflow.Activities.IfElseActivity>. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|  
|<xref:System.Workflow.Activities.InvokeWebServiceActivity>|Umożliwia przepływ pracy do wywołania usługi sieci Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania działaniu InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|  
|<xref:System.Workflow.Activities.InvokeWorkflowActivity>|Umożliwia przepływ pracy do wywołania innego przepływu pracy. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania działania InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|  
|<xref:System.Workflow.Activities.ListenActivity>|Działanie złożone, który zawiera tylko <xref:System.Workflow.Activities.EventDrivenActivity> działań podrzędnych. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania Działanie ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|  
|<xref:System.Workflow.Activities.ParallelActivity>|Umożliwia zaplanowanie dwóch lub więcej podrzędnych **to SequenceActivity** gałęzie działania do przetworzenia w tym samym czasie. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|  
|<xref:System.Workflow.Activities.PolicyActivity>|Używany do reprezentowania kolekcji reguł. Reguła składa się z warunków i wynikowy akcji. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania działania PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|<xref:System.Workflow.Activities.ReplicatorActivity>|Tworzy wiele wystąpień działaniem podrzędnym jednego. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Przy użyciu działanie ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|  
|<xref:System.Workflow.Activities.SequenceActivity>|Zapewnia prosty sposób łączenia wielu działań do wykonywania sekwencyjnego. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania to SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|  
|<xref:System.Workflow.Activities.SetStateActivity>|Określa przejście do nowego stanu. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|<xref:System.Workflow.Activities.StateActivity>|Reprezentuje stan w przepływ pracy automatu stanów. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|<xref:System.Workflow.Activities.StateFinalizationActivity>|Używane w <xref:System.Workflow.Activities.StateActivity> działania jako kontener dla działania podrzędne, które są wykonywane podczas opuszczania **działanie StateActivity** działania. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|<xref:System.Workflow.Activities.StateInitializationActivity>|Używane w <xref:System.Workflow.Activities.StateActivity> działania jako kontener dla działania podrzędne, które są wykonywane podczas wprowadzania **działanie StateActivity** działania. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|  
|**System.Workflow.Activities.SuspendActivity**|Wstrzymuje działanie do przepływu pracy, aby włączyć interwencji w przypadku niektórych warunek błędu, który wymaga specjalnej uwagi. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania działanie SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|  
|**System.Workflow.Activities.SynchronizationScopeActivity**|Wykonuje zawarte działania sekwencyjnie w zsynchronizowanej domenie. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|  
|**System.Workflow.Activities.TerminateActivity**|Umożliwia natychmiastowe zakończenie działania przepływu pracy w przypadku warunek błędu. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|  
|**System.Workflow.Activities.ThrowActivity**|Umożliwia przechwytywanie wyjątków firm zgłoszonych jako część procesu metadanych dla przepływu pracy. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|  
|**System.Workflow.Activities.TransactionScopeActivity**|Dostarcza strukturę dla transakcji i obsługi wyjątków. Aby uzyskać więcej informacji, zobacz [przy użyciu działaniu TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|  
|<xref:System.Workflow.Activities.WebServiceFaultActivity>|Umożliwia to model wystąpienie awarii usługi sieci Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|  
|<xref:System.Workflow.Activities.WebServiceInputActivity>|Odbiera dane z usługi sieci Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania działania WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|  
|<xref:System.Workflow.Activities.WebServiceOutputActivity>|Odpowiada na żądanie usługi sieci Web do przepływu pracy. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|  
|<xref:System.Workflow.Activities.WhileActivity>|Umożliwia przepływu pracy w pętli do momentu spełnienia warunku. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania Działanie WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]sposób tworzenia działań niestandardowych, zobacz [tworzenia działań niestandardowych](http://go.microsoft.com/fwlink?LinkID=65023) i [przy użyciu narzędzia Projektant działań starszych](../workflow-designer/using-the-legacy-activity-designer.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Widoki działania (starsza wersja)](../workflow-designer/activity-views-legacy.md)  
 Zawiera opis widoków projektu różnych działań.  
  
 [Instrukcje: Dodawanie działań do przybornika (starsza wersja)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 Przedstawiono sposób dodawania działań do przybornika.  
  
 [Instrukcje: Tworzenie warunku reguły deklaratywnej (starsza wersja)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 Przedstawia kroki, aby utworzyć warunek reguły deklaratywne.  
  
 [Instrukcje: Tworzenie zestawu reguł działania PolicyActivity (starsza wersja)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 Przedstawia kroki, aby utworzyć zestaw reguł działania PolicyActivity.  
  
 [Porady: Implementowanie operacja kontraktu usługi WCF (starsze)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 Przedstawia kroki, aby zaimplementować [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] kontraktu operacji.  
  
 [Porady: wywoływanie operacja kontraktu usługi WCF (starsze)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)  
 Przedstawia kroki, aby wywołać [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] kontraktu operacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Działań w systemie Windows Workflow Foundation](http://go.microsoft.com/fwlink?LinkID=65005)   
 [Tworzenie przepływów pracy](http://go.microsoft.com/fwlink?LinkID=65010)   
 [Tworzenie działań przepływu pracy](http://go.microsoft.com/fwlink?LinkID=65023)