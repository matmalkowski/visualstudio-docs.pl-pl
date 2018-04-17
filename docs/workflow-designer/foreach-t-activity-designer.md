---
title: Instrukcja ForEach&lt;T&gt; Projektant działań | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a9f62f8b3fcb96d0d0abc8ba52b2d0ccfb42473
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="foreachlttgt-activity-designer"></a>Instrukcja ForEach&lt;T&gt; Projektant działań
<xref:System.Activities.Statements.ForEach%601> Działania wykonuje działania zawarte w jego <xref:System.Activities.Statements.ForEach%601.Body%2A> dla każdego elementu w określonej <xref:System.Activities.Statements.ForEach%601.Values%2A> kolekcji.

## <a name="foreacht-properties-in-the-workflow-designer"></a>Instrukcja ForEach < T\> właściwości w Projektancie przepływów pracy
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.ForEach%601> właściwości działania i informacje dotyczące używania ich w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.ForEach%601> działania. Wartość domyślna to ForEach < Int32\>. Mimo że <xref:System.Activities.Activity.DisplayName%2A> wartość nie jest ściśle wymagane, jest najlepszym rozwiązaniem jej użyć.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Kolekcja elementów w celu wykonania iteracji. Aby ustawić <xref:System.Activities.Statements.ForEach%601.Values%2A>, wpisz [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] wyrażenie w **wartości** polu na **ForEach < T\>**  działania projektanta lub w siatce właściwości.|
|*TypeArgument*|True|Typ elementów w <xref:System.Activities.Statements.ForEach%601.Values%2A> kolekcji określonej przez parametr ogólny *T*. Domyślnie *elementu TypeArgument* ustawiono **Int32**. Aby zmienić typ, zmień wartość *elementu TypeArgument* pola kombi w siatce właściwości.|

 Domyślnie, nosi nazwę sterująca pętli **elementu**. Można zmienić nazwę zmiennej iteracyjnej w <xref:System.Activities.Statements.ForEach%601> Projektant działań. Sterująca pętli można używać w wyrażeniach w elementów podrzędnych <xref:System.Activities.Statements.ForEach%601> działania.

## <a name="see-also"></a>Zobacz także

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)