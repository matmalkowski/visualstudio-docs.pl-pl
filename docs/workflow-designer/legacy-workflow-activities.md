---
title: "Działania przepływu pracy starszego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
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
ms.openlocfilehash: 756fa86cf892120b0062e2816f146425ac1b4fa3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="legacy-workflow-activities"></a>Działania przepływu pracy w starszej wersji
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]zawiera zestaw domyślne działania udostępniające funkcje dla przepływu sterowania, warunki obsługi zdarzeń, zarządzanie stanem i komunikacji z aplikacjami i usługami. Podczas projektowania przepływów pracy, można użyć działania dostarczane przez system, które są udostępniane przez [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)], lub utworzyć własne niestandardowe działania.  
  
 W poniższej tabeli wymieniono [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] zestawu działań out-of-box framework. Wiele, ale nie wszystkich tych działań są reprezentowane przez projektantów działań, które są dostępne z **przybornika** z [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Aby utworzyć działanie, przeciągnij jego projektanta z **przybornika** i upuść ją na powierzchni projektu.  
  
|Działanie|Opis|  
|--------------|-----------------|  
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|Używane z **działanie HandleExternalEventActivity** działania wejściowymi i wyjściowymi komunikacji z lokalną usługą. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|  
|[Działania CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|Zawiera logikę oczyszczania dla działań złożonych anulowana, zanim wszystkie działania złożonego jego elementy podrzędne są gotowe wykonywania. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|  
|[Klasy CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Umożliwia dodanie kodu języka Visual Basic lub C# do przepływu pracy. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania z typu CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|  
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|Możliwy do kompensacji wersji [to SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|  
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|Możliwy do kompensacji wersji **działania TransactionScopeActivity**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|  
|[Działanie CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|Umożliwia wywołanie kodu cofnąć lub kompensacji operacje już wykonywane przez przepływ pracy po wystąpieniu błędu. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania Działanie CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|  
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|Otoka dla jednego lub kilku działań wykonujących kompensację ukończone działaniu TransactionScopeActivity [!INCLUDE[crdefault](../test/includes/crdefault_md.md)] [za pomocą działania CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|  
|[Grupy ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|Wykonuje działania podrzędnego, na podstawie warunku, który dotyczy [grupy ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) działania samego i na podstawie warunków, które są stosowane osobno do każdego elementu podrzędnego. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania grupy ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|  
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|Umożliwia tworzenie opóźnień w przepływie pracy, które są oparte na interwał limitu czasu. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Przy użyciu Działanie DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Opakowuje jedno lub więcej działań, które są wykonywane, gdy wystąpi określone zdarzenie. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Przy użyciu działanie EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
|[Działanie EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Zapewnia platformę do kojarzenia zdarzenia z działania. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Przy użyciu działanie EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|  
|[Działanie EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Wykonuje jego działanie podrzędne głównego równocześnie z [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|  
|[Działanie FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Używane do obsługi wyjątku typu, który określisz. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Przy użyciu działanie FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|  
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|Reprezentuje złożonego działanie, które ma uporządkowaną listę działań podrzędnych typu [FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Przy użyciu działanie FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|  
|[Działanie HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|Używane w połączeniu z [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) działania wejściowymi i wyjściowymi komunikacji z lokalną usługą. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania działanie HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|  
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Sprawdza stan każdej gałęzi i wykonuje działania na pierwszej gałęzi, dla którego warunku jest równe **true**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Przy użyciu działanie IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|  
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|Reprezentuje gałąź [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|  
|[Działaniu InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Umożliwia przepływ pracy do wywołania usługi sieci Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania działaniu InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|  
|[Działania InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|Umożliwia przepływ pracy do wywołania innego przepływu pracy. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania działania InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|  
|[Działanie ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|Działanie złożone, który zawiera tylko [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029) działań podrzędnych. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania Działanie ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|  
|[Typem ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|Umożliwia zaplanowanie dwóch lub więcej podrzędnych **to SequenceActivity** gałęzie działania do przetworzenia w tym samym czasie. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|  
|[Działania PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|Używany do reprezentowania kolekcji reguł. Reguła składa się z warunków i wynikowy akcji. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania działania PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|[Działanie ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|Tworzy wiele wystąpień działaniem podrzędnym jednego. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Przy użyciu działanie ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|  
|[To SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Zapewnia prosty sposób łączenia wielu działań do wykonywania sekwencyjnego. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania to SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|  
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Określa przejście do nowego stanu. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|[Działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Reprezentuje stan w przepływ pracy automatu stanów. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Używane w [działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) działania jako kontener dla działania podrzędne, które są wykonywane podczas opuszczania **działanie StateActivity** działania. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Używane w [działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) działania jako kontener dla działania podrzędne, które są wykonywane podczas wprowadzania **działanie StateActivity** działania. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|  
|[Działanie SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Wstrzymuje działanie do przepływu pracy, aby włączyć interwencji w przypadku niektórych warunek błędu, który wymaga specjalnej uwagi. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania działanie SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|  
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|Wykonuje zawarte działania sekwencyjnie w zsynchronizowanej domenie. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|  
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|Umożliwia natychmiastowe zakończenie działania przepływu pracy w przypadku warunek błędu. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|  
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|Umożliwia przechwytywanie wyjątków firm zgłoszonych jako część procesu metadanych dla przepływu pracy. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|  
|[Działanie TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|Dostarcza strukturę dla transakcji i obsługi wyjątków. Aby uzyskać więcej informacji, zobacz [przy użyciu działaniu TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|  
|[Działanie WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Umożliwia to model wystąpienie awarii usługi sieci Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|  
|[Działania WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Odbiera dane z usługi sieci Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania działania WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|  
|[Działanie WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|Odpowiada na żądanie usługi sieci Web do przepływu pracy. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|  
|[Działanie WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|Umożliwia przepływu pracy w pętli do momentu spełnienia warunku. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Za pomocą działania Działanie WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|  
  
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