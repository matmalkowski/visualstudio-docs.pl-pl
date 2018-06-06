---
title: 'Porady: tworzenie cieniowania tekstury skali szarości'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 79181d81-44af-445e-9a18-03483dd70260
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ef614cbfd611eb9994f378e655d50a8656aa0441
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746328"
---
# <a name="how-to-create-a-grayscale-texture-shader"></a>Porady: tworzenie cieniowania tekstury skali szarości

W tym artykule przedstawiono sposób użycia języka programu do cieniowania wykres skierowane (DGSL) i Projektant programu do cieniowania można utworzyć cieniowania tekstury skali szarości. Ten program do cieniowania Modyfikuje wartości kolorów RGB próbki tekstury, a następnie używa go wraz z wartością alfa zostały zmodyfikowane, aby ustawić kolor końcowy.

## <a name="create-a-grayscale-texture-shader"></a>Tworzenie cieniowania tekstury skali szarości

Przed przystąpieniem do napisania go na kolor ostateczne dane wyjściowe, zmieniając wartość koloru próbki tekstury, można zaimplementować cieniowania tekstury skali szarości.

Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.

1.  Utwórz cieniowania tekstury podstawowe, zgodnie z opisem w [porady: Tworzenie podstawowego cieniowania tekstury](../designers/how-to-create-a-basic-texture-shader.md).

2.  Odłącz **RGB** terminali z **próbki tekstury** węzła z **RGB** terminali z **ostateczny kolor** węzła. W **wybierz** tryb, wybierz **RGB** terminali z **próbki tekstury** węzła, a następnie wybierz pozycję **przerwanie łączy**. Dzięki temu miejsce na węźle, który jest dodawany w następnym kroku.

3.  Dodaj **polecenie Zmniejsz nasycenie** węzła do wykresu. W **przybornika**w obszarze **filtry**, wybierz pozycję **polecenie Zmniejsz nasycenie** i przenieść ją na powierzchnię projektu.

4.  Obliczanie wartości skali szarości przy użyciu **polecenie Zmniejsz nasycenie** węzła. W **wybierz** tryb, Przenieś **RGB** terminali z **próbki tekstury** węzeł **RGB** terminali z **polecenie Zmniejsz nasycenie**  węzła.

    > [!NOTE]
    > Domyślnie **polecenie Zmniejsz nasycenie** węzła w pełni desaturates koloru okna wprowadzania i używa wag jasności standardowych konwersji skali odcieni szarości. Możesz zmienić sposób **polecenie Zmniejsz nasycenie** węzła zachowuje, zmieniając wartość **jasności** właściwości, lub tylko częściowo desaturating koloru okna wprowadzania. Aby częściowo Zmniejsz nasycenie koloru okna wprowadzania, należy podać wartość skalarną w zakresie [0,1) do **procent** terminali z **polecenie Zmniejsz nasycenie** węzła.

5.  Połączyć się ostateczny kolor z wartości koloru skali szarości. Przenieś **dane wyjściowe** terminali z **polecenie Zmniejsz nasycenie** węzeł **RGB** terminali z **ostateczny kolor** węzła.

Na poniższej ilustracji przedstawiono ukończone programu do cieniowania wykres i Podgląd programu do cieniowania stosowane do modułu.

> [!NOTE]
> Na tej ilustracji płaszczyźnie jest używany jako kształtu podglądu, a określono tekstury lepiej wykazać efekt programu do cieniowania.

![Wykres programu do cieniowania i podgląd jego wpływu](../designers/media/digit-grayscale-effect.png)

Niektórych kształtów udostępniać lepsze podglądy niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat wyświetlania podglądu programów do cieniowania w projektancie programu do cieniowania, zobacz [Designer programu do cieniowania](../designers/shader-designer.md)

## <a name="see-also"></a>Zobacz także

- [Porady: zastosowanie programu do cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Instrukcje: eksport cieniowania](../designers/how-to-export-a-shader.md)
- [Edytor obrazów](../designers/image-editor.md)
- [Projektant cieniowania](../designers/shader-designer.md)
- [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)