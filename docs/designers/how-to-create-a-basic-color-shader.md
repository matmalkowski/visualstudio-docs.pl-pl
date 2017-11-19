---
title: 'Porady: tworzenie cieniowania kolor podstawowy | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1bb3ee7a4b646e39e22752d336d5414f64551ce0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-basic-color-shader"></a>Porady: tworzenie cieniowania koloru podstawowego
Ten dokument przedstawia sposób umożliwiają utworzenie cieniowania koloru Designer programu do cieniowania i języka programu do cieniowania wykres skierowane (DGSL). Ten program do cieniowania Ustawia kolor końcowy stałej wartości kolorów RGB.  
  
 W tym dokumencie przedstawiono następujące działania:  
  
-   Usuwanie węzłów z wykresu  
  
-   Dodawanie węzłów do wykresu.  
  
-   Ustawianie właściwości węzła  
  
-   Łączenie węzłów  
  
## <a name="creating-a-flat-color-shader"></a>Tworzenie cieniowania koloru  
 Można zaimplementować cieniowania koloru zapisując wartości koloru stała kolor RGB kolor ostateczne dane wyjściowe.  
  
 Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.  
  
#### <a name="to-create-a-flat-color-shader"></a>Aby utworzyć cieniowania koloru  
  
1.  Utwórz DGSL programu do cieniowania do pracy z. Aby uzyskać informacje o sposobie dodawania cieniowania DGSL do projektu, w sekcji wprowadzenie w [Designer programu do cieniowania](../designers/shader-designer.md).  
  
2.  Usuń **kolor punktu** węzła. Użyj **wybierz** narzędzie, aby wybrać **kolor punktu** węzeł, a następnie na pasku menu wybierz pozycję **Edytuj**, **usunąć**.  
  
3.  Dodaj **kolor stałej** węzła do wykresu. W **przybornika**w obszarze **stałe**, wybierz pozycję **kolor stałej** i przenieść ją na powierzchnię projektu.  
  
4.  Określ wartość koloru **kolor stałej** węzła. Użyj **wybierz** narzędzie, aby wybrać **kolor stałej** węzła, a następnie w **właściwości** okna w **dane wyjściowe** właściwości, określ wartość koloru. Dla pomarańczowy Określ wartość (1.0, 0,5, 0,2, 1.0).  
  
5.  Stała kolor nawiązać połączenia z ostateczny kolor. Do utworzenia połączenia, Przenieś **RGB** terminali z **kolor stałej** węzeł **RGB** terminali z **ostateczny kolor** węzeł, i następnie przenieś **alfa** terminali z **kolor stałej** węzeł **alfa** terminali z **ostateczny kolor** węzła. Te połączenia ustawioną ostateczny kolor stała kolor zdefiniowany w poprzednim kroku.  
  
 Na poniższej ilustracji przedstawiono ukończone programu do cieniowania wykres i Podgląd programu do cieniowania stosowane do modułu.  
  
> [!NOTE]
>  Na ilustracji kolor pomarańczowy określono lepiej wykazać efekt programu do cieniowania.  
  
 ![Wykres programu do cieniowania i jego wynik 3 &#45; modelu D](../designers/media/digit-flat-color-effect.png "cyfrę płaski — kolor-efekt uboczny")  
  
 Niektórych kształtów udostępniać lepsze podglądy niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat wersji preview programów do cieniowania w projektancie programu do cieniowania, zobacz [Designer programu do cieniowania](../designers/shader-designer.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: dotyczą programu do cieniowania 3-w modelu](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Porady: eksportowanie programu do cieniowania](../designers/how-to-export-a-shader.md)   
 [Projektant programu do cieniowania](../designers/shader-designer.md)   
 [Węzły projektanta programu do cieniowania](../designers/shader-designer-nodes.md)