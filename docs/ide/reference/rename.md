---
title: "Zrefaktoryzuj zmienić w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: bd15d1b59eb5d593fe2b069c2b6721ca623ae99c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="rename-a-code-symbol-refactoring"></a>Symbol kodu Refaktoryzacja zmiany nazwy

Dotyczy to refaktoryzacji:

- C#

- Visual Basic

**Co:** pozwala zmienić identyfikatory symboli kodu, takich jak pola, zmienne lokalne, metody, obszary nazw, właściwości i typów.

**Kiedy:** chcesz zmienić element bezpiecznie bez konieczności Znajdź wszystkie wystąpienia i kopiowania/wklejania nową nazwę.

**Dlaczego:** kopiowania i wklejania nową nazwę dla całego projektu prawdopodobnie będą powodować błędy. To narzędzie refaktoryzacji dokładnie będzie wykonywać operacji zmiany nazwy.

## <a name="how-to"></a>Porada

1. Zaznacz lub umieść kursor tekst wewnątrz można zmienić nazwy elementu:

   - C#:

    ![Wyróżniony kod - C#](media/rename-highlight-cs.png)

   - Visual Basic:

    ![Wyróżniony kod - języka Visual Basic](media/rename-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + R**. (Należy pamiętać, że skrót klawiaturowy mogą być różne oparte na profil, który wybrano).
   - **Myszy**
     - Wybierz **Edytuj > Refaktoryzuj > Zmień nazwę**.
     - Kliknij prawym przyciskiem myszy kod i wybierz **zmienić**.

1. Zmień nazwę elementu po prostu, wpisując nazwę nowego.

   - C#:

    ![Zmień nazwę animacji - C#](media/rename-animated-cs.gif)

   - Visual Basic:

    ![Zmień nazwę - VB](media/rename-rename-vb.png)

   > [!TIP]
   > Można także zaktualizować komentarze i innymi ciągami, aby użyć tej nowej nazwy oraz [podgląd zmian](../../ide/preview-changes.md) przed zapisaniem, za pomocą pola wyboru w **zmienić** pole, który jest wyświetlany u góry prawo do edytora.

1. Po zakończeniu modyfikowania zmiany, wybierz **Zastosuj** przycisk lub naciśnij przycisk **Enter** , a zmiany zostaną zatwierdzone.

> [!NOTE]
> Jeśli używasz nazwę, która już istnieje która może spowodować konflikt, **zmienić** wyświetli ostrzeżenie, pole.
>
> ![Zmień nazwę konflikt](media/rename-conflict-cs.png)

## <a name="see-also"></a>Zobacz także

[Refaktoryzacja](../refactoring-in-visual-studio.md)  
[Podgląd zmian](../../ide/preview-changes.md)
