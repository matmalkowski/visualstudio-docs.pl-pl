---
title: Tworzenie reguł analizy kodu niestandardowego, ustaw w programie Visual Studio
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 727c11e24eb3409de89fe211c6a37691dfec298c
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204118"
---
# <a name="customize-a-rule-set"></a>Dostosuj zestaw reguł

Można utworzyć niestandardowego zestawu reguł do potrzeb określonego projektu dla analizy kodu.

## <a name="create-a-custom-rule-set"></a>Tworzenie niestandardowego zestawu reguł

Aby utworzyć niestandardową regułę zestaw, możesz otworzyć wbudowany zestaw reguł w **edytorze zestawu reguł**. Z tego miejsca można dodawać i usuwać określone zasady i możesz zmienić akcję, która występuje, gdy zostanie naruszona zasada&mdash;na przykład wyświetlić ostrzeżenia lub błędu.

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **właściwości**.

2. Na **właściwości** stron, wybierz opcję **analizy kodu** kartę.

3. W **Uruchom ten zestaw reguł** listy rozwijanej, wykonaj jedną z następujących czynności:

    - Wybierz zestaw reguł, który chcesz dostosować.

     \- lub —

    - Wybierz  **\<Przeglądaj … >** do określenia zestawu istniejącą regułę, która nie jest na liście.

4. Wybierz **Otwórz** reguły są wyświetlane w edytorze zestawu reguł.

Można również utworzyć nowego pliku zestawu reguł z **nowy plik** okno dialogowe:

1. Wybierz **pliku** > **New** > **pliku**, lub naciśnij **Ctrl**+**N**.

2. W **nowy plik** okno dialogowe, wybierz opcję **ogólne** kategorii po lewej stronie, a następnie wybierz pozycję **zestawu reguł analizy kodu**.

3. Wybierz **Otwórz**.

   Nowy *.ruleset* plik zostanie otwarty w edytorze zestawu reguł.

### <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Tworzenie niestandardowego zestawu reguł z wielu zestawów reguł

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt, a następnie wybierz **właściwości**.

2. Na **właściwości** stron, wybierz opcję **analizy kodu** kartę.

3. Wybierz  **\<Wybierz wiele reguł ustawia... >** z **Uruchom ten zestaw reguł**.

4. W **apletu Dodaj lub Usuń zestawy reguł** okno dialogowe, wybierz zestawy reguł można chcesz uwzględnić w Twojego nowego zestawu reguł.

   ![Dodawanie lub usuwanie zestawów reguł, okno dialogowe](media/add-remove-rule-sets.png)

5. Wybierz **Zapisz jako**, wprowadź nazwę dla *.ruleset* pliku, a następnie wybierz **Zapisz**.

   Nowy zestaw reguł wybrano **Uruchom ten zestaw reguł** listy.

6. Wybierz **Otwórz** można otworzyć nowej reguły, które są ustawiane za pomocą edytora zestawu reguł.

## <a name="name-and-description"></a>Nazwa i opis

Aby zmienić nazwę wyświetlaną zestawu reguł, który jest otwarty w edytorze, otwórz **właściwości** okna, wybierając **widoku** > **okno właściwości** na pasku menu. Wprowadź nazwę wyświetlaną w **nazwa** pole. Można również wprowadzić opis zestawu reguł.

## <a name="next-steps"></a>Następne kroki

Teraz, gdy masz zestaw reguł, następnym krokiem jest dostosowywanie reguł przez dodanie lub usunięcie reguł lub modyfikowanie ważność naruszeń reguł.

> [!div class="nextstepaction"]
> [Modyfikowanie zasad w edytorze zestawu reguł](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Konfigurowanie analizy kodu dla projektu kodu zarządzanego](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Informacje o zestawie reguł analizy kodu](../code-quality/rule-set-reference.md)