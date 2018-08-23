---
title: TerminateWorkflow, Projektant działań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: a00677390967f0cc0cff8a04b33895d7c88588f6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679261"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow, projektant działań
**TerminateWorkflow** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.TerminateWorkflow> działania.  
  
## <a name="the-terminateworkflow-activity"></a>Działanie TerminateWorkflow  
 <xref:System.Activities.Statements.TerminateWorkflow> Działanie kończy wykonywanie przepływu pracy.  
  
### <a name="using-the-terminateworkflow-activity-designer"></a>Za pomocą TerminateWorkflow, Projektant działań  
 **TerminateWorkflow** projektanta działań można znaleźć w **środowiska uruchomieniowego** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** karty (opcjonalnie zaznacz **przybornika** z **widoku** menu lub klawiszy CTRL + ALT + X.)  
  
 **TerminateWorkflow** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zwyczajowo umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.TerminateWorkflow> działanie przy użyciu domyślnego **DisplayName** z TerminateWorkflow. <xref:System.Activities.Activity.DisplayName%2A> Mogą być edytowane w nagłówku **TerminateWorkflow** projektanta działań lub **DisplayName** pola siatki właściwości.  
  
### <a name="the-terminateworkflow-properties"></a>Właściwości TerminateWorkflow  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.TerminateWorkflow> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości i niektóre z nich mogą być edytowane [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.TerminateWorkflow> działania. Wartość domyślna to TerminateWorkflow. Chociaż nazwa wyświetlana nie jest bezwzględnie konieczne, jest najlepszym rozwiązaniem, aby użyć nazwy wyświetlanej.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Wyjątek do zgłaszania, gdy przepływ pracy zostanie zakończony. Ustaw tę właściwość w siatce właściwości.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Powód, który wyjaśnia, dlaczego przepływu pracy zostało zakończone. Ustaw tę właściwość w siatce właściwości.|  
  
## <a name="see-also"></a>Zobacz też  
 [Środowisko uruchomieniowe](../workflow-designer/runtime-activity-designers.md)   
 [Utrwalanie](../workflow-designer/persist-activity-designer.md)