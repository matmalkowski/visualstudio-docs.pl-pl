---
title: 'Porady: Tworzenie podstawowego modułu cieniującego Lamberta | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0aee168b1788ce41f807d6b656588e7094e257b8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680585"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Porady: tworzenie podstawowego modułu cieniującego Lamberta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: Tworzenie podstawowego cieniowania Lamberta](https://docs.microsoft.com/visualstudio/designers/how-to-create-a-basic-lambert-shader).  
  
W tym dokumencie przedstawiono sposób użycia Shader Designer i język programu do cieniowania wykres kierowany (DGSL) do utworzenia oświetlenia modułu cieniującego, który implementuje klasycznego modelu oświetlenia Lamberta.  
  
 Ten dokument przedstawia te działania:  
  
-   Dodawanie węzłów do wykresu programu do cieniowania  
  
-   Trwa rozłączanie węzłów  
  
-   Łączenie z węzłami  
  
## <a name="the-lambert-lighting-model"></a>Modelu oświetlenia Lamberta  
 Model oświetlenia Lambert dołącza oświetlenia otoczenia i kierunkowe odcień obiektów w scenie 3-D. Otoczenia składniki zapewniają podstawowy poziom oświetlenia w scenie 3-D. Kierunkowe składniki zapewniają dodatkowe oświetlenia ze źródeł (dalekie) światła kierunkowego. Oświetlenia otoczenia ma wpływ na wszystkie powierzchnie w scenie tak samo, niezależnie od ich orientacji. Dla danego powierzchni jest to produkt koloru otoczenia powierzchni i koloru i intensywności oświetlenia otoczenia na scenie. Światła kierunkowego ma wpływ na co narażonego na ataki w scenie inaczej, zgodnie z orientacją powierzchni względem kierunku po stronie źródła światła. Jest to produkt kolor rozpraszania i orientację powierzchni, a kolor, intensywność i kierunek źródła światła. Powierzchnie, które są spowodowane bezpośrednio do źródła światła otrzymują maksymalny udział i powierzchnie, które są spowodowane bezpośrednio natychmiast otrzymać nie wkład. W ramach modelu oświetlenia Lamberta składnik otoczenia i co najmniej jednego składnika kierunkowe są łączone w celu określenia udział łączny kolor rozpraszania dla każdego punktu w obiekcie.  
  
 Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.  
  
#### <a name="to-create-a-lambert-shader"></a>Aby utworzyć modułu cieniującego Lamberta  
  
1.  Tworzenie modułu cieniującego DGSL chcesz pracować. Aby uzyskać informacje dotyczące sposobu dodawania modułu cieniującego DGSL do projektu, zobacz sekcję pierwsze kroki w [Shader Designer](../designers/shader-designer.md).  
  
2.  Odłącz **koloru punktu** węzła z **ostateczny kolor** węzła. Wybierz **RGB** terminali z **koloru punktu** węzła, a następnie wybierz **Przerwij linki**. Pozostaw **alfa** terminalu połączone.  
  
3.  Dodaj **Lamberta** węzła do wykresu. W **przybornika**w obszarze **narzędzie**, wybierz opcję **Lamberta** i przenieś go do powierzchni projektowej. Węzeł Lamberta oblicza udział łączny kolor rozpraszania piksela na podstawie parametrów otoczenia i rozpraszania oświetlenia.  
  
4.  Połącz **koloru punktu** węzeł **Lamberta** węzła. W **wybierz** tryb, Przenieś **RGB** terminali z **koloru punktu** węzeł, aby **kolor rozpraszania** terminali z **Lamberta**  węzła. To połączenie zawiera węzeł Lamberta kolorem rozpraszania interpolowane piksela.  
  
5.  Połącz się ostateczny kolor z wartości obliczanej koloru. Przenieś **dane wyjściowe** terminali z **Lamberta** węzeł **RGB** terminali z **ostateczny kolor** węzła.  
  
 Poniższej ilustracji ukończone programu do cieniowania programu graph i wersję zapoznawczą programu do cieniowania, zastosowano do modelu czajniczek.  
  
> [!NOTE]
>  Aby lepiej zaprezentować efekt programu cieniującego na tej ilustracji, została określona za pomocą koloru pomarańczowego **MaterialDiffuse** parametr programu do cieniowania. Gry lub aplikacji można Użyj tego parametru, aby podać wartość koloru unikatowy dla każdego obiektu. Informacje o parametrach materiału sekcja Podgląd cieniowania w [Shader Designer](../designers/shader-designer.md).  
  
 ![Wykres modułu cieniującego i wersją zapoznawczą jego wpływu. ](../designers/media/digit-lambert-effect-graph.png "Cyfry Lamberta — efekt Graph")  
  
 Niektórych kształtów udostępniać lepsze wersje zapoznawcze niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat programów do cieniowania w projektancie programu do cieniowania w wersji zapoznawczej, zobacz sekcję Podgląd cieniowania w [Shader Designer](../designers/shader-designer.md).  
  
 Poniższa ilustracja przedstawia programu do cieniowania, który jest opisany w tym dokumencie zastosowano do modelu 3-D.  
  
 ![Zastosowano do modelu oświetlenia Lamberta. ](../designers/media/digit-lambert-effect-result.png "Cyfry Lamberta — efekt — wynik")  
  
 Aby uzyskać więcej informacji dotyczących sposobu stosowania programu do cieniowania do modelu 3-D, zobacz [porady: stosowanie cieniowania do modelu 3-D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: stosowanie cieniowania do modelu 3-D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Porady: eksport cieniowania](../designers/how-to-export-a-shader.md)   
 [Porady: Tworzenie podstawowego modułu cieniowanie Phong](../designers/how-to-create-a-basic-phong-shader.md)   
 [Projektant programu do cieniowania](../designers/shader-designer.md)   
 [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)



