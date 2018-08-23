---
title: 'Porady: tworzenie cieniowania koloru podstawowego | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 23a7082c305bdabf139e284d448fafdf375762e2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42674797"
---
# <a name="how-to-create-a-basic-color-shader"></a>Porady: tworzenie cieniowania koloru podstawowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: tworzenie cieniowania koloru podstawowego](https://docs.microsoft.com/visualstudio/designers/how-to-create-a-basic-color-shader).  
  
W tym dokumencie przedstawiono sposób użycia języka programu do cieniowania wykres kierowany (DGSL) i Projektant programu do cieniowania do tworzenie cieniowania koloru. Ten program do cieniowania Ustawia kolor końcowy stałej wartości kolorów RGB.  
  
 Ten dokument przedstawia te działania:  
  
-   Usuwanie węzłów z wykresu  
  
-   Dodawanie węzłów do wykresu  
  
-   Ustawianie właściwości węzła  
  
-   Łączenie z węzłami  
  
## <a name="creating-a-flat-color-shader"></a>Tworzenie cieniowania koloru  
 Możesz zaimplementować cieniowania koloru, zapisując wartość koloru stałej kolor RGB kolor końcowych danych wyjściowych.  
  
 Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.  
  
#### <a name="to-create-a-flat-color-shader"></a>Do tworzenie cieniowania koloru  
  
1.  Tworzenie modułu cieniującego DGSL chcesz pracować. Aby uzyskać informacje dotyczące sposobu dodawania modułu cieniującego DGSL do projektu, zobacz sekcję pierwsze kroki w [Shader Designer](../designers/shader-designer.md).  
  
2.  Usuń **koloru punktu** węzła. Użyj **wybierz** narzędzie do wybierania **koloru punktu** węzła, a następnie na pasku menu wybierz **Edytuj**, **Usuń**.  
  
3.  Dodaj **stała koloru** węzła do wykresu. W **przybornika**w obszarze **stałe**, wybierz opcję **stała koloru** i przenieś go do powierzchni projektowej.  
  
4.  Określ wartość koloru **stała koloru** węzła. Użyj **wybierz** narzędzie do wybierania **stała koloru** węzła, a następnie w **właściwości** okna w **dane wyjściowe** właściwości, określ wartość koloru. Na pomarańczowy należy określić wartość (1.0, 0,5, 0.2, 1.0).  
  
5.  Stała koloru nawiązać połączenie ostateczny kolor. Pod kątem tworzenia połączeń, należy przenieść **RGB** terminali z **stała koloru** węzeł **RGB** terminali z **ostateczny kolor** węzła, i następnie przenieś **alfa** terminali z **stała koloru** węzeł, aby **alfa** terminali z **ostateczny kolor** węzła. Te połączenia Ustaw kolor końcowy stała koloru zdefiniowane w poprzednim kroku.  
  
 Poniższej ilustracji ukończone programu do cieniowania programu graph i wersję zapoznawczą programu do cieniowania stosowane do modułu.  
  
> [!NOTE]
>  Na ilustracji koloru pomarańczowego określono lepiej wykazać efekt programu do cieniowania.  
  
 ![Wykres modułu cieniującego i jego wynik na 3&#45;modelu D](../designers/media/digit-flat-color-effect.png "cyfrę — stosowana jest stała — — efekt koloru")  
  
 Niektórych kształtów udostępniać lepsze wersje zapoznawcze niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat programów do cieniowania w projektancie programu do cieniowania w wersji zapoznawczej, zobacz [Shader Designer](../designers/shader-designer.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: stosowanie cieniowania do modelu 3-D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Porady: eksport cieniowania](../designers/how-to-export-a-shader.md)   
 [Projektant programu do cieniowania](../designers/shader-designer.md)   
 [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)



