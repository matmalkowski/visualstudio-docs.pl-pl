---
title: Tworzenie reguł analizy kodu niestandardowego, w programie Visual Studio
ms.date: 04/04/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f9297d862b0fa47ecc4f5b7b08f6b754e1b5dfc3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="custom-rule-sets"></a>Niestandardowych zestawów reguł

Możesz utworzyć niestandardowy *zestaw reguł* do potrzeb określonego projektu dla analizy kodu.

## <a name="create-a-custom-rule-set"></a>Tworzenie niestandardowego zestawu reguł

Aby utworzyć regułę niestandardową zestaw, możesz otworzyć wbudowanego zestawu reguł w **edytorze zestawu reguł**. Z tego miejsca, można dodać lub usunąć określone zasady i można zmienić akcję, która występuje, gdy naruszenia reguły&mdash;na przykład wyświetlić ostrzeżenia lub błędu.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **właściwości**.

2. Na **właściwości** stron, wybierz opcję **analizy kodu** kartę.

3. W **Uruchom ten zestaw reguł** listy rozwijanej, wykonaj jedną z następujących czynności:

    - Wybierz zestaw reguł, który chcesz dostosować.

     \- lub -

    - Wybierz  **\<Przeglądaj >** określ zestaw istniejącej reguły, których nie ma na liście.

4. Wybierz **Otwórz** reguły są wyświetlane w edytorze zestawu reguł.

Można również utworzyć nowego pliku zestawu reguł z **nowy plik** okna dialogowego:

1. Wybierz **pliku** > **nowy** > **pliku**, lub naciśnij klawisz **Ctrl**+**N**.

2. W **nowy plik** okno dialogowe, wybierz opcję **ogólne** kategorii po lewej stronie, a następnie wybierz **zestawu reguł analizy kodu**.

3. Wybierz **Otwórz**.

   Nowy *.ruleset* plik zostanie otwarty w edytorze zestawu reguł.

### <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Tworzenie niestandardowego zestawu reguł jest z wielu zestawów reguł

1. W Eksploratorze rozwiązań kliknij projekt prawym przyciskiem myszy, a następnie wybierz **właściwości**.

2. Na **właściwości** stron, wybierz opcję **analizy kodu** kartę.

3. Wybierz  **\<Wybierz zestawy wielu reguł... >** z **Uruchom ten zestaw reguł**.

4. W **Dodawanie lub usuwanie zestawów reguł** okno dialogowe, wybierz zestawów reguł, możesz chcesz dołączyć do nowego zestawu reguł.

   ![Dodawanie lub usuwanie zestawów reguł, okno dialogowe](media/add-remove-rule-sets.png)

5. Wybierz **Zapisz jako**, wprowadź nazwę *.ruleset* pliku, a następnie wybierz **zapisać**.

   Nowy zestaw reguł jest zaznaczona w **Uruchom ten zestaw reguł** listy.

6. Wybierz **Otwórz** aby otworzyć nową regułę, ustaw w edytorze zestawu reguł.

## <a name="name-and-description"></a>Nazwa i opis

Aby zmienić nazwę wyświetlaną w zestawie reguł, który jest otwarty w edytorze, otwórz **właściwości** okna, wybierając **widoku** > **okna właściwości** na pasku menu. Wprowadź nazwę wyświetlaną w **nazwa** pole. Można również wprowadzić opis zestawu reguł.

## <a name="next-steps"></a>Następne kroki

Teraz, gdy masz zestawu reguł, następnym krokiem jest dostosowanie zasad przez dodanie lub usunięcie zasady lub modyfikowanie ważności naruszenia reguły.

> [!div class="nextstepaction"]
> [Modyfikuj reguły w edytorze zestawu reguł](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Konfigurowanie analizy kodu dla projektu kodu zarządzanego](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Informacje o zestawie reguł analizy kodu](../code-quality/rule-set-reference.md)