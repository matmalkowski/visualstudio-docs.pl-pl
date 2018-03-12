---
title: "Porady: używanie edytora wyrażeń | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: be43ad439c8868064fc7e0bab79e051abb991e0d
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-use-the-expression-editor"></a>Porady: używanie edytora wyrażeń
Edytor wyrażeń jest formant projektanta przepływów pracy systemu Windows, który jest używany w wielu działań przepływu pracy jako sposób wprowadzania i oceny tych wyrażeń. Edytor wyrażeń zapewnia pełni funkcjonalnymi IDE, edytowania IntelliSense, w tym kolorowania, ParamInfo, zygzaki sygnalizujące błędy, między innymi funkcjami. Po jego wprowadzeniu, kompilator sprawdza wyrażenie. Jeśli wyrażenie jest nieprawidłowe, zostanie wyświetlony ikony błędu. Można również otworzyć edytora jako **edytora wyrażeń** okno dialogowe.

 Wyrażenia są wartości literałów lub [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kod powiązany z argumentów lub właściwości. Zawierają one elementy wartość (np. zmienne, stałe, literały, właściwości), które są łączone z operacjami umożliwiające uzyskanie nową wartość. Wyrażenia są napisane przy użyciu składni VB.NET, nawet jeśli aplikacja programu przy użyciu języka C#. To oznacza, że wielkość liter nie ma znaczenia, porównanie odbywa się przy użyciu równa się pojedynczy znak ("="), zamiast ("=="), operatorów logicznych są wyrazy "i" i "lub" zamiast symboli "& &" i "&#124;&#124;", i **nic**  jest używany zamiast **null**. Aby uzyskać więcej informacji na temat wyrażenia i operatory w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] oraz niektóre przykłady, zobacz [operatory i wyrażenia w Visual Basic](http://go.microsoft.com/fwlink/?LinkId=186818).

 **Edytora wyrażeń** działa w następujący sposób:

-   Jeśli fokus nie jest na edytora wyrażeń, prawdopodobnie regularnej kontroli blok tekstu.

-   Gdy fokus jest ustawiony na edytora wyrażeń, wyszukuje i zachowuje się jak kontrolka edytora wyrażeń. Po jego traci fokus, it ponownie wygląda jak regularne blok tekstu.

-   Jeśli można skupić się na edytorze wyrażenie w Projektancie rehosted przepływu pracy, następnie ją zachowuje się jak pole tekstowe. Gdy fokus jest stracił w Projektancie rehosted przepływów pracy, Edytor wyrażeń ponownie wygląda jak regularne blok tekstu.

> [!NOTE]
> IntelliSense dla edytora wyrażeń jest dostępna tylko wewnątrz elementu [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. W obu [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] i scenariusze rehosted kompilator sprawdza wyrażenie po jest wprowadzana i edytora wyrażeń Wyświetla ikonę błędu, jeśli wyrażenie jest nieprawidłowe.

### <a name="using-the-expression-editor"></a>Za pomocą edytora wyrażeń

1.  W [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], otwórz projekt nowego lub istniejącego przepływu pracy.

2.  Dodaj na przykład <xref:System.Activities.Statements.Assign> działania do przepływu pracy.

    > [!NOTE]
    > Wiele działań przepływu pracy mają edytory wyrażenia. Obiekty TextBlock wyrażenie również zostać wyświetlony w Projektancie zmiennej, projektanta argumentów i projektanta argumentów dynamicznych. <xref:System.Activities.Statements.Assign> To działanie służy jako przykład.

3.  Kliknij przycisk Edytor po lewej stronie wyrażenia w Projektancie działania dla <xref:System.Activities.Statements.Assign> działania.

     Ciągi szare znaku wodnego  **\<do >** i  **\<wprowadź wyrażenia języka VB. >** są domyślnymi ciągów tekstowych dla wyrażenia edytory w <xref:System.Activities.Statements.Assign> działania.

4.  Wprowadź wyrażenie. Jeśli zostanie wprowadzony ciąg, upewnij się, że ciąg w cudzysłowy. Jeśli chcesz powiązać argumentu wyrażenia do zmiennej, należy pozostawić cudzysłowów wyłączone.

     Gdy wszystko będzie gotowe, wybierz region lub obszar poza wyrażenia w edytorze Przenieś fokus do innej części projektanta. To spowoduje, że kompilator można sprawdzić poprawności wyrażenia opisanych powyżej.

     Alternatywny sposób Podaj/Edytuj wyrażenie jest kliknij przycisk wielokropka obok nazwy właściwości w siatce właściwości. Spowoduje to otwarcie **edytora wyrażeń** jako okna dialogowego.

## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.Presentation.View.ExpressionTextBox>