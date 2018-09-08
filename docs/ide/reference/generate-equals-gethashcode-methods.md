---
title: Generuj element Equals C# i zastąpienia metody GetHashCode w programie Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: deaa0b37988e2df04bb7937c76f341af849698f0
ms.sourcegitcommit: aea5cdb76fbc7eb31d1e5cc3c8d6adb0c743220f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44124973"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Generowanie elementu Equals i GetHashCode — metoda zastępuje w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

**Co:** pozwala wygenerować **jest równa** i **GetHashCode** metody.

**Kiedy:** generować te zastąpienia, gdy masz typ, który należy porównać przez co najmniej jedno pole, a nie według lokalizacji obiektu w pamięci.

**Dlaczego:**

- Przed zaimplementowaniem typ wartości, należy rozważyć zastępowanie **jest równa** metodę, aby uzyskać większą wydajność przez Domyślna implementacja metody Equals na ValueType.

- Przed zaimplementowaniem Typ referencyjny, należy rozważyć zastępowanie **jest równa** metodę, jeśli danego typu wygląda typu podstawowego, takie jak punkt, ciąg, BigNumber i tak dalej.

- Zastąp **GetHashCode** metodę, aby zezwolić na typ, który ma działać poprawnie w tabeli wyznaczania wartości skrótu. Dowiedz się więcej wskazówek na [Operatory równości](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Instrukcje

1. Umieść kursor w swojej deklaracji typu.

   ![Wyróżniony kod](media/overrides-highlight-cs.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
     - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
     - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
     - Kliknij ikonę ![Żarówka](media/bulb-cs.png) ikona, która pojawia się na lewym marginesie, gdy kursor tekstu jest już w wierszu deklaracji typu.

   ![Generowanie zastąpienia (wersja zapoznawcza)](media/overrides-preview-cs.png)

1. Wybierz **Generuj element Equals(object)** lub **Generowanie Equals i GetHashCode** z menu rozwijanego.

1. W **Wybierz składowe** okno dialogowe, zaznacz elementy członkowskie, aby wygenerować metody:

    ![Generowanie zastąpienia okna dialogowego](media/overrides-dialog-cs.png)

    > [!TIP]
    > Możesz również generować operatory z tego okna dialogowego za pomocą pola wyboru poniżej listy elementów członkowskich.

   Equals i GetHashCode zastąpienia są generowane przy użyciu domyślnej implementacji.

   ![Generowanie wyników — metoda](media/overrides-result-cs.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)