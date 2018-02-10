---
title: "Refaktoryzuj pola do właściwości w programie Visual Studio | Dokumentacja firmy Microsoft"
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
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 78d2c33002e59eab1b6e8605092a74d9995453a8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="encapsulate-a-field-refactoring"></a>Hermetyzuj pole refaktoryzacji elementu

Dotyczy to refaktoryzacji:

- C#

- Visual Basic

**Co:** umożliwia przekształcić pola właściwości, a następnie zaktualizować wszystkie użycia tego pola, aby użyć nowo utworzonego właściwości.

**Kiedy:** chcesz przenieść pole do właściwości, a następnie zaktualizuj wszystkie odwołania do tego pola.

**Dlaczego:** chcesz przyznać dostęp do innych klas do pola, ale nie ma tych klas bezpośredni dostęp.  Zawijania pola we właściwości, można napisać kod, aby sprawdzić wartości jest przypisany, na przykład.

## <a name="how-to"></a>Porada

1. Zaznacz lub umieść kursor tekst wewnątrz Nazwa pola w celu hermetyzacji:

   - C#:

    ![Wyróżniony kod - C#](media/encapsulate-highlight-cs.png)

   - Visual Basic:

    ![Wyróżniony kod - języka Visual Basic](media/encapsulate-highlight-vb.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + E**.  (Należy pamiętać, że skrót klawiaturowy mogą być różne oparte na profil, który wybrano).
     - Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz opcję **hermetyzowania pola** wpisu z menu podręcznego okna podglądu.
   - **Myszy**
     - Wybierz **Edytuj > Refaktoryzuj > hermetyzowania pola**.
     - Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz opcję **hermetyzowania pola** wpisu z menu podręcznego okna podglądu.

   Wybór | Opis
   --------- | -----------
   **Hermetyzuj pola (i używaj właściwości)** | Hermetyzuje pola z właściwością i aktualizuje wszystkie użycia pola Użyj wygenerowanej właściwości
   **Hermetyzuj pola (ale nadal używaj pola)** | Hermetyzuje pola z właściwością, ale pozostawia niezmienionej użycia wszystkie pola

   Właściwość jest tworzony i odwołania do pola są aktualizowane, jeśli wybrana.

   > [!TIP]
   > Użyj **podgląd zmian** łącza w oknie podręcznym [aby zobaczyć, co zostanie](../../ide/preview-changes.md) przed zatwierdzeniem do niego.

   - C#:

    ![Hermetyzuj właściwość result - C#](media/encapsulate-result-cs.png)

   - Visual Basic:

    ![Hermetyzuj właściwość result - Visual Basic](media/encapsulate-result-vb.png)

## <a name="see-also"></a>Zobacz także

[Refaktoryzacja](../refactoring-in-visual-studio.md)  
[Podgląd zmian](../../ide/preview-changes.md)