---
title: Zrefaktoryzuj zmienić w programie Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 696ec34bb0009b9b09b5902a102c71cf1331f320
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945457"
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

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
