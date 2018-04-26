---
title: 'Projektant przepływu pracy — porady: debugowanie XAML z projektanta przepływów pracy'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: eac6294861080614cbdd46e6ac1cc9a05d7124ff
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Porady: debugowanie XAML z projektanta przepływów pracy

Przepływy pracy są zdefiniowane w języku XAML. Reprezentacja interfejsu użytkownika przepływu pracy jest oparty na drzewie XAML definiujący przepływ pracy. Działanie debugowania jest podobny do debugowania przepływów pracy w Projektancie przepływów pracy systemu Windows. Na przykład podczas debugowania XAML, zmiennych lokalnych, obejrzyj i wątków windows działał tak samo jak w debugowaniu projektanta przepływów pracy. Ponadto widoku stosu wywołań podczas debugowania XAML jest liniowej hierarchiczny widok przepływ wykonania przepływu pracy.

> [!NOTE]
> XAML przepływu pracy znajduje się w tym samym zestawie co działania, zestawu część nazwy klas nie są uwzględniane. Bez tej części nazwy klas (działanie) XAML nie można załadować w czasie wykonywania. Nie zaleca się definiowania działań w tej samej przestrzeni nazw jako głównego projektu; w przeciwnym razie XAML musi być edytowane ręcznie po edycji w projektancie.

## <a name="to-debug-workflow-xaml"></a>Debugowanie XAML przepływu pracy

1.  Otwórz projekt przepływu pracy lub działania w programie Visual Studio.

2.  Ustaw punkt przerwania działania lub działania, które chcesz debugować zgodnie z opisem w [porady: Ustawianie punktów przerwania w przepływach pracy](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3.  Kliknij prawym przyciskiem myszy plik .xaml, który zawiera definicję przepływu pracy i wybierz **kod widoku**. Widoczny będzie wyświetlany na tym samym wierszu co deklaracja elementu XAML działania w widoku Projekt można ustawić punktu przerwania na punkt przerwania.

4.  Wywoływanie debugger zgodnie z opisem w [porady: wywoływanie Debugger przepływu pracy](../workflow-designer/how-to-invoke-the-workflow-debugger.md).

5.  Podczas wykonywania kodu osiągnie jednego z punktów przerwania, zostanie wyróżniony element XAML skojarzone z tego punktu przerwania. Aby przejść do następnego punktu przerwania, należy użyć **F10** lub **F11** klucza.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Ustawianie punktów przerwania w przepływach pracy](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Instrukcje: Wywoływanie debugera przepływu pracy](../workflow-designer/how-to-invoke-the-workflow-debugger.md)