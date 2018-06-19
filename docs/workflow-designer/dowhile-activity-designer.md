---
title: Projektant przepływu pracy — Projektant działań DoWhile
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 23588a044596ce5250cc68d01263f5d80775866a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969981"
---
# <a name="dowhile-activity-designer"></a>Projektant działań DoWhile

<xref:System.Activities.Statements.DoWhile> Działania wykonuje działania zawarte w jego <xref:System.Activities.Statements.DoWhile.Body%2A> co najmniej raz, aż określony warunek ma **false**. Jeśli potrzebujesz działania zawarte w treści pętli do wykonania zero lub więcej razy, użyj <xref:System.Activities.Statements.While> działania zamiast tego.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Właściwości DoWhile w Projektancie przepływów pracy

W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.DoWhile> właściwości działania i informacje dotyczące używania ich w Projektancie:

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Działanie do wykonania, gdy wynikiem warunku jest **true**. Aby dodać <xref:System.Activities.Statements.DoWhile.Body%2A> działania, Porzuć działanie z przybornika do **treści** polu na **DoWhile** Projektant działań z tekstu podpowiedzi "Upuść tutaj działanie".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Warunek do oceny po każdej iteracji pętli. Aby ustawić <xref:System.Activities.Statements.DoWhile.Condition%2A>, wpisz wyrażenie języka Visual Basic w **warunku** polu na **DoWhile** działania projektanta lub w siatce właściwości.|

## <a name="see-also"></a>Zobacz także

- [Podczas](../workflow-designer/while-activity-designer.md)
- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)