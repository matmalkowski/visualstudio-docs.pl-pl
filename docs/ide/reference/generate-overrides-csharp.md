---
title: "Generowanie Equals i GetHashCode — metoda zastąpień - generowania kodu (C#) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 56b1753dbdcfbf8ce318e964a16879f02b1482c4
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2018
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-c"></a>Generowanie Equals i GetHashCode — metoda zastąpień w języku C# #

**Co:** umożliwia wygenerowanie **jest równe** i **GetHashCode** metody.

**Kiedy:** generowania te zastąpienia, które ma typ, który reprezentuje "wartość", która powinna być porównywana przez niektóre pola, a nie według lokalizacji obiektu w pamięci.

**Dlaczego:** w przypadku wdrażania typu wartości, należy rozważyć zastąpienie metody Equals, aby uzyskać większą wydajność przez domyślną implementację metody Equals na ValueType.

W przypadku wdrażania Typ referencyjny, należy rozważyć zastąpienie metody Equals, jeśli z danym typem wygląda typu podstawowego, takie jak punkt, String, BigNumber i tak dalej.

Zastąp metodę GetHashCode w celu dopuszcza typu działać poprawnie w tablicy skrótów. Przeczytaj więcej pomocy na [Operatory równości](/dotnet/standard/design-guidelines/equality-operators).

**Jak:**

1. Umieść kursor w Twojej deklaracji typu.

   ![Wyróżniony kod](media/overrides-highlight-cs.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl +.** do wyzwalania **szybkie akcje i Refaktoryzacje** menu i wybierz **Generowanie Equals(object)** lub **Generowanie metodę Equals i GetHashCode** z menu podręcznego okna podglądu.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu i wybierz **Generowanie Equals(object)** lub **Generowanie metodę Equals i GetHashCode** z okna podglądu menu podręczne.
     * Kliknij przycisk ![Żarówka](media/bulb-cs.png) ikonę, która jest wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już na wiersz z deklaracji typu.

   ![Generowanie podglądu zastąpień](media/overrides-preview-cs.png)

1. Wybierz składniki, które mają zostać wygenerowane metody zastąpień:

    ![Generowanie okna dialogowego zastąpień](media/overrides-dialog-cs.png)

    > [!TIP]
    > Można także wygenerować operatory z tego okna dialogowego za pomocą pola wyboru poniżej listy członków.

1. Equals i GetHashCode zastąpienia zostaną wygenerowane z automatycznego domyślnej implementacji.

   ![Generowanie wyników — metoda](media/overrides-result-cs.png)

## <a name="see-also"></a>Zobacz także

[Generowanie kodu](../code-generation-in-visual-studio.md)  
[Podgląd zmian](../../ide/preview-changes.md)
