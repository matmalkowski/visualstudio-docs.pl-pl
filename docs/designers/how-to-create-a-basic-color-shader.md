---
title: 'Porady: tworzenie cieniowania koloru podstawowego'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fba456d6a06281e0472e907b27bcd76b57b17e93
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747121"
---
# <a name="how-to-create-a-basic-color-shader"></a>Porady: tworzenie cieniowania koloru podstawowego

W tym artykule przedstawiono sposób użycia języka programu do cieniowania wykres skierowane (DGSL) i Projektant programu do cieniowania można utworzyć cieniowania koloru. Ten program do cieniowania Ustawia kolor końcowy stałej wartości kolorów RGB.

## <a name="create-a-flat-color-shader"></a>Utwórz cieniowania koloru

Można zaimplementować cieniowania koloru zapisując wartości koloru stała kolor RGB kolor ostateczne dane wyjściowe.

Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.

1.  Utwórz DGSL programu do cieniowania do pracy z. Aby uzyskać informacje o sposobie dodawania cieniowania DGSL do projektu, w sekcji wprowadzenie w [Designer programu do cieniowania](../designers/shader-designer.md).

2.  Usuń **kolor punktu** węzła. Użyj **wybierz** narzędzie, aby wybrać **kolor punktu** węzeł, a następnie na pasku menu wybierz pozycję **Edytuj**, **usunąć**.

3.  Dodaj **kolor stałej** węzła do wykresu. W **przybornika**w obszarze **stałe**, wybierz pozycję **kolor stałej** i przenieść ją na powierzchnię projektu.

4.  Określ wartość koloru **kolor stałej** węzła. Użyj **wybierz** narzędzie, aby wybrać **kolor stałej** węzła, a następnie w **właściwości** okna w **dane wyjściowe** właściwości, określ wartość koloru. Dla pomarańczowy Określ wartość (1.0, 0,5, 0,2, 1.0).

5.  Stała kolor nawiązać połączenia z ostateczny kolor. Do utworzenia połączenia, Przenieś **RGB** terminali z **kolor stałej** węzeł **RGB** terminali z **ostateczny kolor** węzeł, i następnie przenieś **alfa** terminali z **kolor stałej** węzeł **alfa** terminali z **ostateczny kolor** węzła. Te połączenia ustawioną ostateczny kolor stała kolor zdefiniowany w poprzednim kroku.

Na poniższej ilustracji przedstawiono ukończone programu do cieniowania wykres i Podgląd programu do cieniowania stosowane do modułu.

> [!NOTE]
> Na ilustracji kolor pomarańczowy określono lepiej wykazać efekt programu do cieniowania.

![Wykres programu do cieniowania i jego wynik 3&#45;modelu D](../designers/media/digit-flat-color-effect.png)

Niektórych kształtów udostępniać lepsze podglądy niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat wersji preview programów do cieniowania w projektancie programu do cieniowania, zobacz [Designer programu do cieniowania](../designers/shader-designer.md).

## <a name="see-also"></a>Zobacz także

- [Porady: zastosowanie programu do cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Instrukcje: eksport cieniowania](../designers/how-to-export-a-shader.md)
- [Projektant cieniowania](../designers/shader-designer.md)
- [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)