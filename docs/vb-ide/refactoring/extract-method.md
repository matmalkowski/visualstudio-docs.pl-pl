---
title: "Wyodrębnienie metody - refaktoryzacji (Visual Basic) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: 8ad16c15-432b-4b8c-86fd-5f31ad652d24
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractmethod
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: 6ec25b8c0e2a583364ff3c6418515507cdc04d40
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="extract-a-method-in-visual-basic"></a>Wyodrębnij metodę w języku Visual Basic
**Co:** pozwala włączyć do własnej metody fragment kodu.

**Kiedy:** masz fragment kodu istniejących w niektórych metodę, która musi zostać wywołana z innej metody.  

**Dlaczego:** użytkownik może kopiowanie/wklejanie kodu, ale który może doprowadzić do duplikacji.  Lepszym rozwiązaniem jest Refaktoryzuj ten fragment do własnej metody, które można wywołać za darmo inną metodą.

**Jak:**

1. Wyróżnij kodu, który zostanie wyodrębniony:

   ![Wyróżniony kod](media/extractmethod_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Klawiatury**
     * Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + M**.  (Należy pamiętać, że skrót klawiaturowy mogą być różne oparte na profil, który wybrano).
     * Naciśnij klawisz **Ctrl +.** Aby wyzwalacz **szybkie akcje i Refaktoryzacje** menu i wybierz **Wyodrębnij metodę** z menu podręcznego okna podglądu.
   * **Myszy**
     * Wybierz **Edytuj > Refaktoryzuj > wyodrębniania metody**.
     * Kliknij prawym przyciskiem myszy kod i wybierz **Refaktoryzuj > wyodrębnić > Wyodrębnij metodę**.
     * Kliknij prawym przyciskiem myszy kod, wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **Wyodrębnij metodę** z menu podręcznego okna podglądu.

   Metoda zostanie utworzony natychmiast.  W tym miejscu można teraz zmienić nazwę metody po prostu, wpisując nazwę nowego.

   > [!TIP]
   > Można także zaktualizować komentarze i innymi ciągami, aby użyć tej nowej nazwy oraz [podgląd zmian](../../ide/preview-changes.md) przed zapisaniem, za pomocą pola wyboru w **zmienić** pole, który jest wyświetlany u góry rogu środowiskiem IDE.

   ![Zmień nazwę — metoda](media/extractmethod_rename.png)

1. Po zakończeniu modyfikowania zmiany, kliknij przycisk **Zastosuj** przycisk lub naciśnij przycisk **Enter** , a zmiany zostaną zatwierdzone.

## <a name="see-also"></a>Zobacz też  
[Refaktoryzacji (Visual Basic)](../refactoring-vb.md)  
[Podgląd zmian](../../ide/preview-changes.md)