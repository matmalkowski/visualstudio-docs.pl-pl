---
title: Praca z 3-zasoby do gier i aplikacji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0c57284e21e1b276c6191109701f507c5a12f819
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="working-with-3-d-assets-for-games-and-apps"></a>Praca z obiektami 3-D do gier i aplikacji
W tym dokumencie opisano [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia, które służą do tworzenia lub modyfikowania 3-modeli, tekstury i programów do cieniowania, na podstawie DirectX gier i aplikacji.  
  
## <a name="directx-app-development-in-visual-studio"></a>Tworzenie aplikacji DirectX w programie Visual Studio  
 Aplikacja DirectX zwykle łączy logiki programowania, interfejsu API programu DirectX i programy wysoki poziom cieniowania języka (HLSL), wraz z audio i 3-visual zasoby do prezentowania rozbudowanych, interakcyjnych multimedialnym środowisko.[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zawiera narzędzia służące do pracy z obrazami i tekstury, 3-modele i programów do cieniowania bez opuszczania IDE, aby użyć innego narzędzia. Narzędzia Visual Studio są szczególnie nadaje się do tworzenia *symbolu zastępczego* zasoby, które służy do testowania kodu lub tworzenie prototypów przed Komisji zasoby gotowe do produkcji i sprawdzanie i modyfikowanie gotowe do produkcji zasoby podczas debugowania aplikacji.  
  
 Poniżej przedstawiono więcej informacji na temat typów zasobów, które można pracować w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### <a name="images-and-textures"></a>Obrazy i tekstury  
 Obrazy i tekstury umożliwiają kolor visual szczegółowo gier i aplikacji. W 3-grafiki tekstury są dostępne w różnych formatach, typy i mają geometrię do obsługi różnych celów. Na przykład mapy normalne zapewnienia bardziej szczegółowe oświetlenia 3-modeli wektorów powierzchni każdego piksela i mapy modułu zapewniają tekstury we wszystkich kierunkach do celów, takich jak niebo pakującej, odbić i mapowanie kulistego tekstury. Tekstury zapewniają MCI mapy do obsługi wydajne renderowanie na różnych poziomach szczegółów i może obsługiwać różne kanałów i kolor uporządkowania. Tekstury mogą być przechowywane w różnych formatach skompresowany, które zajmują mniej dedykowanego pamięci grafiki i wydajniej pomocy GPU dostępu tekstury.  
  
 Można użyć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] edytor obrazów do pracy z obrazami i tekstury w wielu typowych typy i formaty.  
  
### <a name="3-d-models"></a>modele 3-D  
 Modele 3-Tworzenie miejsca i kształtu w gier i aplikacji. Minimalny, modeli kodowania pozycja punkty przestrzeni 3-w — które są określane jako *wierzchołków*— wraz z indeksowanie danych, aby zdefiniować linie lub trójkąty reprezentujących kształtu modelu. Dodatkowe dane mogą być skojarzone z tymi wierzchołków — na przykład kolor informacje, wektory normalne lub atrybuty specyficzne dla aplikacji. Każdy model można również zdefiniować atrybuty obiektu całej — na przykład, które program do cieniowania jest używana do obliczania wygląd obiektu powierzchni, lub tekstury, które są stosowane do niego.  
  
 Można użyć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] edytorze modeli do pracy z 3-w modelach w wielu typowych formatach.  
  
### <a name="shaders"></a>Programów do cieniowania  
 Programów do cieniowania są programy małe, specyficznego dla domeny, które działają w jednostce przetwarzania graficznych (GPU). Modele 3-w jaki sposób określić programów do cieniowania na ekranie przekształceniem kształtów i jak jest pokolorowane każdego piksela tych kształtów. Tworzenie programu do cieniowania i zastosowaniu go do obiektu w aplikacji lub gry, można przypisać obiektu unikatowego wyglądu.  
  
 Można użyć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] programu do cieniowania Designer, który jest narzędzie do projektowania programu do cieniowania oparte na wykresie, aby utworzyć niestandardowe efekty wizualne bez wiedzy o HLSL programowania w języku.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji dotyczących sposobu uruchamiania programu DirectX programowania, zobacz [DirectX](http://go.microsoft.com/fwlink/p/?LinkId=224633). Aby uzyskać więcej informacji o tym, jak można debugować aplikacji DirectX, zobacz [diagnostyki grafiki (debugowanie grafiki DirectX)](../debugger/visual-studio-graphics-diagnostics.md).  
  
## <a name="directx-version-compatibility"></a>Zgodność wersji programu DirectX  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]używa programu DirectX do renderowania 2- i 3-zasobów. Można wybrać programu DirectX 11 renderowania lub renderowania oprogramowania Windows Advanced rasteryzacji platformy (WARP). Moduł renderowania programu DirectX 11 Umożliwia renderowanie wysokiej wydajności, przyspieszane sprzętowo programu DirectX 11 i DirectX 10 GPU. Moduł renderowania WARP pomaga, upewnij się, że zasobów pracy z szeroką gamę komputerów — dotyczy to również komputery, które nie mają grafiki nowoczesne urządzenia i komputery, które zostały zintegrowane sprzętu grafiki. Aby uzyskać więcej informacji na temat WARP, zobacz [przewodnik Windows Advanced rasteryzacji platformy (WARP)](http://go.microsoft.com/fwlink/p/?LinkId=224634).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Praca z tekstury i obrazów](../designers/working-with-textures-and-images.md)|Informacje dotyczące używania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do pracy z obrazami i tekstury.|  
|[Praca z modelami 3-w](../designers/working-with-3-d-models.md)|Informacje dotyczące używania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do pracy z 3-modeli.|  
|[Praca z programów do cieniowania](../designers/working-with-shaders.md)|Informacje dotyczące używania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] programu do cieniowania Designer do tworzenia i modyfikowania efekty niestandardowego programu do cieniowania.|  
|[Korzystanie z zasobów 3-w aplikacji lub gry](../designers/using-3-d-assets-in-your-game-or-app.md)|W tym artykule opisano sposób użycia zasobów, które utworzono za pomocą edytora obrazów, edytorze modeli lub projektanta programu do cieniowania w aplikacji lub gry.|