---
title: Wyodrębnij metodę w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/26/2018
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 9e2766159413255543a6022fe0bd52ed6084db96
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="extract-a-method-refactoring"></a>Wyodrębnij refaktoryzacji — metoda

Dotyczy to refaktoryzacji:

- C#

- Visual Basic

**Co:** pozwala włączyć do własnej metody fragment kodu.

**Kiedy:** masz fragment kodu istniejących w niektórych metodę, która musi zostać wywołana z innej metody.

**Dlaczego:** użytkownik może kopiowanie/wklejanie kodu, ale który może doprowadzić do duplikacji. Lepszym rozwiązaniem jest Refaktoryzuj ten fragment do własnej metody, które można wywołać za darmo inną metodą.

## <a name="how-to"></a>Porada

1. Wyróżnij kodu, który zostanie wyodrębniony:

   - C#:

    ![Zaznaczony kod - C#](media/extractmethod-highlight-cs.png)

   - Visual Basic:

    ![Wyróżniony kod - języka Visual Basic](media/extractmethod-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + M**. (Należy pamiętać, że skrót klawiaturowy mogą być różne oparte na profil, który wybrano).
     - Naciśnij klawisz **Ctrl**+**.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **Wyodrębnij metodę** z menu podręcznego okna podglądu.
   - **Myszy**
     - Wybierz **Edytuj > Refaktoryzuj > wyodrębniania metody**.
     - Kliknij prawym przyciskiem myszy kod i wybierz **Refaktoryzuj > wyodrębnić > Wyodrębnij metodę**.
     - Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **Wyodrębnij metodę** z menu podręcznego okna podglądu.

   Metoda zostanie utworzony natychmiast. W tym miejscu można teraz zmienić nazwę metody po prostu, wpisując nazwę nowego.

   > [!TIP]
   > Można także zaktualizować komentarze i innymi ciągami, aby użyć tej nowej nazwy oraz [podgląd zmian](../../ide/preview-changes.md) przed zapisaniem, za pomocą pola wyboru w **zmienić** pole, który jest wyświetlany u góry rogu środowiskiem IDE.

   - C#:

    ![Zmień nazwę metody - C#](media/extractmethod-rename-cs.png)

   - Visual Basic:

    ![Zmień nazwę metody - Visual Basic](media/extractmethod-rename-vb.png)

1. Po zakończeniu modyfikowania zmiany, wybierz **Zastosuj** przycisk lub naciśnij przycisk **Enter** , a zmiany zostaną zatwierdzone.

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)