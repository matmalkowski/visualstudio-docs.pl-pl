---
title: 'Porady: tworzenie cieniowania gradientu geometrii | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f7d46fe01947e7f2813ae7eea8df81ae0b35f4f9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Porady: tworzenie modułu cieniującego gradientu geometrycznego
Ten dokument pokazuje, jak używać projektanta programu do cieniowania i język programu do cieniowania wykres skierowane do tworzenia cieniowania geometrycznego w gradientu. Ten program do cieniowania skaluje stałej wartości kolorów RGB przez wysokość każdego punktu obiektu w przestrzeni świata.  
  
 W tym dokumencie przedstawiono następujące działania:  
  
-   Dodawanie węzłów do programu do cieniowania wykresu.  
  
-   Ustawianie właściwości węzła  
  
-   Rozłączanie węzłów  
  
-   Łączenie węzłów  
  
## <a name="creating-a-geometry-based-gradient-shader"></a>Tworzenie na podstawie geometrii cieniowania gradientu  
 Programu do cieniowania na podstawie geometrii można wdrożyć przy dołączaniu pozycja piksela do programu do cieniowania. W językach cieniowanie pikseli zawiera więcej informacji niż tylko jego koloru i lokalizacji na ekranie 2-D. Piksel — znane jako *fragmentu* w niektórych systemach — jest to zbiór wartości, które opisują powierzchni, który odpowiada piksel. Wysokość każdego piksela obiektu 3-w przestrzeni świata wpływ na kolor ostateczne dane wyjściowe fragmentu korzysta z programu do cieniowania opisany w tym dokumencie.  
  
 Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.  
  
#### <a name="to-create-a-geometry-based-gradient-shader"></a>Aby utworzyć na podstawie geometrii cieniowania gradientu  
  
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
>  Na tej ilustracji kolor pomarańczowy określono, aby lepiej pokazują efekt programu do cieniowania, ale ponieważ Podgląd kształtu nie ma żadnych pozycja w przestrzeni świata, programu do cieniowania nie pełni złożono w projektancie programu do cieniowania. W rzeczywistym sceny aby zademonstrować pełnego efektu, można wyświetlić podglądu programu do cieniowania.  
  
 ![Wykres programu do cieniowania i podgląd jego wpływu](../designers/media/digit-gradient-effect-graph.png "cyfrę-gradientu-efekt-wykresu")  
  
 Niektórych kształtów udostępniać lepsze podglądy niektórych programów do cieniowania. Informacje o sposobie w wersji preview programów do cieniowania w projektancie programu do cieniowania, zobacz **Podgląd programów do cieniowania** w [Designer programu do cieniowania](../designers/shader-designer.md)  
  
 Na poniższej ilustracji przedstawiono programu do cieniowania, które jest opisane w tym dokumencie stosowana do sceny 3-w przedstawionej w [porady: Model terenu 3-](../designers/how-to-model-3-d-terrain.md). Intensywność koloru zwiększa się wraz z wysokość punktu na świecie.  
  
 ![Efekt gradientu zastosować do 3 &#45; D terenu modelu](../designers/media/digit-gradient-effect-result.png "cyfrę-gradientu-efekt-wynik")  
  
 Aby uzyskać więcej informacji dotyczących sposobu stosowania programu do cieniowania 3-w modelu, zobacz [porady: dotyczą programu do cieniowania 3-w modelu](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: dotyczą programu do cieniowania 3-w modelu](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Porady: eksportowanie programu do cieniowania](../designers/how-to-export-a-shader.md)   
 [Porady: Model terenu 3-w](../designers/how-to-model-3-d-terrain.md)   
 [Porady: tworzenie cieniowania tekstury skali szarości](../designers/how-to-create-a-grayscale-texture-shader.md)   
 [Projektant programu do cieniowania](../designers/shader-designer.md)   
 [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)