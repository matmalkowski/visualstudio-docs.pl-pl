---
title: 'Porady: tworzenie tekstury podstawowej'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0222e8bf-d29f-421b-9b1f-123d500fa179
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d58cbb439eb370af16ee68ca03a4d1db467861f0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-basic-texture"></a>Porady: tworzenie tekstury podstawowej
Ten dokument pokazano, jak umożliwiają utworzenie tekstury podstawowej edytora obrazów.

 W tym dokumencie przedstawiono następujące działania:

-   Ustawianie rozmiaru tekstury

-   Ustawienie kolory pierwszego planu i tła

-   Za pomocą kanału alfa (przezroczystości)

-   Przy użyciu **wypełnienia** i **elipsy** narzędzia

-   Ustawienie właściwości narzędzia

## <a name="creating-a-basic-texture"></a>Tworzenie podstawowych tekstury
 Edytor obrazów służy do tworzenia i modyfikowania obrazów i tekstur gry lub aplikacji.

 Poniższe kroki pokazują, jak utworzyć tekstury, który reprezentuje element docelowy "bullseye". Gdy skończysz, tekstury powinien wyglądać poniższej ilustracji. Aby lepiej zaprezentować przezroczystość tekstury, edytor obrazów skonfigurowano na potrzeby wzorzec zielony, szachownicą go wyświetlić.

 ![Miejsce docelowe "Bullseye" z przezroczystość wyświetlany na zielono](../designers/media/digit-bullseye-texture-in-editor.png "cyfrę-Bullseye-tekstury-w — Edytor")

 Przed rozpoczęciem upewnij się, że **właściwości** okno jest wyświetlane. Możesz użyć **właściwości** okno, aby ustawić rozmiar obrazu, zmień właściwości narzędzia i określić kolory podczas pracy.

#### <a name="to-create-a-bullseye-target-texture"></a>Aby utworzyć tekstury docelowej "bullseye"

1.  Utwórz tekstury do pracy z. Aby uzyskać informacje o sposobie dodawania tekstury do projektu, w sekcji wprowadzenie w [edytor obrazów](../designers/image-editor.md).

2.  Ustawienie rozmiaru obrazu 512 x 512 pikseli. W **właściwości** Ustaw wartości **szerokość** i **wysokość** właściwości `512`.

3.  Na pasku narzędzi edytora obrazów, wybierz **wypełnienia** narzędzia. **Właściwości** oknie zostaną wyświetlone właściwości **wypełnienia** wraz z właściwości obrazu.

4.  Ustaw kolor pierwszego planu na kolor czarny pełna przezroczystość. W **właściwości** okna w **kolory** właściwości grupy wybierz **pierwszego planu**. Ustaw wartości **R**, **G**, **B**, i **A** właściwości obok próbnika kolorów do `0`.

5.  Na pasku narzędzi edytora obrazów, wybierz **wypełnienia** narzędzia, a następnie naciśnij i przytrzymaj klawisz Shift i wybrać dowolny punkt na obrazie. Przy użyciu klawisza Shift powoduje, że wartość alfa koloru wypełnienia zastąpić kolor obrazu. w przeciwnym razie wartość alfa umożliwia blend kolor wypełnienia wraz z koloru z obrazu.

    > [!IMPORTANT]
    >  Ten krok, wraz z wybór kolorów w poprzednim kroku gwarantuje, że podstawowy obraz jest gotowy do docelową teksturę "bullseye" będzie rysowany. Gdy obraz jest wypełniony przezroczysty czarne — i dlatego obramowania elementu docelowego jest czarny — nie będzie żadnych aliasów artefakty wokół docelowej.

6.  Na pasku narzędzi edytora obrazów, wybierz **elipsy** narzędzia.

7.  Kolor pierwszego planu na kolor czarny pełni nieprzezroczyste. Ustaw wartości **R**, **G**, i **B** właściwości `0` i wartość **A** właściwości `255`.

8.  Kolor tła na kolor biały pełni nieprzezroczyste. W **właściwości** okna w **kolory** właściwości grupy wybierz **tła**. Ustaw wartości **R**, **G**, **B**, i **A** właściwości `255`.

9. Ustawia szerokość konturu elipsy. W **właściwości** okna w **wygląd** grupy właściwość, ustaw wartość **szerokość** właściwości `8`.

10. Upewnij się, że wygładzanie jest włączona. W **właściwości** okna w **wygląd** właściwości grupy, upewnij się, że **wygładzanie** właściwość jest ustawiona.

11. Przy użyciu **elipsy** narzędzie, narysuj koło z współrzędnych pikseli `(3, 3)` do współrzędnych pikseli `(508, 508)`. Do rysowania więcej okręgu łatwe, możesz można naciśnij i przytrzymaj klawisz Shift podczas rysowania.

    > [!NOTE]
    >  Współrzędne pikseli w bieżącym położeniu kursora są wyświetlane na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] paska stanu.

12. Zmiana koloru tła. Ustaw **R** do `44`, **G** do `165`, **B** do `211`, i **A** do `255`.

13. Rysowanie innego koło z współrzędnych pikseli `(64, 64)` do współrzędnych pikseli `(448, 448)`.

14. Zmiana koloru tła do pełni nieprzezroczyste biały. Ustaw **R**, **G**, **B**, i **A** do `255`.

15. Rysowanie innego koło z współrzędnych pikseli `(128, 128)` do współrzędnych pikseli `(384, 384)`.

16. Zmiana koloru tła. Ustaw **R** do `255`, **G** i **B** do `64`, i **A** do `255`.

17. Rysowanie innego koło z współrzędnych pikseli `(192, 192)` do współrzędnych pikseli `(320, 320)`.

 Docelową teksturę "bullseye" zostało zakończone. Oto finalnego obrazu wyświetlany z efektem przezroczystości.

 ![Zakończenie "bullseye" target tekstury](../designers/media/gfx_image_demo_bullseye.png "gfx_image_demo_bullseye")

 Jako kolejny krok można wygenerować poziomów Mipmapy tego tekstury. Aby uzyskać informacje, zobacz [porady: tworzenie i modyfikowanie MCI poziomy](../designers/how-to-create-and-modify-mip-levels.md).

## <a name="see-also"></a>Zobacz także

- [Edytor obrazów](../designers/image-editor.md)