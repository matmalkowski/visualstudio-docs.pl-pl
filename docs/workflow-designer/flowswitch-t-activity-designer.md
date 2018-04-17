---
title: Elementu FlowSwitch&lt;T&gt; Projektant działań | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: fb8c28f835fad4e70b213d13aaeb654780b72297
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="flowswitchlttgt-activity-designer"></a>Elementu FlowSwitch&lt;T&gt; Projektant działań
<xref:System.Activities.Statements.FlowSwitch%601> Działanie jest warunkowego węzła, który zapewnia rozgałęzianie przepływ kontroli w zależności od kryterium, gdy wymagane są więcej niż dwóch gałęziach alternatywnych. Jeśli rozgałęzianie przepływu wymaga dwóch ścieżek, użyj <xref:System.Activities.Statements.FlowDecision> działania zamiast tego.

## <a name="the-flowswitcht-activity"></a>Elementu FlowSwitch < T\> działania
 <xref:System.Activities.Statements.FlowSwitch%601> Zawiera działanie <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> która zwraca wartość typu *T* (określonej przez parametr ogólny) podczas szacowania. Działanie zawiera także zestaw <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, który określa unikatowy mapowanie możliwe wyniki tej oceny do zestawu <xref:System.Activities.Statements.FlowNode> obiektów. <xref:System.Activities.Statements.FlowNode> Wykonywane jest tą, którego obiektu typu *T* jest zgodna z wartością z ocenianą <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. A <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> przypadku (opcjonalnie) można podać w przypadku, w którym są uzyskiwane Brak dopasowania.

### <a name="using-the-flowswitcht-activity-designer"></a>Przy użyciu elementu FlowSwitch\<T > Projektant działań
 **Elementu FlowSwitch\<T >** Projektant działań można znaleźć w **schemat blokowy** kategorii **przybornika**, które jest dostępne po kliknięciu **Przybornika** karcie po lewej stronie [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (można także wybrać **narzędzi** z **widoku** menu lub CTRL + ALT + X.)

 **Elementu FlowSwitch\<T >** Projektant działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] powierzchni w **schemat blokowy** Projektant działań. Użyj **wybierz typy** okna do określania typu (skojarzone w kodzie z <xref:System.Activities.Statements.FlowSwitch%601> przez jego parametru ogólnego) uzyskane z obliczenia <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Ta procedura powoduje utworzenie <xref:System.Activities.Statements.FlowSwitch%601> działania z etykietą **przełącznika** w <xref:System.Activities.Statements.Flowchart> działania. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> Można wpisać w **wyrażenie** pole **właściwości** okna, klikając, gdy tekst podpowiedzi mówi "Wprowadź wyrażenia języka VB.".

 Wskaźnik myszy na **elementu FlowSwitch\<T >** Projektant działań powoduje kwadratowych uchwytów, które są używane do łączenia <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> wokół jego krawędzi. Po przeciąganie **elementu FlowSwitch < T\>**  Projektant działań i innych projektantów działań na **schemat blokowy**, <xref:System.Activities.Activity> obiektów, które reprezentują one gotowe ze sobą powiązane Aby określić kolejność wykonywania. Aby utworzyć jedną z <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> skojarzone z <xref:System.Activities.Statements.FlowSwitch%601>, kliknij jedną z kwadratowa wielkość uchwytów w obwodzie **elementu FlowSwitch < T\>**  i przeciągnij go (przytrzymując przycisk myszy) do jednego z uchwytów który pojawia się w podobny sposób wokół działania docelowego, gdy wskaźnik myszy znajduje się nad jego projektanta. Zwolnij przycisk myszy i Strzałka z **elementu FlowSwitch < T\>**  do projektanta docelowego pojawia się reprezentujący ten przypadek. Wartość domyślna dla tego przypadku wyświetla na strzałkę i można je edytować w **przypadku** pole **właściwości** okna.

### <a name="the-flowswitcht-properties"></a>Elementu FlowSwitch < T\> właściwości
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