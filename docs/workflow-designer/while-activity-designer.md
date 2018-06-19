---
title: Projektant przepływu pracy — podczas Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02f0e83f674378ca7f9297aedbeb580b4f2cad89
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973405"
---
# <a name="while-activity-designer"></a>Podczas gdy Projektant działań

<xref:System.Activities.Statements.While> Działania wykonuje działania zawarte w jego <xref:System.Activities.Statements.While.Body%2A> podczas określonego <xref:System.Activities.Statements.While.Condition%2A> daje w wyniku **true**. Nigdy nie może wykonać zawarte działanie. Jeśli chcesz, aby zawarte działanie ma być wykonywana co najmniej raz, użyj <xref:System.Activities.Statements.DoWhile> działania zamiast tego.

## <a name="while-properties-in-workflow-designer"></a>Podczas właściwości w Projektancie przepływów pracy

W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.While> właściwości działania i w tym artykule opisano, jak są używane w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.While> Projektant działań w nagłówku. Wartość domyślna to podczas. Wartość można edytować w **właściwości** okna lub bezpośrednio w nagłówku projektanta działania.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jej użyć.|
|<xref:System.Activities.Statements.While.Body%2A>|False|Zawiera działanie do wykonania podczas <xref:System.Activities.Statements.While.Condition%2A> daje w wyniku **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|True|Zawiera wyrażenie języka Visual Basic, który jest oszacowywane, aby określić czy działania w <xref:System.Activities.Statements.While.Body%2A> jest wykonywana.|

## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)