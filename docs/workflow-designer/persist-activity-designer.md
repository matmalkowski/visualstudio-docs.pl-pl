---
title: Projektant działań utrwalić | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f990bff4f38fc50e99ec67ec344f51df252c4c6d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="persist-activity-designer"></a>Utrwalanie Projektant działań
**Utrwalanie** Projektant działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Persist> działania.

## <a name="the-persist-activity"></a>Utrwalanie działania
 <xref:System.Activities.Statements.Persist> Działania zapisuje przepływ pracy na dysku, jeśli to możliwe. <xref:System.Activities.Statements.Persist> Działania nie można wykonać w strefie nie trwałości, jak na przykład w <xref:System.Activities.Statements.TransactionScope> działania. Jeśli używasz <xref:System.Activities.Statements.Persist> działania w zakresie z systemem innym niż trwałości, jest zgłaszany wyjątek w czasie wykonywania.

### <a name="using-the-persist-activity-designer"></a>Przy użyciu utrwalić Projektant działań
 **Utrwalanie** Projektant działań można znaleźć w **środowiska uruchomieniowego** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika** Karta (można także wybrać **przybornika** z **widoku** menu lub CTRL + ALT + X.)

 **Utrwalanie** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni we wszystkich działań zwykle są umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie <xref:System.Activities.Statements.Persist> działania z domyślną **DisplayName** z Nietrwałości. <xref:System.Activities.Activity.DisplayName%2A> Można edytowane w nagłówku **utrwalanie** Projektant działań lub **DisplayName** pola siatki właściwości.

### <a name="the-persist-properties"></a>Utrwalanie właściwości
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Persist> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości i niektóre z nich można edytowane na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.Persist> działania. Wartość domyślna to Nietrwałości. Wyświetlana nazwa nie jest ściśle wymagane, jest najlepszym rozwiązaniem, aby użyć nazwy wyświetlanej.|

## <a name="see-also"></a>Zobacz także

- [Środowisko uruchomieniowe](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)