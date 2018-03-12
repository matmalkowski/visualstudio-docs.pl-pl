---
title: "Opóźnienie Projektant działań | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cddf4be42d05ebfc3c2df3e64f011b93673eead6
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2018
---
# <a name="delay-activity-designer"></a>Projektant działań opóźnienia
**Opóźnienie** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Delay> działania.

## <a name="the-delay-activity"></a>Działanie opóźnienia
 <xref:System.Activities.Statements.Delay> Działania opóźnienie wykonywania przepływu pracy dla określonego przedziału czasu.

### <a name="using-the-delay-activity-designer"></a>Przy użyciu narzędzia Projektant działań opóźnienia
 **Opóźnienie** Projektant działań można znaleźć w **podstawowych** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karty [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)

 **Opóźnienie** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań zwykle są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Delay> działania z domyślną <xref:System.Activities.Activity.DisplayName%2A> opóźnienia. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **opóźnienie** Projektant działań lub **DisplayName** pola siatki właściwości.

### <a name="the-delay-properties"></a>Właściwości opóźnienia
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Delay> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości i ich niektóre można edytowane w [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]powierzchnię projektanta.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.Delay> działania. Wartość domyślna to opóźnienie. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagane, jest najlepszym rozwiązaniem jej użyć.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Ilość czasu opóźnienia przepływ pracy. Ta właściwość jest ustawiana w siatce właściwości. Wpisz w jednym literału <xref:System.TimeSpan> w formacie 00:00:00 lub wyrażenie języka Visual Basic, aby określić ilość czasu.|

## <a name="see-also"></a>Zobacz także

- [Typy pierwotne](../workflow-designer/primitives-activity-designers.md)
- [Przypisz](../workflow-designer/assign-activity-designer.md)
- [Delay, projektant działań](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)