---
title: 'Porady: tworzenie podstawowego modułu cieniującego Lamberta'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11e8c592bb91fc516ad6a5379330201198c65c14
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Porady: tworzenie podstawowego modułu cieniującego Lamberta

W tym artykule przedstawiono sposób umożliwiają utworzenie cieniowania oświetlenia, implementujący klasycznego modelu oświetlenia Lambert Designer programu do cieniowania i języka programu do cieniowania wykres skierowane (DGSL).

## <a name="the-lambert-lighting-model"></a>Model oświetlenia Lambert

Model oświetlenia Lambert zawiera oświetlenia otoczenia i kierunkową do obiektów cienia w scenę 3D. Składniki otoczenia zapewniają na podstawowym poziomie oświetlenia w scenę 3D. Składniki kierunkową udostępniają dodatkowe oświetlenia od kierunkowej źródła światła (najbardziej oddalonych). Oświetlenia otoczenia ma wpływ na wszystkie powierzchnie sceny jednakowo, niezależnie od ich orientacji. Dla danej warstwy jest to produkt koloru otoczenia powierzchni i kolor oraz zwiększeniem oświetlenie sceny. Kierunkową oświetlenia ma wpływ na co powierzchni sceny inaczej, oparte na orientację powierzchni względem kierunku źródła światła. Jest produktem kolor rozpraszania i orientację powierzchnią i kolor, intensywność i kierunek źródła światła. Powierzchnie stają przed bezpośrednio do źródła światła odbierania maksymalny wkład uprawnia do powierzchnie stają przed bezpośrednio optymalizacji nie udziału. Zgodnie z modelem oświetlenia Lambert otoczenia składnika jeden lub więcej składników kierunkową połączone i określić udział całkowita kolor rozpraszania dla każdego punktu w obiekcie.

Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.

1.  Utwórz DGSL programu do cieniowania do pracy z. Aby uzyskać informacje o sposobie dodawania cieniowania DGSL do projektu, w sekcji wprowadzenie w [Designer programu do cieniowania](../designers/shader-designer.md).

2.  Odłącz **kolor punktu** węzła z **ostateczny kolor** węzła. Wybierz **RGB** terminali z **kolor punktu** węzeł, a następnie wybierz pozycję **przerwanie łączy**. Pozostaw **alfa** terminal połączony.

3.  Dodaj **Lambert** węzła do wykresu. W **przybornika**w obszarze **narzędzie**, wybierz pozycję **Lambert** i przenieść ją na powierzchnię projektu. Węzeł lambert oblicza udział całkowita kolor rozpraszania piksela na podstawie parametrów otoczenia i rozpraszania oświetlenia.

4.  Połącz **kolor punktu** węzeł **Lambert** węzła. W **wybierz** tryb, Przenieś **RGB** terminali z **kolor punktu** węzeł **rozproszone kolor** terminali z **Lambert**  węzła. To połączenie zawiera węzeł lambert kolorem rozpraszania interpolowane piksela.

5.  Wartość obliczana koloru nawiązać połączenia z ostateczny kolor. Przenieś **dane wyjściowe** terminali z **Lambert** węzeł **RGB** terminali z **ostateczny kolor** węzła.

 Na poniższej ilustracji przedstawiono ukończone programu do cieniowania wykres i Podgląd programu do cieniowania zastosowano do modelu teapot.

> [!NOTE]
> Aby lepiej zaprezentować efekt cieniowania na tej ilustracji, kolor pomarańczowy został określony przy użyciu **MaterialDiffuse** parametr programu do cieniowania. Gry lub aplikacji można użyć tego parametru umożliwiają określanie wartości koloru unikatowy dla każdego obiektu. Informacje o istotnych parametrach, zobacz sekcję Podgląd programów do cieniowania w [Designer programu do cieniowania](../designers/shader-designer.md).

 ![Wykres programu do cieniowania i podgląd jego skutków. ] (../designers/media/digit-lambert-effect-graph.png "Cyfrę Lambert efekt wykresu")

 Niektórych kształtów udostępniać lepsze podglądy niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat wersji preview programów do cieniowania w projektancie programu do cieniowania, zobacz sekcję Podgląd programów do cieniowania w [Designer programu do cieniowania](../designers/shader-designer.md).

 Na poniższej ilustracji przedstawiono programu do cieniowania, które jest opisane w tym dokumencie zastosowano do modelu 3D.

 ![Oświetlenie Lambert zastosowane do modelu. ] (../designers/media/digit-lambert-effect-result.png "Cyfrę Lambert efekt wynik")

 Aby uzyskać więcej informacji dotyczących sposobu stosowania programu do cieniowania do modelu 3D, zobacz [porady: dotyczą programu do cieniowania modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Zobacz także

- [Porady: zastosowanie programu do cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Instrukcje: eksport cieniowania](../designers/how-to-export-a-shader.md)
- [Instrukcje: tworzenie podstawowego modułu cieniowanie Phong](../designers/how-to-create-a-basic-phong-shader.md)
- [Projektant cieniowania](../designers/shader-designer.md)
- [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)