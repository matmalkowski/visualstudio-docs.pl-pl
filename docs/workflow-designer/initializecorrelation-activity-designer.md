---
title: "Projektant działań InitializeCorrelation | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 83abd9f76f68ec4131840fb0ea58e9aeb93f30d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="initializecorrelation-activity-designer"></a>Projektant działań InitializeCorrelation
**InitializeCorrelation** Projektant działań służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.InitializeCorrelation> działania, który jest używany do ustanawiania korelacja komunikatów przed wysyłaniu lub odbieraniu je.  
  
## <a name="the-initializecorrelation-activity"></a>Działanie InitializeCorrelation  
 <xref:System.ServiceModel.Activities.InitializeCorrelation> To działanie służy do inicjowania korelacji bez wysyłania i odbierania wiadomości. Zwykle korelacji zainicjowano przy wysyłaniu lub odbieraniu wiadomości. Jeśli przed wysłanego lub odebranego komunikatu, należy ustanowić korelacji, użyj <xref:System.ServiceModel.Activities.InitializeCorrelation> zainicjować korelacji.  
  
### <a name="using-the-initializecorrelation-activity-designer"></a>Przy użyciu narzędzia Projektant działań InitializeCorrelation  
 **InitializeCorrelation** Projektant działań można znaleźć w **wiadomości** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**  karcie na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)  
  
 **InitializeCorrelation** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.InitializeCorrelation> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z InitializeCorrelation.The <xref:System.Activities.Activity.DisplayName%2A> można edytowane w nagłówku **InitializeCorrelation** Projektant działań lub  **Nazwa wyświetlana** pole **właściwości** okna.  
  
 <xref:System.ServiceModel.Activities.CorrelationHandle> Może być Określa **korelacji** w **właściwości** okno na **InitializeCorrelation** działania powierzchnię projektanta.  
  
 Kliknięcie przycisku wielokropka obok **CorrelationData** w **właściwości** okna lub tekst wskazówki "View..." na **InitializeCorrelation** Projektant działań Wyświetla powierzchni **inicjowania korelacji** okno dialogowe, w którym można określić dojścia korelacji i par klucz wartość, można go zainicjować. [!INCLUDE[crabout](../test/includes/crabout_md.md)]za pomocą tego okna dialogowego, zobacz [okno dialogowe Edytor kolekcji typu](../workflow-designer/type-collection-editor-dialog-box.md) tematu.  
  
### <a name="the-initializecorrelation-properties"></a>Właściwości InitializeCorrelation  
 W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.InitializeCorrelation> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w **właściwości** oknie lub na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.ServiceModel.Activities.InitializeCorrelation> działania. Wartość domyślna to InitializeCorrelation.<br /><br /> Mimo że użycie wartości innych niż domyślne dla przyjaznych <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem, aby użyć tych wartości.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> Używanego do kojarzenia działań przepływu pracy w korelacji.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Słownik danych korelacji odnosi się komunikaty do wystąpienia przepływu pracy.<br /><br /> Użyj **inicjowania korelacji** okno dialogowe, aby skonfigurować <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. [!INCLUDE[crabout](../test/includes/crabout_md.md)]Użycie tego okna dialogowego, zobacz [okno dialogowe Edytor kolekcji typu](../workflow-designer/type-collection-editor-dialog-box.md) tematu.|  
  
## <a name="see-also"></a>Zobacz też  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Odbieranie](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Wyślij](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)