---
title: "Refaktoryzacja wyodrębniania metody - (C#) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: d79d55ae-f6bb-4902-8db2-e7fe01bdb0bf
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractmethod
dev_langs: csharp
ms.openlocfilehash: 3890d427ed2888647675a241f4e62a5635d7308c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="extract-a-method-in-c"></a>Wyodrębnij metodę w języku C# #
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
[Refaktoryzacja (C#)](../refactoring-csharp.md)  
[Podgląd zmian](../../ide/preview-changes.md)