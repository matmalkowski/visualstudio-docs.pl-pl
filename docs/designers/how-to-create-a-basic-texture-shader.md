---
title: 'Porady: tworzenie cieniowania tekstury podstawowej'
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 5af113fb-6415-4be0-8b23-10fddb10e80a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: efe0031eed40424dbe9dc0219ecf82c69e44b33c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-a-basic-texture-shader"></a>Porady: tworzenie cieniowania tekstury podstawowej

W tym artykule przedstawiono sposób użycia Designer programu do cieniowania i języka programu do cieniowania wykres skierowane (DGSL) do utworzenia cieniowania jednym tekstury. Ten program do cieniowania Ustawia kolor końcowy bezpośrednio do RGB i wartości alfa, które są pobierane z tekstury.

## <a name="create-a-basic-texture-shader"></a>Utwórz cieniowania tekstury podstawowej

Można zaimplementować cieniowania podstawowy, jeden tekstury pisząc wartości kolorów i alfa próbki tekstury bezpośrednio na kolor ostateczne dane wyjściowe.

Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.

1.  Utwórz DGSL programu do cieniowania do pracy z. Aby uzyskać informacje o sposobie dodawania cieniowania DGSL do projektu, w sekcji wprowadzenie w [Designer programu do cieniowania](../designers/shader-designer.md).

2.  Usuń **kolor punktu** węzła. W **wybierz** tryb, wybierz **kolor punktu** węzeł, a następnie na pasku menu wybierz pozycję **Edytuj**, **usunąć**. Dzięki temu miejsce na węźle, który jest dodawany w następnym kroku.

3.  Dodaj **próbki tekstury** węzła do wykresu. W **przybornika**w obszarze **tekstury**, wybierz pozycję **próbki tekstury** i przenieść ją na powierzchnię projektu.

4.  Dodaj **koordynować tekstury** węzła do wykresu. W **przybornika**w obszarze **tekstury**, wybierz pozycję **koordynować tekstury** i przenieść ją na powierzchnię projektu.

5.  Wybierz tekstury do zastosowania. W **wybierz** tryb, wybierz **próbki tekstury** węzeł, a następnie w **właściwości** okna, określ tekstury, którego chcesz używać przy użyciu **Filename**  właściwości.

6.  Udostępnij tekstury publicznie. Wybierz **próbki tekstury** węzła, a następnie w **właściwości** ustaw **dostępu** właściwości **publicznego**. Teraz można ustawić tekstury z innego narzędzia, takie jak **edytorze modeli**.

7.  Współrzędne tekstury należy połączyć się z przykładem tekstury. W **wybierz** tryb, Przenieś **dane wyjściowe** terminali z **koordynować tekstury** węzeł **UV** terminali z **tekstury Przykładowe** węzła. To połączenie próbek w określonych współrzędnych tekstury.

8.  Przykładowe tekstury nawiązać połączenia z ostateczny kolor. Przenieś **RGB** terminali z **próbki tekstury** węzeł **RGB** terminali z **ostateczny kolor** węzeł, a następnie przenieść **Alfa** terminali z **próbki tekstury** węzeł **alfa** terminali z **ostateczny kolor** węzła.

Na poniższej ilustracji przedstawiono ukończone programu do cieniowania wykres i Podgląd programu do cieniowania stosowane do modułu.

> [!NOTE]
> Na tej ilustracji płaszczyźnie jest używany jako kształtu podglądu, a określono tekstury lepiej wykazać efekt programu do cieniowania.

![Wykres programu do cieniowania i podgląd jego wpływu](../designers/media/digit-texture-effect.png "cyfrę tekstury efektu")

Niektórych kształtów udostępniać lepsze podglądy niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat wersji preview programów do cieniowania w projektancie programu do cieniowania, zobacz [Designer programu do cieniowania](../designers/shader-designer.md)

## <a name="see-also"></a>Zobacz także

- [Porady: zastosowanie programu do cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Edytor obrazów](../designers/image-editor.md)
- [Projektant cieniowania](../designers/shader-designer.md)
- [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)