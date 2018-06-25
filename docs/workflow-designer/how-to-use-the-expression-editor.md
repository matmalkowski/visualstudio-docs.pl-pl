---
title: 'Projektant przepływu pracy — porady: używanie edytora wyrażeń'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c1f2ab9cad6f54b8d1106fd68eb017434cf5cfef
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756147"
---
# <a name="how-to-use-the-expression-editor"></a>Porady: używanie edytora wyrażeń

Edytor wyrażeń jest formant projektanta przepływów pracy, który jest używany w wielu działań przepływu pracy o wprowadzenie i obliczać wyrażeń. Edytor wyrażeń zapewnia pełni funkcjonalnymi IDE, edytowanie kolorowania doświadczenia, takie jak IntelliSense, ParamInfo, zygzaki sygnalizujące błędy, między innymi funkcjami. Po jego wprowadzeniu, kompilator sprawdza wyrażenie. Jeśli wyrażenie jest nieprawidłowe, zostanie wyświetlony ikony błędu. Można również otworzyć edytora jako **edytora wyrażeń** okno dialogowe.

Wyrażenia są wartości literału lub kod Visual Basic powiązany z argumentów lub właściwości. Zawierają one elementy wartość (na przykład zmienne, stałe, literały, właściwości), które są łączone z operacjami umożliwiające uzyskanie nową wartość. Wyrażenia są napisane przy użyciu składni VB.NET, nawet jeśli aplikacja programu przy użyciu języka C#. To oznacza, że wielkość liter nie ma znaczenia, porównanie odbywa się przy użyciu jednego równości znak ("=" zamiast "=="), operatorów logicznych są wyrazy "i" i "lub" zamiast symboli "& &" i "||", i **nic** jest używany zamiast **null**. Aby uzyskać więcej informacji na temat wyrażenia i operatory w języku Visual Basic i niektóre przykłady, zobacz [operatory i wyrażenia w Visual Basic](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100)).

**Edytora wyrażeń** działa w następujący sposób:

- Jeśli fokus nie jest na edytora wyrażeń, prawdopodobnie regularnej kontroli blok tekstu.

- Gdy fokus jest ustawiony na edytora wyrażeń, wyszukuje i zachowuje się jak kontrolka edytora wyrażeń. Po jego traci fokus, Edytor wyrażeń ponownie wygląda jak regularne blok tekstu.

- Jeśli można skupić się na edytorze wyrażenie w Projektancie rehosted przepływu pracy, następnie ją zachowuje się jak pole tekstowe. Gdy fokus jest stracił w Projektancie rehosted przepływów pracy, Edytor wyrażeń ponownie wygląda jak regularne blok tekstu.

> [!NOTE]
> IntelliSense dla edytora wyrażeń jest dostępna tylko w programie Visual Studio. W programie Visual Studio i rehosted scenariusze kompilator sprawdza wyrażenie po jest wprowadzana i edytora wyrażeń Wyświetla ikonę błędu, jeśli wyrażenie jest nieprawidłowe.

## <a name="use-the-expression-editor"></a>Użyj edytora wyrażeń

1.  W programie Visual Studio Otwórz projekt nowego lub istniejącego przepływu pracy.

2.  Dodaj na przykład <xref:System.Activities.Statements.Assign> działania do przepływu pracy.

    > [!NOTE]
    > Wiele działań przepływu pracy mają edytory wyrażenia. Obiekty TextBlock wyrażenie również zostać wyświetlony w Projektancie zmiennej, projektanta argumentów i projektanta argumentów dynamicznych. <xref:System.Activities.Statements.Assign> To działanie służy jako przykład.

3.  Kliknij przycisk Edytor po lewej stronie wyrażenia w Projektancie działania dla <xref:System.Activities.Statements.Assign> działania.

     Ciągi szarego znaku wodnego  **\<do >** i  **\<wprowadź wyrażenia języka VB. >** są domyślnymi ciągów tekstowych dla wyrażenia edytory w <xref:System.Activities.Statements.Assign> działania.

4.  Wprowadź wyrażenie. Jeśli zostanie wprowadzony ciąg, upewnij się, że ciąg w cudzysłowy. Jeśli chcesz powiązać argumentu wyrażenia do zmiennej, należy pozostawić cudzysłowów wyłączone.

     Gdy wszystko będzie gotowe, wybierz region lub obszar poza wyrażenia w edytorze Przenieś fokus do innej części projektanta. Przesunięcie fokus powoduje, że kompilator można sprawdzić poprawności wyrażenia opisanych powyżej.

     Alternatywny sposób, aby wprowadzić lub edytować wyrażenie jest kliknij przycisk wielokropka obok nazwy właściwości w siatce właściwości. Wybierając wielokropek otwiera **edytora wyrażeń** jako okno dialogowe.

## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.Presentation.View.ExpressionTextBox>