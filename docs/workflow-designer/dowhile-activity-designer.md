---
title: Projektant działań DoWhile | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d8edec0edcc8461c18d7a90df6a776c96436ae3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="dowhile-activity-designer"></a>Projektant działań DoWhile
<xref:System.Activities.Statements.DoWhile> Działania wykonuje działania zawarte w jego <xref:System.Activities.Statements.DoWhile.Body%2A> co najmniej raz, aż określony warunek ma **false**. Jeśli potrzebujesz działania zawarte w treści pętli do wykonania zero lub więcej razy, użyj <xref:System.Activities.Statements.While> działania zamiast tego.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Właściwości DoWhile w Projektancie przepływów pracy
 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.DoWhile> właściwości działania i informacje dotyczące używania ich w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Działanie do wykonania, gdy wynikiem warunku jest **true**. Aby dodać <xref:System.Activities.Statements.DoWhile.Body%2A> działania, Porzuć działanie z przybornika do **treści** polu na **DoWhile** Projektant działań z tekstu podpowiedzi "Upuść tutaj działanie".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Warunek do oceny po każdej iteracji pętli. Aby ustawić <xref:System.Activities.Statements.DoWhile.Condition%2A>, wpisz [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] wyrażenie w **warunku** polu na **DoWhile** działania projektanta lub w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [Podczas](../workflow-designer/while-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)