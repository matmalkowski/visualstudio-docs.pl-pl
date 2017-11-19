---
title: Hermetyzuj pole - refaktoryzacji (Visual Basic) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: 39a9ed11-363f-4dda-af3b-0affe6db1d42
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.encapsulatefield
dev_langs: VB
ms.openlocfilehash: 9575ad83ead4960016ba7814642cacb1db04ea4d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="encapsulate-a-field-in-visual-basic"></a>Hermetyzuj pole w języku Visual Basic
**Co:** umożliwia przekształcić pola właściwości, a następnie zaktualizować wszystkie użycia tego pola, aby użyć nowo utworzonego właściwości.

**Kiedy:** chcesz przenieść pole do właściwości, a następnie zaktualizuj wszystkie odwołania do tego pola.  

**Dlaczego:** chcesz przyznać dostęp do innych klas do pola, ale nie ma tych klas bezpośredni dostęp.  Zawijania pola we właściwości, można napisać kod, aby sprawdzić wartości jest przypisany, na przykład.

**Jak:**

1. Zaznacz lub umieść kursor tekst wewnątrz Nazwa pola w celu hermetyzacji:

   ![Wyróżniony kod](media/encapsulate_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + E**.  (Należy pamiętać, że skrót klawiaturowy mogą być różne oparte na profil, który wybrano).
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz opcję **hermetyzowania pola** wpisu z menu podręcznego okna podglądu.
   * **Myszy**
     * Wybierz **Edytuj > Refaktoryzuj > hermetyzowania pola**.
     * Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz opcję **hermetyzowania pola** wpisu z menu podręcznego okna podglądu.

   Wybór | Opis
   --------- | -----------
   **Hermetyzuj pola (i używaj właściwości)** | Hermetyzuje pola z właściwością i aktualizuje wszystkie użycia pola Użyj wygenerowanej właściwości
   **Hermetyzuj pola (ale nadal używaj pola)** | Hermetyzuje pola z właściwością, ale pozostawia niezmienionej użycia wszystkie pola

   Właściwość zostanie utworzona natychmiast i będzie można zaktualizować odwołania do pola, jeśli wybrana.

   > [!TIP]
   > Użyj [ **podgląd zmian** ](../../ide/preview-changes.md) łącze w oknie podręcznym, aby zobaczyć wynik będzie przed wykonaniem do niego.

   ![Hermetyzuj wynik właściwości](media/encapsulate_result.png)

## <a name="see-also"></a>Zobacz też  
[Refaktoryzacji (Visual Basic)](../refactoring-vb.md)  
[Podgląd zmian](../../ide/preview-changes.md)