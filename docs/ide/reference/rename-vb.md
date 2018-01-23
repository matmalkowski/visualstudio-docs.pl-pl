---
title: "Zrefaktoryzuj zmiany nazwy w języku Visual Basic | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.rename
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: 0f9421ed314dc513d5e8af30bad907766342300a
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="rename-a-code-symbol-in-visual-basic"></a>Zmiana nazwy symbolu kodu w języku Visual Basic

**Co:** pozwala zmienić identyfikatory symboli kodu, takich jak pola, zmienne lokalne, metody, obszary nazw, właściwości i typów.

**Kiedy:** chcesz zmienić element bezpiecznie bez konieczności Znajdź wszystkie wystąpienia i kopiowania/wklejania nową nazwę.

**Dlaczego:** kopiowania i wklejania nową nazwę dla całego projektu prawdopodobnie będą powodować błędy.  To narzędzie refaktoryzacji dokładnie będzie wykonywać operacji zmiany nazwy.

**Jak:**

1. Zaznacz lub umieść kursor tekst wewnątrz można zmienić nazwy elementu:

   ![Wyróżniony kod](media/rename-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + R**.  (Należy pamiętać, że skrót klawiaturowy mogą być różne oparte na profil, który wybrano).
   * **Myszy**
     * Wybierz **Edytuj > Refaktoryzuj > Zmień nazwę**.
     * Kliknij prawym przyciskiem myszy kod i wybierz **zmienić**.

1. Zmień nazwę elementu po prostu, wpisując nazwę nowego.

   ![Zmień nazwę animacji](media/rename-rename-vb.png)

   > [!TIP]
   > Można także zaktualizować komentarze i innymi ciągami, aby użyć tej nowej nazwy oraz [podgląd zmian](../../ide/preview-changes.md) przed zapisaniem, za pomocą pola wyboru w **zmienić** pole, który jest wyświetlany u góry rogu środowiskiem IDE.

1. Po zakończeniu modyfikowania zmiany, kliknij przycisk **Zastosuj** przycisk lub naciśnij przycisk **Enter** , a zmiany zostaną zatwierdzone.

> [!NOTE]
> Jeśli używasz nazwę, która już istnieje która może spowodować konflikt, **zmienić** wyświetli ostrzeżenie, pole w środowiskiem IDE.
>
> ![Zmień nazwę konflikt](media/rename-conflict-vb.png)

## <a name="see-also"></a>Zobacz także

[Refaktoryzacja](../refactoring-in-visual-studio.md)  
[Podgląd zmian](../../ide/preview-changes.md)