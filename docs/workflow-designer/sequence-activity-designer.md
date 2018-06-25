---
title: Projektant przepływu pracy — Projektant działań sekwencji
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 58aea13f99f225c01806186903b62a58362715b3
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755710"
---
# <a name="sequence-activity-designer"></a>Sequence, projektant działań

<xref:System.Activities.Statements.Sequence> Działanie zawiera uporządkowaną kolekcję działania podrzędne, które wykonuje się w kolejności.

Innym sposobem wykonania zestawu działań w kolejności jest użycie <xref:System.Activities.Statements.Flowchart> działania. Należy rozważyć użycie [schemat blokowy](../workflow-designer/flowchart-activity-designer.md) Jeśli masz rozgałęzianie prostego lub zapętlenia przepływu program, który ma zostać schematycznie modelu.

## <a name="using-the-sequence-activity-designer"></a>Przy użyciu narzędzia Projektant działania sekwencji

Aby dodać <xref:System.Activities.Statements.Sequence> działania, przeciągnij **sekwencji** Projektant działań z **przybornika** i upuść ją na powierzchni projektanta przepływów pracy. Aby dodać do tego działania podrzędnego <xref:System.Activities.Statements.Sequence> działania, przeciągnij niektóre działania, z **przybornika** i upuść ją na trójkąt w polu z tekstu podpowiedzi "Upuść działanie tutaj".

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Właściwości działania sekwencji w Projektancie przepływów pracy

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Sequence> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchnię projektanta.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.Sequence> Projektant działań w nagłówku. Wartość domyślna to sekwencji. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku Projektant działań.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jej użyć.|

## <a name="see-also"></a>Zobacz także

- [Schemat blokowy](../workflow-designer/flowchart-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)