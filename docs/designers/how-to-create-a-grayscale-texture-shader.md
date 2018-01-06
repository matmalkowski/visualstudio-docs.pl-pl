---
title: "Porady: tworzenie cieniowania tekstury skali szarości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79181d81-44af-445e-9a18-03483dd70260
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 515aefab86a0a047d7074d127d9dd621feb0117c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-grayscale-texture-shader"></a>Porady: tworzenie cieniowania tekstury skali szarości
Ten dokument pokazuje, jak używać Designer programu do cieniowania i języka programu do cieniowania wykres skierowane (DGSL) do tworzenia cieniowania tekstury skali szarości. Ten program do cieniowania Modyfikuje wartości kolorów RGB próbki tekstury, a następnie używa go wraz z wartością alfa zostały zmodyfikowane, aby ustawić kolor końcowy.  
  
## <a name="creating-a-grayscale-texture-shader"></a>Tworzenie cieniowania tekstury skali szarości  
 Przed przystąpieniem do napisania go na kolor ostateczne dane wyjściowe, zmieniając wartość koloru próbki tekstury, można zaimplementować cieniowania tekstury skali szarości.  
  
 Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.  
  
#### <a name="to-create-a-grayscale-texture-shader"></a>Aby utworzyć cieniowania tekstury skali szarości  
  
1.  Utwórz cieniowania tekstury podstawowe, zgodnie z opisem w [porady: Tworzenie podstawowego cieniowania tekstury](../designers/how-to-create-a-basic-texture-shader.md).  
  
2.  Odłącz **RGB** terminali z **próbki tekstury** węzła z **RGB** terminali z **ostateczny kolor** węzła. W **wybierz** tryb, wybierz **RGB** terminali z **próbki tekstury** węzła, a następnie wybierz pozycję **przerwanie łączy**. Dzięki temu miejsce na węźle, który jest dodawany w następnym kroku.  
  
3.  Dodaj **polecenie Zmniejsz nasycenie** węzła do wykresu. W **przybornika**w obszarze **filtry**, wybierz pozycję **polecenie Zmniejsz nasycenie** i przenieść ją na powierzchnię projektu.  
  
4.  Obliczanie wartości skali szarości przy użyciu **polecenie Zmniejsz nasycenie** węzła. W **wybierz** tryb, Przenieś **RGB** terminali z **próbki tekstury** węzeł **RGB** terminali z **polecenie Zmniejsz nasycenie**  węzła.  
  
    > [!NOTE]
    >  Domyślnie **polecenie Zmniejsz nasycenie** węzła w pełni desaturates koloru okna wprowadzania i używa wag jasności standardowych konwersji skali odcieni szarości. Możesz zmienić sposób **polecenie Zmniejsz nasycenie** węzła zachowuje, zmieniając wartość **jasności** właściwości, lub tylko częściowo desaturating koloru okna wprowadzania. Aby częściowo Zmniejsz nasycenie koloru okna wprowadzania, należy podać wartość skalarną w zakresie [0,1) do **procent** terminali z **polecenie Zmniejsz nasycenie** węzła.  
  
5.  Połączyć się ostateczny kolor z wartości koloru skali szarości. Przenieś **dane wyjściowe** terminali z **polecenie Zmniejsz nasycenie** węzeł **RGB** terminali z **ostateczny kolor** węzła.  
  
 Na poniższej ilustracji przedstawiono ukończone programu do cieniowania wykres i Podgląd programu do cieniowania stosowane do modułu.  
  
> [!NOTE]
>  Na tej ilustracji płaszczyźnie jest używany jako kształtu podglądu, a określono tekstury lepiej wykazać efekt programu do cieniowania.  
  
 ![Wykres programu do cieniowania i podgląd jego wpływu](../designers/media/digit-grayscale-effect.png "cyfrę skali szarości efektu")  
  
 Niektórych kształtów udostępniać lepsze podglądy niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat wyświetlania podglądu programów do cieniowania w projektancie programu do cieniowania, zobacz [Designer programu do cieniowania](../designers/shader-designer.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: dotyczą programu do cieniowania 3-w modelu](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Porady: eksportowanie programu do cieniowania](../designers/how-to-export-a-shader.md)   
 [Edytor obrazów](../designers/image-editor.md)   
 [Projektant programu do cieniowania](../designers/shader-designer.md)   
 [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)