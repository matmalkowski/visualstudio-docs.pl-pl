---
title: Projektant przepływu pracy — elementu FlowSwitch<T> Projektant działań
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 45c655987f3cafd77b284d9d11eafefd56a188fc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="flowswitcht-activity-designer"></a>Elementu FlowSwitch\<T > Projektant działań

<xref:System.Activities.Statements.FlowSwitch%601> Działanie jest warunkowego węzła, który zapewnia rozgałęzianie przepływ kontroli w zależności od kryterium, gdy wymagane są więcej niż dwóch gałęziach alternatywnych. Jeśli rozgałęzianie przepływu wymaga dwóch ścieżek, użyj <xref:System.Activities.Statements.FlowDecision> działania zamiast tego.

## <a name="the-flowswitcht-activity"></a>Elementu FlowSwitch\<T > działania

<xref:System.Activities.Statements.FlowSwitch%601> Zawiera działanie <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> która zwraca wartość typu *T* (określonej przez parametr ogólny) podczas szacowania. Działanie zawiera także zestaw <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, który określa unikatowy mapowanie możliwe wyniki tej oceny do zestawu <xref:System.Activities.Statements.FlowNode> obiektów. <xref:System.Activities.Statements.FlowNode> Wykonywane jest tą, którego obiektu typu *T* jest zgodna z wartością z ocenianą <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. A <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> przypadku (opcjonalnie) można podać w przypadku, w którym są uzyskiwane Brak dopasowania.

### <a name="using-the-flowswitcht-activity-designer"></a>Przy użyciu elementu FlowSwitch\<T > Projektant działań

**Elementu FlowSwitch\<T >** Projektant działań można znaleźć w **schemat blokowy** kategorii **przybornika**, które jest dostępne po kliknięciu **Przybornika** karcie po lewej stronie projektanta przepływów pracy (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)

**Elementu FlowSwitch\<T >** Projektant działań mogą być przeciągnięte z **przybornika** i porzucić na powierzchni projektanta przepływów pracy w ramach **schemat blokowy** Projektant działań. Użyj **wybierz typy** okna do określania typu (skojarzone w kodzie z <xref:System.Activities.Statements.FlowSwitch%601> przez jego parametru ogólnego) uzyskane z obliczenia <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Ta procedura powoduje utworzenie <xref:System.Activities.Statements.FlowSwitch%601> działania z etykietą **przełącznika** w <xref:System.Activities.Statements.Flowchart> działania. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> Można wpisać w **wyrażenie** pole **właściwości** okna, klikając, gdy tekst podpowiedzi mówi "Wprowadź wyrażenia języka VB.".

Wskaźnik myszy na **elementu FlowSwitch\<T >** Projektant działań powoduje kwadratowych uchwytów, które są używane do łączenia <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> wokół jego krawędzi. Po przeciąganie **elementu FlowSwitch < T\>**  Projektant działań i innych projektantów działań na **schemat blokowy**, <xref:System.Activities.Activity> obiektów, które reprezentują one gotowe ze sobą powiązane Aby określić kolejność wykonywania. Aby utworzyć jedną z <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> skojarzone z <xref:System.Activities.Statements.FlowSwitch%601>, kliknij jedną z kwadratowa wielkość uchwytów w obwodzie **elementu FlowSwitch < T\>**  i przeciągnij go (przytrzymując przycisk myszy) do jednego z uchwytów który pojawia się w podobny sposób wokół działania docelowego, gdy wskaźnik myszy znajduje się nad jego projektanta. Zwolnij przycisk myszy i Strzałka z **elementu FlowSwitch < T\>**  do projektanta docelowego pojawia się reprezentujący ten przypadek. Wartość domyślna dla tego przypadku wyświetla na strzałkę i można je edytować w **przypadku** pole **właściwości** okna.

### <a name="the-flowswitcht-properties"></a>Elementu FlowSwitch\<T > Właściwości

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.FlowSwitch%601> właściwości oraz opis korzystania z nich w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchnię projektanta.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Określa wyrażenie, które jest obliczane, aby określić, które <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> Aby przełączyć się do ścieżki wykonywania.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Określa unikatowy mapowanie możliwe wyniki z obliczenia <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> z zestawem <xref:System.Activities.Statements.FlowNode> obiektów.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Określa mapowanie podczas obliczania <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> nie pasuje do jednej z wartości zawartych w <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> obiektu.|

## <a name="see-also"></a>Zobacz także

- [Schemat blokowy](../workflow-designer/flowchart-activity-designers.md)
- [Schemat blokowy](../workflow-designer/flowchart-activity-designer.md)
- [Elementu FlowDecision](../workflow-designer/flowdecision-activity-designer.md)