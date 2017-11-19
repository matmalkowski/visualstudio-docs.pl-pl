---
title: 'Porady: tworzenie cieniowania tekstury podstawowej | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5af113fb-6415-4be0-8b23-10fddb10e80a
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4620278c98ea373b8e0cde387f1b5526bf21349b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-basic-texture-shader"></a>Porady: tworzenie cieniowania tekstury podstawowej
Ten dokument przedstawia sposób umożliwiają utworzenie cieniowania tekstury jednym Designer programu do cieniowania i języka programu do cieniowania wykres skierowane (DGSL). Ten program do cieniowania Ustawia kolor końcowy bezpośrednio do RGB i wartości alfa, które są pobierane z tekstury.  
  
 W tym dokumencie przedstawiono następujące działania:  
  
-   Usuwanie węzłów z wykresu programu do cieniowania  
  
-   Dodawanie węzłów do wykresu.  
  
-   Ustawianie parametrów programu do cieniowania  
  
-   Ustawienie parametru widoczności  
  
-   Łączenie węzłów  
  
## <a name="creating-a-basic-texture-shader"></a>Tworzenie cieniowania tekstury podstawowej  
 Można zaimplementować cieniowania podstawowy, jeden tekstury pisząc wartości kolorów i alfa próbki tekstury bezpośrednio na kolor ostateczne dane wyjściowe.  
  
 Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.  
  
#### <a name="to-create-a-basic-texture-shader"></a>Aby utworzyć cieniowania tekstury podstawowej  
  
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
>  Na tej ilustracji płaszczyźnie jest używany jako kształtu podglądu, a określono tekstury lepiej wykazać efekt programu do cieniowania.  
  
 ![Wykres programu do cieniowania i podgląd jego wpływu](../designers/media/digit-texture-effect.png "cyfrę tekstury efektu")  
  
 Niektórych kształtów udostępniać lepsze podglądy niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat wersji preview programów do cieniowania w projektancie programu do cieniowania, zobacz [Designer programu do cieniowania](../designers/shader-designer.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: dotyczą programu do cieniowania 3-w modelu](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Edytor obrazów](../designers/image-editor.md)   
 [Projektant programu do cieniowania](../designers/shader-designer.md)   
 [Węzły projektanta programu do cieniowania](../designers/shader-designer-nodes.md)