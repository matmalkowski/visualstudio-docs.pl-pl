---
title: 'Projektant przepływu pracy — porady: Tworzenie zestawu reguł działania PolicyActivity (starsze)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57142fc21bc9db03a338f20a27e20b8af51b48cd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Porady: Tworzenie zestawu reguł działania PolicyActivity (starsze)

W tym temacie opisano sposób tworzenia działania reguły ustawić za pomocą projektanta przepływów pracy programu starszej wersji systemu Windows, którego element docelowy .NET Framework w wersji 3.5 lub WinFX.

 Po przeciągnięciu **zasad** elementu działania z **przybornika** na powierzchnię projektu przepływu pracy można wybrać istniejącą regułę lub utworzyć nową regułę, ustaw dla [działania PolicyActivity ](http://go.microsoft.com/fwlink?LinkID=65019) działania. Wybierz istniejącą regułę skonfigurowane za pomocą [reguły ustawić okno dialogowe Wybieranie (starsze)](../workflow-designer/select-rule-set-dialog-box-legacy.md) i utworzyć zestawy reguł za pomocą [reguły ustawić okno dialogowe Edytor (starsze)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).

> [!NOTE]
> Możesz otworzyć [reguły ustawić okno dialogowe Edytor (starsze)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) okno dialogowe bezpośrednio przez dwukrotne kliknięcie [działania PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) działanie, które znajduje się na powierzchnię projektu przepływu pracy.

## <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>Aby wybrać lub utworzyć zestaw reguł dla działania działania PolicyActivity

1.  Kliknij prawym przyciskiem myszy [działania PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019), a następnie kliknij przycisk **właściwości** otworzyć **właściwości** okna.

2.  Kliknij przycisk **RuleSetReference** właściwości.

3.  Wykonaj jedną z następujących czynności:

    -   Kliknij przycisk **RuleSetReference** wielokropka **[...]** , a następnie wybierz istniejącą regułę w [reguły ustawić okno dialogowe Wybieranie (starsze)](../workflow-designer/select-rule-set-dialog-box-legacy.md). Następnie przejdź do kroku 10.

         —lub—

    -   Wpisz nazwę dla zestawu reguł. Kliknij przycisk **RuleSetReference** wielokropka **[...]** , a następnie wybierz **Edytuj** w [reguły ustawić okno dialogowe Wybieranie (starsze)](../workflow-designer/select-rule-set-dialog-box-legacy.md).

         —lub—

    -   Wpisz nazwę dla zestawu reguł. Rozwiń węzeł **RuleSetReference** właściwości i wybierz wielokropek **[...]**  w **definicji RuleSet** właściwości.

         [Reguły ustawić okno dialogowe Edytor (starsze)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) otwiera.

4.  W [reguły ustawić okno dialogowe Edytor (starsze)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), kliknij przycisk **Dodaj regułę** Aby dodać nową regułę do zestawu reguł.

5.  Wprowadź **nazwa**, **priorytet**, i **ponownej oceny** właściwości, czy też pozostawić wartości domyślne.

6.  Wprowadź tekst **warunku**.

7.  Wprowadź tekst **następnie akcje** i **Else akcje**.

8.  Kliknij przycisk **Dodaj regułę** ponownie, aby dodać inną regułę.

9. Po zakończeniu kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także

- [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)
- [Wybieranie zestawu reguł, okno dialogowe (starsza wersja)](../workflow-designer/select-rule-set-dialog-box-legacy.md)
- [Edytor zestawu reguł, okno dialogowe (starsza wersja)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)
- [Za pomocą zasad działania](http://go.microsoft.com/fwlink?LinkID=65004)
- [Działania przepływu pracy w starszej wersji](../workflow-designer/legacy-workflow-activities.md)