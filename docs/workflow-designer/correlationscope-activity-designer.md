---
title: "Projektant działań CorrelationScope | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3e6e745e470c5e5b5a279f460198729bd9429ccc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="correlationscope-activity-designer"></a>Projektant działań CorrelationScope
**CorrelationScope** Projektant działań służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.CorrelationScope> działanie, które umożliwia zarządzanie niejawne komunikatów działań podrzędnych za pomocą <xref:System.ServiceModel.Activities.CorrelationHandle> obiektu.  
  
## <a name="the-correlationscope-activity"></a>Działanie CorrelationScope  
 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> Właściwość określa <xref:System.ServiceModel.Activities.CorrelationHandle> używany do zarządzania wiadomości działań podrzędnych. <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> działań zawartych w <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> są skonfigurowane do używania <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> właściwość zawierający <xref:System.ServiceModel.Activities.CorrelationScope> działanie korelacji.  
  
### <a name="using-the-correlationscope-activity-designer"></a>Przy użyciu narzędzia Projektant działań CorrelationScope  
 **CorrelationScope** Projektant działań można znaleźć w **wiadomości** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** karcie po lewej stronie [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)  
  
 **CorrelationScope** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.CorrelationScope> działania z domyślną **DisplayName** z CorrelationScope. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **CorrelationScope** Projektant działań lub **DisplayName** pole **właściwości** okna.  
  
 Aby określić <xref:System.ServiceModel.Activities.CorrelationHandle> używany przez podrzędny działań dotyczących komunikatów, kliknij przycisk wielokropka obok **CorrelatesWith** w **właściwości** okno, aby wyświetlić **edytora wyrażeń**  okno dialogowe. Tej właściwości można ustawić w taki sposób, na powierzchni projektowej działania.  
  
 Zakres w korelacji działania są określane przez usunięcie ich projektantów w **treści** polu w **CorrelationScope** projektanta.  
  
### <a name="the-correlationscope-properties"></a>Właściwości CorrelationScope  
 W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.CorrelationScope> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w **właściwości** okna lub na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] projektanta powierzchni i często w obu.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Opcjonalne przyjazna nazwa <xref:System.ServiceModel.Activities.InitializeCorrelation> działania.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Określa <xref:System.ServiceModel.Activities.CorrelationHandle> używany do zarządzania wiadomości działań podrzędnych. Jeśli ta właściwość nie jest ustawiona <xref:System.ServiceModel.Activities.CorrelationScope> tworzy niejawny <xref:System.ServiceModel.Activities.CorrelationHandle> automatycznie.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Określa działań w zakresie korelacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Odbieranie](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Wyślij](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)