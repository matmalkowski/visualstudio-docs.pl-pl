---
title: "Projektant działań sekwencji | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 64ec037433ca4ff984628994ba2bf353ad8e365c
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2018
---
# <a name="sequence-activity-designer"></a>Projektant działań sekwencji
<xref:System.Activities.Statements.Sequence> Działanie zawiera uporządkowaną kolekcję działania podrzędne, które wykonuje się w kolejności.

 Innym sposobem wykonania zestawu działań w kolejności jest użycie <xref:System.Activities.Statements.Flowchart> działania. Należy rozważyć użycie [schemat blokowy](../workflow-designer/flowchart-activity-designer.md) Jeśli masz rozgałęzianie prostego lub zapętlenia przepływu program, który ma zostać schematycznie modelu.

## <a name="using-the-sequence-activity-designer"></a>Przy użyciu narzędzia Projektant działania sekwencji
 Aby dodać <xref:System.Activities.Statements.Sequence> działania, przeciągnij **sekwencji** Projektant działań z **przybornika** i upuść ją na powierzchni projektanta przepływów pracy systemu Windows. Aby dodać do tego działania podrzędnego <xref:System.Activities.Statements.Sequence> działania, przeciągnij niektóre działania, z **przybornika** i upuść ją na trójkąt w polu z tekstu podpowiedzi "Upuść działanie tutaj".

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Właściwości działania sekwencji w Projektancie przepływów pracy
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Sequence> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchnię projektanta.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.Sequence> Projektant działań w nagłówku. Wartość domyślna to sekwencji. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku Projektant działań.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jej użyć.|

## <a name="see-also"></a>Zobacz także

- [Schemat blokowy](../workflow-designer/flowchart-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)