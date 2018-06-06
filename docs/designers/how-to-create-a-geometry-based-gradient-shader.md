---
title: 'Porady: tworzenie modułu cieniującego gradientu geometrycznego'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 056eae05911af2a9ae6be12f2d3d7b18106df9b1
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745779"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Porady: tworzenie modułu cieniującego gradientu geometrycznego

W tym artykule pokazano, jak używać projektanta programu do cieniowania i język programu do cieniowania wykres skierowane do tworzenia cieniowania geometrycznego w gradientu. Ten program do cieniowania skaluje stałej wartości kolorów RGB przez wysokość każdego punktu obiektu w przestrzeni świata.

## <a name="create-a-geometry-based-gradient-shader"></a>Tworzenie cieniowania gradientu geometrycznego

Programu do cieniowania na podstawie geometrii można wdrożyć przy dołączaniu pozycja piksela do programu do cieniowania. W językach cieniowanie pikseli zawiera więcej informacji niż tylko jego koloru i lokalizacji na ekranie 2D. Piksel — znane jako *fragmentu* w niektórych systemach — jest to zbiór wartości, które opisują powierzchni, który odpowiada piksel. Wysokość każdego piksela obiektu 3D w przestrzeni świata wpływ na kolor ostateczne dane wyjściowe fragmentu korzysta z programu do cieniowania opisany w tym dokumencie.

Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.

1.  Utwórz DGSL programu do cieniowania do pracy z. Aby uzyskać informacje o sposobie dodawania cieniowania DGSL do projektu, w sekcji wprowadzenie w [Designer programu do cieniowania](../designers/shader-designer.md).

2.  Odłącz **kolor punktu** węzła z **ostateczny kolor** węzła. Wybierz **RGB** terminali z **kolor punktu** węzeł, a następnie wybierz pozycję **przerwanie łączy**. Dzięki temu miejsce na węźle, który jest dodawany w następnym kroku.

3.  Dodaj **mnożenia** węzła do wykresu. W **przybornika**w obszarze **matematyczne**, wybierz pozycję **mnożenia** i przenieść ją na powierzchnię projektu.

4.  Dodaj **wektor maski** węzła do wykresu. W **przybornika**w obszarze **narzędzie**, wybierz pozycję **wektor maska** i przenieść ją na powierzchnię projektu.

5.  Określ wartości maski **wektor maski** węzła. W **wybierz** tryb, wybierz **wektor maski** węzeł, a następnie w **właściwości** ustaw **zielony / Y** właściwości **True**, a następnie ustaw **czerwony / X**, **Blue / Z** i **alfa / W** właściwości **False**. W tym przykładzie **czerwony / X**, **zielony / Y**, i **Blue / Z** właściwości odpowiadają x, y i składniki z **pozycji World** węzeł, i **alfa / W** jest używana. Ponieważ tylko **zielony / Y** ustawiono **True**, po jego są wyświetlane jako znaki pozostanie tylko składnik y wektor wejściowy.

6.  Dodaj **pozycji World** węzła do wykresu. W **przybornika**w obszarze **stałe**, wybierz pozycję **pozycji World** i przenieść ją na powierzchnię projektu.

7.  Maski pozycji miejsca na świecie fragmentu. W **wybierz** tryb, Przenieś **dane wyjściowe** terminali z **pozycji World** węzeł **wektor** terminali z **maski Wektor** węzła. To połączenie maski pozycji fragmentu ignorowania x i z składników.

8.  Należy pomnożyć stała kolor RGB według położenia miejsca na świecie maskowanego. Przenieś **RGB** terminali z **kolor punktu** węzeł **Y** terminali z **mnożenia** węzeł, a następnie przenieść  **Dane wyjściowe** terminali z **wektor maski** węzeł **X** terminali z **mnożenia** węzła. To połączenie skaluje wartości koloru przez wysokość piksela w przestrzeni świata.

9. Wartość koloru skalowanych należy nawiązać ostateczny kolor. Przenieś **dane wyjściowe** terminali z **mnożenia** węzeł **RGB** terminali z **ostateczny kolor** węzła.

Na poniższej ilustracji przedstawiono ukończone programu do cieniowania wykres i Podgląd programu do cieniowania zastosowany do sfery.

> [!NOTE]
> Na tej ilustracji kolor pomarańczowy określono, aby lepiej pokazują efekt programu do cieniowania, ale ponieważ Podgląd kształtu nie ma żadnych pozycja w przestrzeni świata, programu do cieniowania nie pełni złożono w projektancie programu do cieniowania. W rzeczywistym sceny aby zademonstrować pełnego efektu, można wyświetlić podglądu programu do cieniowania.

 ![Wykres programu do cieniowania i podgląd jego wpływu](../designers/media/digit-gradient-effect-graph.png)

 Niektórych kształtów udostępniać lepsze podglądy niektórych programów do cieniowania. Informacje o sposobie w wersji preview programów do cieniowania w projektancie programu do cieniowania, zobacz **Podgląd programów do cieniowania** w [Designer programu do cieniowania](../designers/shader-designer.md)

 Na poniższej ilustracji przedstawiono programu do cieniowania, które jest opisane w tym dokumencie stosowana do sceny 3W, która jest uruchomiona w [porady: Model 3D terenu](../designers/how-to-model-3-d-terrain.md). Intensywność koloru zwiększa się wraz z wysokość punktu na świecie.

 ![Efekt gradientu stosowane do 3&#45;modelu terenu D](../designers/media/digit-gradient-effect-result.png)

 Aby uzyskać więcej informacji dotyczących sposobu stosowania programu do cieniowania do modelu 3D, zobacz [porady: dotyczą programu do cieniowania modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Zobacz także

- [Porady: zastosowanie programu do cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Instrukcje: eksport cieniowania](../designers/how-to-export-a-shader.md)
- [Porady: Model terenu 3D](../designers/how-to-model-3-d-terrain.md)
- [Instrukcje: tworzenie cieniowania tekstury skali szarości](../designers/how-to-create-a-grayscale-texture-shader.md)
- [Projektant cieniowania](../designers/shader-designer.md)
- [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)