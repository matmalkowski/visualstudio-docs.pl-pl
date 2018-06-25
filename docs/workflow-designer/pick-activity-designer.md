---
title: Projektant przepływu pracy — Projektant działań pobrania
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb12deec8bba5ac7974b0aa730726f309f1c9c46
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757754"
---
# <a name="pick-activity-designer"></a>Pick, projektant działań

<xref:System.Activities.Statements.Pick> Działania zawiera przepływu sterowania opartego na zdarzeniach. Działania wykonuje jeden z kilku gałęzie w odpowiedzi na wyzwalająca zdarzenia.

## <a name="the-pick-activity"></a>Wybierz działanie

A <xref:System.Activities.Statements.Pick> działania zawiera kolekcję <xref:System.Activities.Statements.PickBranch> obiektów, z których jedna <xref:System.Activities.Statements.Pick> działania może zostać uruchomiony ze względu na niektóre zdarzenia przychodzącego, która służy jako wyzwalacz. W ten sposób projektanta przepływów pracy udostępnia modelowanie przepływu sterowania opartego na zdarzeniach. Każdy <xref:System.Activities.Statements.PickBranch> zawiera <xref:System.Activities.Statements.PickBranch.Trigger%2A> i <xref:System.Activities.Statements.PickBranch.Action%2A>. Na początku <xref:System.Activities.Statements.Pick> wykonania działania, wszystkie działania wyzwalacza z <xref:System.Activities.Statements.PickBranch> zaplanowane elementy. Po ukończeniu pierwsze działanie zaplanowano odpowiadające mu działanie akcji, a inne działania wyzwalacza zostały anulowane.

### <a name="how-to-use-the-pick-activity-designer"></a>Jak używać Projektant działań pobrania

Dostęp **wybierz** Projektant działań w **przepływ sterowania** kategorii **przybornika**. **Wybierz** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy wszędzie tam, gdzie projektantów działań są zazwyczaj umieszczone, na przykład wewnątrz  **Sekwencja** Projektant działań. Po usunięcie go w Projektancie przepływów pracy, tworzy <xref:System.Activities.Statements.Pick> działania, która domyślnie zawiera dwa puste <xref:System.Activities.Statements.PickBranch> działań jako elementy z wyświetlane nazwy Branch1 i Branch2. Te odpowiednich <xref:System.Activities.Statements.PickBranch.DisplayName%2A> wartości właściwości mogą być edytowane w **PickBranch** nagłówka projektanta aktywności lub poziomu **właściwości** okna dla każdej gałęzi.

Istnieją dwa sposoby dodawania <xref:System.Activities.Statements.PickBranch> działań do kolekcji <xref:System.Activities.Statements.Pick> obiektu: przeciąganie i upuszczanie **PickBranch** projektanta z **przybornika** lub korzystając z menu kontekstowego w ramach **wybierz** powierzchnię projektu. Aby uzyskać więcej informacji, zobacz [PickBranch](../workflow-designer/pickbranch-activity-designer.md) tematu. Powiadomienie, że tylko element, którego może być umieszczony wewnątrz **wybierz** Projektant działań jest **PickBranch** Projektant działań.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Wybierz właściwości działania w Projektancie przepływów pracy

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Pick> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchnię projektanta.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.Pick> Projektant działań w nagłówku. Wartość domyślna to pobranie. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku Projektant działań.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jej użyć.|

## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
- [Wybieranie działania](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Używanie działania Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)