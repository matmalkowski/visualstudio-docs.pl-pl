---
title: Praca z zasobami 3D do gier i aplikacji
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cd99cad3b63df1cf7ab3bcecb347df53f7408832
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="work-with-3d-assets-for-games-and-apps"></a>Korzystanie z zasobów 3D do gier i aplikacji

Ten dokument zawiera opis narzędzi Visual Studio, które służy do tworzenia lub modyfikowania modeli 3D, tekstury i programów do cieniowania, na podstawie DirectX gier i aplikacji.

## <a name="directx-app-development-in-visual-studio"></a>Tworzenie aplikacji DirectX w programie Visual Studio
 Aplikacja DirectX zwykle łączy logiki programowania, interfejsu API programu DirectX i programy wysoki poziom cieniowania języka (HLSL), wraz z audio i 3D visual zasoby do prezentowania rozbudowanych, interakcyjnych multimedialnym środowisko. Visual Studio zawiera narzędzia, których można użyć do pracy z obrazów i tekstury 3D modeli i programów do cieniowania bez opuszczania IDE, aby użyć innego narzędzia. Narzędzia Visual Studio są szczególnie nadaje się do tworzenia *symbolu zastępczego* zasoby, które służy do testowania kodu lub tworzenie prototypów przed Komisji zasoby gotowe do produkcji i sprawdzanie i modyfikowanie gotowe do produkcji zasoby podczas debugowania aplikacji.

 Poniżej przedstawiono więcej informacji na temat typów zasobów, które można pracować w programie Visual Studio.

### <a name="images-and-textures"></a>Obrazy i tekstury
 Obrazy i tekstury umożliwiają kolor visual szczegółowo gier i aplikacji. W grafiki 3D tekstury są dostępne w różnych formatach, typy i mają geometrię do obsługi różnych celów. Na przykład mapy normalnej zapewniają wektorów powierzchni każdego piksela dla bardziej szczegółowe oświetlenia modeli 3D, a mapy modułu zapewniają tekstury we wszystkich kierunkach do celów, takich jak niebo pakującej, odbić i mapowanie kulistego tekstury. Tekstury zapewniają MCI mapy do obsługi wydajne renderowanie na różnych poziomach szczegółów i może obsługiwać różne kanałów i kolor uporządkowania. Tekstury mogą być przechowywane w różnych formatach skompresowany, które zajmują mniej dedykowanego pamięci grafiki i wydajniej pomocy GPU dostępu tekstury.

 Edytor obrazów programu Visual Studio umożliwia pracę z obrazami i tekstury w wielu typowych typy i formaty.

### <a name="3d-models"></a>Modele 3D
 Modele 3D Tworzenie miejsca i kształtu w gier i aplikacji. Minimalny, modeli kodowania pozycja punkty w przestrzeni 3D — które są nazywane *wierzchołków*— wraz z indeksowanie danych, aby zdefiniować linie lub trójkąty reprezentujących kształtu modelu. Dodatkowe dane mogą być skojarzone z tymi wierzchołków — na przykład kolor informacje, wektory normalne lub atrybuty specyficzne dla aplikacji. Każdy model można również zdefiniować atrybuty obiektu całej — na przykład, które program do cieniowania jest używana do obliczania wygląd obiektu powierzchni, lub tekstury, które są stosowane do niego.

 Można użyć edytora modelu programu Visual Studio do pracy z modeli 3D w wielu typowych formatach.

### <a name="shaders"></a>Programów do cieniowania
 Programów do cieniowania są programy małe, specyficznego dla domeny, które działają w jednostce przetwarzania graficznych (GPU). Programów do cieniowania ustalić sposób 3D modeli na ekranie przekształceniem kształtów i jak jest pokolorowane każdego piksela tych kształtów. Tworzenie programu do cieniowania i zastosowaniu go do obiektu w aplikacji lub gry, można przypisać obiektu unikatowego wyglądu.

 Projektanta programu Visual Studio programu do cieniowania, która jest narzędzie do projektowania programu do cieniowania oparte na wykresie, służy do tworzenia niestandardowych efektów wizualnych bez wiedzy o programowaniu HLSL.

> [!NOTE]
> Aby uzyskać więcej informacji dotyczących sposobu uruchamiania programu DirectX programowania, zobacz [DirectX](http://go.microsoft.com/fwlink/p/?LinkId=224633). Aby uzyskać więcej informacji o tym, jak można debugować aplikacji DirectX, zobacz [diagnostyki grafiki (debugowanie grafiki DirectX)](../debugger/visual-studio-graphics-diagnostics.md).

## <a name="directx-version-compatibility"></a>Zgodność wersji programu DirectX
 Visual Studio używa programu DirectX do renderowania zasobów 2W i 3W. Można wybrać programu DirectX 11 renderowania lub renderowania oprogramowania Windows Advanced rasteryzacji platformy (WARP). Moduł renderowania programu DirectX 11 Umożliwia renderowanie wysokiej wydajności, przyspieszane sprzętowo programu DirectX 11 i DirectX 10 GPU. Moduł renderowania WARP pomaga, upewnij się, że zasobów pracy z szeroką gamę komputerów — dotyczy to również komputery, które nie mają grafiki nowoczesne urządzenia i komputery, które zostały zintegrowane sprzętu grafiki. Aby uzyskać więcej informacji na temat WARP, zobacz [przewodnik Windows Advanced rasteryzacji platformy (WARP)](http://go.microsoft.com/fwlink/p/?LinkId=224634).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Praca z obrazami i teksturami](../designers/working-with-textures-and-images.md)|Opisuje sposób pracy z obrazami i tekstury za pomocą programu Visual Studio.|
|[Praca z modelami 3D](../designers/working-with-3-d-models.md)|Opisuje sposób pracy z modeli 3D za pomocą programu Visual Studio.|
|[Praca z cieniowaniem](../designers/working-with-shaders.md)|Informacje dotyczące używania projektanta programu do cieniowania programu Visual Studio do tworzenia i modyfikowania efekty niestandardowego programu do cieniowania.|
|[Korzystanie z zasobów 3D w aplikacji lub gry](../designers/using-3-d-assets-in-your-game-or-app.md)|W tym artykule opisano sposób użycia zasobów, które utworzono za pomocą edytora obrazów, edytorze modeli lub projektanta programu do cieniowania w aplikacji lub gry.|