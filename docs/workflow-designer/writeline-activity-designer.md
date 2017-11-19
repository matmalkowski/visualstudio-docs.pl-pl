---
title: "Projektant działań WriteLine | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 615cfb46222dfbf6e6b3cb1ba6741cde7c7bf708
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="writeline-activity-designer"></a>Projektant działań WriteLine
**WriteLine** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.WriteLine> działania.  
  
## <a name="the-writeline-activity"></a>Działanie WriteLine  
 <xref:System.Activities.Statements.WriteLine> Działania zapisuje tekst w określonym <xref:System.IO.TextWriter> obiektu. Jeśli nie <xref:System.IO.TextWriter> jest określony, <xref:System.Activities.Statements.WriteLine> zapisuje tekst do konsoli.  
  
### <a name="using-the-writeline-activity-designer"></a>Przy użyciu narzędzia Projektant działań WriteLine  
 **WriteLine** Projektant działań można znaleźć w **podstawowych** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karty [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)  
  
 **WriteLine** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań zwykle są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.WriteLine> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> z WriteLine. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **WriteLine** Projektant działań lub **DisplayName** pola siatki właściwości.  
  
### <a name="the-writeline-properties"></a>Właściwości WriteLine  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.WriteLine> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości i niektóre z nich można edytowane na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]powierzchnię projektanta.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.WriteLine> działania. Wartość domyślna to WriteLine. Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jest użycie jednego.|  
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Tekst do zapisu. Aby ustawić właściwości, wpisz wyrażenie języka Visual Basic w **tekst** polu na **WriteLine** działania projektanta lub w siatce właściwości.|  
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.IO.TextWriter> Do której <xref:System.Activities.Statements.WriteLine> zapisuje <xref:System.Activities.Statements.WriteLine.Text%2A>. Wartość domyślna to konsoli.|  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy podstawowe](../workflow-designer/primitives-activity-designers.md)   
 [Przypisz](../workflow-designer/assign-activity-designer.md)   
 [Opóźnienie](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)