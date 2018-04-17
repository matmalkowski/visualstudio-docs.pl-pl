---
title: 'Porady: debugowanie XAML z projektanta przepływów pracy | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: c0ac923de3c5381add6f0a33612258e8b9d64824
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Porady: debugowanie XAML z projektanta przepływów pracy
Przepływy pracy są zdefiniowane w języku XAML. Reprezentacja interfejsu użytkownika przepływu pracy jest oparty na drzewie XAML definiujący przepływ pracy. Działanie debugowania jest podobny do debugowania przepływów pracy w Projektancie przepływów pracy systemu Windows. Na przykład podczas debugowania XAML, zmiennych lokalnych, obejrzyj i wątków windows działają tak samo jak w [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] debugowania. Ponadto widoku stosu wywołań podczas debugowania XAML jest liniowej hierarchiczny widok przepływ wykonania przepływu pracy.

> [!NOTE]
> XAML przepływu pracy znajduje się w tym samym zestawie co działania, zestawu część nazwy klas nie są uwzględniane. Bez tej części nazwy klas (działanie) XAML nie można załadować w czasie wykonywania. Nie zaleca się definiowania działań w tej samej przestrzeni nazw jako głównego projektu; w przeciwnym razie XAML musi być edytowane ręcznie po edycji w projektancie.

### <a name="to-debug-workflow-xaml"></a>Debugowanie XAML przepływu pracy

1.  Otwórz projekt przepływu pracy lub działania w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

2.  Ustaw punkt przerwania działania lub działania, które chcesz debugować zgodnie z opisem w [porady: Ustawianie punktów przerwania w przepływach pracy](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3.  Kliknij prawym przyciskiem myszy plik .xaml, który zawiera definicję przepływu pracy i wybierz **kod widoku**. Widoczny będzie wyświetlany na tym samym wierszu co deklaracja elementu XAML działania w widoku Projekt można ustawić punktu przerwania na punkt przerwania.

4.  Wywoływanie debugger zgodnie z opisem w [porady: wywoływanie Debugger przepływu pracy](../workflow-designer/how-to-invoke-the-workflow-debugger.md).

5.  Podczas wykonywania kodu osiągnie jednego z punktów przerwania, zostanie wyróżniony element XAML skojarzone z tego punktu przerwania. Aby przejść do następnego punktu przerwania, należy użyć **F10** lub **F11** klucza.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Ustawianie punktów przerwania w przepływach pracy](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Instrukcje: Wywoływanie debugera przepływu pracy](../workflow-designer/how-to-invoke-the-workflow-debugger.md)