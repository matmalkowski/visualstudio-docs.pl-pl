---
title: 'Porady: tworzenie cieniowania podstawowe Lambert | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-designers
ms.topic: conceptual
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5525ef575c4c986b8da2e77b3c0265cd681b5652
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Porady: tworzenie podstawowego modułu cieniującego Lamberta
Ten dokument przedstawia sposób umożliwiają utworzenie cieniowania oświetlenia, implementujący klasycznego modelu oświetlenia Lambert Designer programu do cieniowania i języka programu do cieniowania wykres skierowane (DGSL).  
  
 W tym dokumencie przedstawiono następujące działania:  
  
-   Dodawanie węzłów do programu do cieniowania wykresu.  
  
-   Rozłączanie węzłów  
  
-   Łączenie węzłów  
  
## <a name="the-lambert-lighting-model"></a>Model oświetlenia Lambert  
 Model oświetlenia Lambert zawiera oświetlenia otoczenia i kierunkową do obiektów cienia w 3-sceny. Składniki otoczenia zapewniają na podstawowym poziomie oświetlenia w 3-sceny. Składniki kierunkową udostępniają dodatkowe oświetlenia od kierunkowej źródła światła (najbardziej oddalonych). Oświetlenia otoczenia ma wpływ na wszystkie powierzchnie sceny jednakowo, niezależnie od ich orientacji. Dla danej warstwy jest to produkt koloru otoczenia powierzchni i kolor oraz zwiększeniem oświetlenie sceny. Kierunkową oświetlenia ma wpływ na co powierzchni sceny inaczej, oparte na orientację powierzchni względem kierunku źródła światła. Jest produktem kolor rozpraszania i orientację powierzchnią i kolor, intensywność i kierunek źródła światła. Powierzchnie stają przed bezpośrednio do źródła światła odbierania maksymalny wkład uprawnia do powierzchnie stają przed bezpośrednio optymalizacji nie udziału. Zgodnie z modelem oświetlenia Lambert otoczenia składnika jeden lub więcej składników kierunkową połączone i określić udział całkowita kolor rozpraszania dla każdego punktu w obiekcie.  
  
 Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.  
  
#### <a name="to-create-a-lambert-shader"></a>Aby utworzyć cieniowania Lambert  
  
1.  Utwórz DGSL programu do cieniowania do pracy z. Aby uzyskać informacje o sposobie dodawania cieniowania DGSL do projektu, w sekcji wprowadzenie w [Designer programu do cieniowania](../designers/shader-designer.md).  
  
2.  Odłącz **kolor punktu** węzła z **ostateczny kolor** węzła. Wybierz **RGB** terminali z **kolor punktu** węzeł, a następnie wybierz pozycję **przerwanie łączy**. Pozostaw **alfa** terminal połączony.  
  
3.  Dodaj **Lambert** węzła do wykresu. W **przybornika**w obszarze **narzędzie**, wybierz pozycję **Lambert** i przenieść ją na powierzchnię projektu. Węzeł lambert oblicza udział całkowita kolor rozpraszania piksela na podstawie parametrów otoczenia i rozpraszania oświetlenia.  
  
4.  Połącz **kolor punktu** węzeł **Lambert** węzła. W **wybierz** tryb, Przenieś **RGB** terminali z **kolor punktu** węzeł **rozproszone kolor** terminali z **Lambert**  węzła. To połączenie zawiera węzeł lambert kolorem rozpraszania interpolowane piksela.  
  
5.  Wartość obliczana koloru nawiązać połączenia z ostateczny kolor. Przenieś **dane wyjściowe** terminali z **Lambert** węzeł **RGB** terminali z **ostateczny kolor** węzła.  
  
 Na poniższej ilustracji przedstawiono ukończone programu do cieniowania wykres i Podgląd programu do cieniowania zastosowano do modelu teapot.  
  
> [!NOTE]
>  Aby lepiej zaprezentować efekt cieniowania na tej ilustracji, kolor pomarańczowy został określony przy użyciu **MaterialDiffuse** parametr programu do cieniowania. Gry lub aplikacji można użyć tego parametru umożliwiają określanie wartości koloru unikatowy dla każdego obiektu. Informacje o istotnych parametrach, zobacz sekcję Podgląd programów do cieniowania w [Designer programu do cieniowania](../designers/shader-designer.md).  
  
 ![Wykres programu do cieniowania i podgląd jego skutków. ] (../designers/media/digit-lambert-effect-graph.png "Cyfrę Lambert efekt wykresu")  
  
 Niektórych kształtów udostępniać lepsze podglądy niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat wersji preview programów do cieniowania w projektancie programu do cieniowania, zobacz sekcję Podgląd programów do cieniowania w [Designer programu do cieniowania](../designers/shader-designer.md).  
  
 Na poniższej ilustracji przedstawiono programu do cieniowania, które jest opisane w tym dokumencie dotyczą 3-w modelu.  
  
 ![Oświetlenie Lambert zastosowane do modelu. ] (../designers/media/digit-lambert-effect-result.png "Cyfrę Lambert efekt wynik")  
  
 Aby uzyskać więcej informacji dotyczących sposobu stosowania programu do cieniowania 3-w modelu, zobacz [porady: dotyczą programu do cieniowania 3-w modelu](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: dotyczą programu do cieniowania 3-w modelu](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Porady: eksportowanie programu do cieniowania](../designers/how-to-export-a-shader.md)   
 [Porady: Tworzenie podstawowego cieniowania Phong](../designers/how-to-create-a-basic-phong-shader.md)   
 [Projektant programu do cieniowania](../designers/shader-designer.md)   
 [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)