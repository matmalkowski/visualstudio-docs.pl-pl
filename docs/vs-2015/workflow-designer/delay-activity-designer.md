---
title: Opóźnienie, Projektant działań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 012d5b9a9bb39221c5c9babdcf8010e28a24cb59
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42695446"
---
# <a name="delay-activity-designer"></a>Delay, projektant działań
**Opóźnienie** projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Delay> działania.  
  
## <a name="the-delay-activity"></a>Działanie opóźnienia  
 <xref:System.Activities.Statements.Delay> Działania opóźnia wykonywania przepływu pracy przez określony przedział czasu.  
  
### <a name="using-the-delay-activity-designer"></a>Za pomocą Delay, Projektant działań  
 **Opóźnienie** projektanta działań można znaleźć w **podstawowych** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karcie [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać **narzędzi** z **widoku** menu lub klawiszy CTRL + ALT + X.)  
  
 **Opóźnienie** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie działań są zwyczajowo umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Delay> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z opóźnieniem. <xref:System.Activities.Activity.DisplayName%2A> Mogą być edytowane w nagłówku **opóźnienie** projektanta działań lub **DisplayName** pola siatki właściwości.  
  
### <a name="the-delay-properties"></a>Właściwości opóźnienia  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Delay> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości i ich niektóre mogą być edytowane w [!INCLUDE[wfd2](../includes/wfd2-md.md)]powierzchni projektowej.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.Delay> działania. Wartość domyślna to opóźnienie. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest bezwzględnie konieczne, jest najlepszym rozwiązaniem, aby użyć jednego.|  
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Ilość czasu, opóźnienie przepływu pracy. Ta właściwość jest ustawiona w siatce właściwości. Wpisz jeden literał <xref:System.TimeSpan> w formacie 00:00:00 lub wyrażenie języka Visual Basic, aby określić ilość czasu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy podstawowe](../workflow-designer/primitives-activity-designers.md)   
 [Przypisz](../workflow-designer/assign-activity-designer.md)   
 [DELAY, Projektant działań](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)