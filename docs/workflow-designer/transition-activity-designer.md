---
title: Przejście Projektant działań | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Transition.UI
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 25b00c38110e8a97d5e5465f3e170bef9c28bb88
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="transition-activity-designer"></a>Projektant działań przejścia
A <xref:System.Activities.Statements.Transition> reprezentuje przejścia między dwoma stanami.

## <a name="using-the-transition-activity-designer"></a>Przy użyciu narzędzia Projektant działań przejścia
 Projektant działań przejścia pozwala na skonfigurowanie przejścia między dwoma stanami.

### <a name="transition-properties-in-the-workflow-designer"></a>Właściwości przejścia w Projektancie przepływów pracy
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Transition> właściwości, które można ustawić za pomocą projektanta przepływów pracy i w tym artykule opisano, jak są używane w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.Transition> Projektant działań. Wartość domyślna to **T1**. Wartość można edytować w siatce właściwości w nagłówku projektanta rozwinięte przejścia i w nagłówku sekcji akcji w Projektancie rozwinięte przejścia. <xref:System.Activities.Activity.DisplayName%2A> Jest używany w nadrzędnych, który jest wyświetlany w górnej części projektanta przepływów pracy.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ścisłym wymogiem jest najlepszym rozwiązaniem jej użyć.|
|<xref:System.Activities.Statements.Transition.Condition%2A>|False|Jeśli jest obecny, określa wyrażenie, które muszą być **True** przed kontrola jest przekazywana do stanu docelowego. Ten stan można edytować w siatce właściwości i w Projektancie rozwinięte przejścia. Wiele warunków w ramach przejścia udostępnionego są oceniane w kolejności, w jakiej występują w Projektancie przejścia. **Uwaga:** należy pamiętać, że jeśli <xref:System.Activities.Statements.Transition.Condition%2A> przejścia daje w wyniku **False** (lub wszystkie warunki przejście z wyzwalaczem udostępnionym obliczać **False**), nie nastąpi przejście i zostanie przełożone wszystkich wyzwalaczy dla wszystkich przejścia ze stanu. W tym samouczku tej sytuacji niemożliwe ze względu na sposób warunki są skonfigurowane (mamy określonych akcji dla tego, czy wynik jest prawidłowy lub nieprawidłowy).|
|**Źródło**|True|Wskazuje stan, z którego pochodzi ten proces przejścia. Klikając nazwę stanu źródła zmienia widok projektanta do widoku rozwiniętego elementu członkowskiego. Ta wartość jest ustawiana podczas przejścia jest tworzony i nie można zmienić.|
|<xref:System.Activities.Statements.Transition.Trigger%2A>|False|Określa działania, których ukończenie inicjuje przejścia. Aby ustawić to działanie, przeciągnij działanie z **przybornika** i upuść ją na **wyzwalacza** sekcji przejścia.|
|<xref:System.Activities.Statements.Transition.Action%2A>|False|Określa działania, która jest wykonywana po zakończeniu działania wyzwalacza i <xref:System.Activities.Statements.Transition.Condition%2A>, jeśli jest obecny, daje w wyniku **true**. To działanie jest wykonywany podczas przechodzenia do stanu docelowego po <xref:System.Activities.Statements.State.Exit%2A> dla stanu źródła, jeśli jest obecny, wykonaniu działania. Po rozwinięciu projektanta przejścia tę wartość można ustawić przez przeciągnięcie działania z **przybornika** i upuszczanie go na **akcji** sekcji przejścia. Może istnieć wiele akcji dla jednego przejścia. Poszczególne działania może być rozwinięty i nabytej i może zostać określona, klikając pozycję w górę lub w dół wyświetloną strzałkę akcję w przypadku wielu działań w przejście.|
|**Miejsce docelowe**|True|Wskazuje stan komputera stanu przejścia do po zakończeniu przejścia. Odpowiada to <xref:System.Activities.Statements.Transition.To%2A> właściwość to przejścia w modelu obiektów. Klikając nazwę stanu docelowego zmienia widok projektanta do widoku rozwiniętego elementu członkowskiego. Ta wartość jest ustawiana podczas przejścia jest tworzony i przeciągając strzałkę, która łączy przejście do stanu docelowego w projektancie, można zmienić.|

### <a name="creating-transitions"></a>Tworzenie przejścia
 Przejścia są tworzone przez przeciąganie linii z jednego stanu do innego lub poprzez upuszczenie stanu na trójkąty wyświetlanych, gdy jeden stan zostanie przeciągnięty za pośrednictwem innego stanu. Aby utworzyć przejście przez przeciągnięcie, umieść kursor myszy nad krawędzią stanu źródła, a następnie przeciągnij linię od stanu źródłowego do stanu docelowego. Aby utworzyć przejście przez porzucenie, przeciągnij stan docelowy Aktywuj stanu źródła i upuść ją na jedną z czterech trójkąty, które pojawiają się wokół stanu źródła. Stan docelowy może być albo nowy stan przeciągnięte z **przybornika**, lub istniejący stan przeciągnięte z projektanta przepływów pracy.

> [!NOTE]
> Pojedynczego stanu komputera stanu może zawierać maksymalnie 76 przejścia utworzone za pomocą projektanta przepływów pracy. Limit przejścia dla stanu utworzony poza projektanta przepływów pracy jest ograniczona tylko zasoby systemowe.

 Przejścia z wyzwalaczem udostępnionym są zestawu przejść, których udostępnianie tego samego zdarzenia wyzwalacza. Wyzwalaczem udostępnionym umożliwia warunkowego przejście do stanu docelowego, na podstawie oceny wyrażenia skonfigurowany dla wielu przejścia, w których udostępnianie wspólnych wyzwalacz zdarzenia. Aby dodać dodatkowe akcje do przejścia i utworzyć przejście udostępniony, kliknij koło, wskazującą rozpoczęcia żądanego przejścia i przeciągnij go do pożądanego stanu. Nowe przejście współużytkują tego samego wyzwalacza jak przejście początkowej, ale ma unikatowy stan i działań. Udostępniony przejścia można również tworzyć od w Projektancie przejścia, klikając **Dodaj udostępnione przejście z wyzwalaczem** w dolnej części projektanta przejścia, a następnie wybierając stan docelowy z  **Dostępne stany do połączenia** listy rozwijanej.

## <a name="see-also"></a>Zobacz także

- [Obiekt StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [Stan końcowy](../workflow-designer/finalstate-activity-designer.md)
- [Stan](../workflow-designer/state-activity-designer.md)