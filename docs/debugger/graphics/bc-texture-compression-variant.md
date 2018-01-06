---
title: Wariant kompresji tekstury BC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d0f5305-585b-4b01-bc9a-7a32d6e991da
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 13b97c4d9e90adf8b621100d6d2a68d11570e71d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bc-texture-compression-variant"></a>Wariant kompresji tekstury BC
Umożliwia blokowanie kompresji tekstury, które mają format pikseli, który jest odmianą B8G8R8X8, B8G8R8A8 lub R8G8B8A8.  
  
## <a name="interpretation"></a>Interpretacja  
 Opartej na blokach kompresji, takich jak BC1, BC2, i BC3 zajmować znacznie mniej pamięci niż nieskompresowane formatów obrazów i w związku z tym zużywać znacznie mniej przepustowości pamięci. W porównaniu do nieskompresowanych formatu, który używa 32 bity na piksel BC1 (wcześniej znane jako DXT1) pozwala kompresji 8:1 i 4:1 osiąga BC3 (wcześniej znane jako DXT5). Różnica między BC1 i BC3 jest BC1 nie obsługuje kanał alfa BC3 obsługuje skompresowane bloku kanału alfa. Pomimo stosunek wysoki stopień kompresji jest tylko drobne obniżenie jakości obrazu dla typowych tekstury. Jednak zablokować kompresji niektóre rodzaje tekstury — na przykład kolorów te, które znacząco zmienność mały obszar — może mieć wyniki nie do przyjęcia.  
  
 Jeśli Twoje tekstury są odpowiednie do opartej na blokach kompresji i nie wymagają doskonała koloru, należy wziąć pod uwagę przy użyciu formatu skompresowane bloku, aby zmniejszyć użycie pamięci i zużywać mniej przepustowości.  
  
## <a name="remarks"></a>Uwagi  
 Kompresuj tekstury formacie kompresji opartej na blokach przy każdym wywołaniu do `ID3DDevice::CreateTexture2D` tworzącą tekstury źródła. W szczególności tekstury są kompresowane, gdy:  
  
-   `D3D11_TEXTURE2D_DESC` Przekazano obiekt `pDesc` opisuje niezmiennych zasobów programu do cieniowania; będący:  
  
    -   Element członkowski BindFlags ma tylko D3D11_BIND_SHADER_RESOURCE flagę.  
  
    -   Użycie elementu członkowskiego ustawiono D3D11_USAGE_DEFAULT lub D3D11_USAGE_IMMUTABLE.  
  
    -   Element członkowski CPUAccessFlags jest równa 0 (nie dostępu do Procesora).  
  
    -   Element członkowski SamplerDesc ma jego Count — członek ustawioną wartość 1 (nie próbkowanie Wygładzanie (MSAA)).  
  
-   Początkowe dane są dostarczane do wywołania `CreateTexture2D`.  
  
 Poniżej przedstawiono formatów obsługiwanych źródłowych i ich formatów skompresowane bloku.  
  
|Oryginalnym formacie (od)|Format skompresowanych (do)|  
|------------------------------|------------------------------|  
|`DXGI_FORMAT_B8G8R8X8_UNORM`|BC1 (dawniej DXT1)|  
|`DXGI_FORMAT_B8G8R8X8_UNORM_SRGB`|BC1|  
|`DXGI_FORMAT_B8G8R8X8_TYPELESS`|BC1|  
|`DXGI_FORMAT_B8G8R8A8_UNORM`|BC3 (dawniej DXT5)|  
|`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB`|BC3|  
|`DXGI_FORMAT_B8G8R8A8_TYPELESS`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_UNORM`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_UNORM_SRGB`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_TYPELESS`|BC3|  
  
 Jeśli Twoje tekstury ma format, którego nie ma na liście, tekstury nie jest modyfikowany.  
  
## <a name="restrictions-and-limitations"></a>Ograniczenia i ograniczenia  
 Czasami tekstury, które zostały utworzone z odmianą obrazów w formacie B8G8R8A8 lub R8G8B8A8 faktycznie nie używaj kanału alfa, ale nie istnieje sposób wariantu wiedzieć, czy jest używany lub nie. Aby zapewnić poprawność w przypadku, gdy jest używany kanał alfa, wariant zawsze koduje te formaty w mniej wydajne format BC3. Pomaga lepiej zrozumieć potencjalnej wydajności renderowanie aplikacji z wariantu przy użyciu odmianą B8G8R8X8 format obrazu, jeśli nie używasz kanału alfa tak, aby wariant można użyć bardziej wydajne formatu BC1 analiza ramek grafiki.  
  
## <a name="example"></a>Przykład  
 Ten wariant bloku kompresuje tekstury w czasie wykonywania przed wywołaniem do `CreateTexture2D`. Odradza się tej metody dla kodu produkcyjnego ponieważ nieskompresowanych tekstury zużywać więcej miejsca na dysku i dodatkowego kroku może znacznie zwiększyć czas ładowania w aplikacji, ponieważ opartej na blokach kompresji wymaga znaczących zasoby obliczeniowe do kodowania. Zamiast tego zaleca się skompresować tekstury w trybie offline za pomocą edytora obrazów lub procesora obrazu, który jest częścią planowaną kompilacji. Te metody zmniejszyć wymagania dotyczące miejsca na dysku, aby wyeliminować środowiska wykonawczego nakładów pracy w aplikacji i zapewniają więcej czasu przetwarzania, dzięki czemu można zachować najlepszą jakość obrazu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wariant wymiarów tekstury połowie/kwartału](half-quarter-texture-dimensions-variant.md)