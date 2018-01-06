---
title: Wariant formatu docelowego renderowania 16bpp | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 896ca20589e987f5a516e85c47d3f06a44a2550c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="16bpp-render-target-format-variant"></a>Wariant formatu docelowego renderowania 16bpp
Ustawia piksela formatu DXGI_FORMAT_B5G6R5_UNORM dla wszystkich obiektów docelowych renderowania i kopii buforów.  
  
## <a name="interpretation"></a>Interpretacja  
 Obiektu docelowego renderowania lub buforu zapasowego zwykle wykorzystuje format 32 bity na piksel (32 bity na piksel), takich jak B8G8R8A8_UNORM. formaty 32 bity na piksel może używać dużej ilości pamięci przepustowość. Ponieważ B5G6R5_UNORM format jest 16bpp formatu, który jest połowa 32 bity na piksel formatów, przy jej użyciu można zwolnić wykorzystania przepustowości pamięci, ale kosztem zmniejszenie koloru.  
  
 Jeśli ten wariant wyświetlane są bardziej wydajne dużych, prawdopodobnie oznacza to, że aplikacja zużywa zbyt dużej ilości pamięci przepustowość. Wzrost wydajności mogą występować w szczególnie przypadku, gdy PROFILOWANEGO ramki odczuwa znaczną ilość overdraw lub zawiera wiele przenikanie alfa.  
  
 Jeśli rodzaje sceny, które mają być renderowane przez aplikację nie wymagają odtwarzania o wysokiej wierności kolorów, nie wymagają, aby kanału alfa obiektu docelowego renderowania i często nie mogą zawierać gradientów smooth — które są podatne na pasma artefakty zmniejszenie kolor wierności — należy wziąć pod uwagę przy użyciu formatu docelowego renderowania 16bpp zmniejsza użycie przepustowości pamięci.  
  
 Jeśli sceny, które mają być renderowane w aplikacji wymagają odtwarzania kolorów o wysokiej wierności lub kanału alfa lub smooth gradienty są często używane, należy rozważyć inne strategie zmniejsza użycie przepustowości pamięci — na przykład zmniejszenie ilości overdraw lub przenikanie alfa zmniejszenie wymiary obiektu lub modyfikowanie zasobów tekstury korzystać z mniejszej przepustowości pamięci przez włączenie kompresji lub zmniejszenia ich wymiarów. W zwykły sposób należy wziąć pod uwagę obrazu jakości kompromis dostarczane za pomocą dowolnego z tych optymalizacji.  
  
 Jeśli aplikacja będzie korzystać z przełączanie do buforu zapasowego 16bpp, ale jest częścią Twojego łańcucha wymiany, należy wykonać dodatkowe czynności, ponieważ nie jest DXGI_FORMAT_B5G6R5_UNORM format obsługiwanych buforu zapasowego łańcucha wymiany utworzone za pomocą `D3D11CreateDeviceAndSwapChain` lub `IDXGIFactory::CreateSwapChain`. Zamiast tego należy utworzyć obiektu docelowego renderowania format B5G6R5_UNORM przy użyciu `CreateTexture2D` i renderowania w tym zamiast tego. Następnie przed wywołaniem obecnie na Twojej łańcucha wymiany, skopiuj obiektu docelowego renderowania na buforu zapasowego łańcucha wymiany w celu za pomocą rysowania quad pełnego ekranu z obiektu docelowego renderowania jako tekstury Twoje źródła. Jest to dodatkowy krok, który będzie korzystać z niektórych przepustowości pamięci, większość operacji renderowania zajmie mniej przepustowości ponieważ wpływają na obiektu docelowego renderowania 16bpp; Jeśli spowoduje to zapisanie większej przepustowości, nie jest używany przez skopiowanie obiektu docelowego renderowania buforu zapasowego łańcucha wymiany w celu, renderowanie wydajność się zwiększy.  
  
 Architektury procesora GPU, korzystających z techniki sąsiadującym renderowania widoczny korzystny wydajności przy użyciu formatu 16bpp obiektu, ponieważ większa część obiektu można zmieścić w pamięci podręcznej obiektu lokalnego każdego kafelka. Renderowanie sąsiadującym architektury czasami znajdują się w GPU aparaty telefoniczne przenośnych i komputerów typu tablet. rzadko pojawią się one poza tym niszowych.  
  
## <a name="remarks"></a>Uwagi  
 Format docelowy renderowania jest resetowany do DXGI_FORMAT_B5G6R5_UNORM przy każdym wywołaniu do `ID3D11Device::CreateTexture2D` tworzącą obiektu docelowego renderowania. W szczególności format jest zastąpione w przypadku obiektu D3D11_TEXTURE2D_DESC przekazano pDesc opisuje cel renderowania; Czyli:  
  
-   Element członkowski BindFlags ma flagę D3D11_BIND_REDNER_TARGET.  
  
-   Element członkowski BindFlags ma flagę D3D11_BIND_DEPTH_STENCIL wyczyszczone.  
  
-   Użycie elementu członkowskiego ustawiono D3D11_USAGE_DEFAULT.  
  
## <a name="restrictions-and-limitations"></a>Ograniczenia i ograniczenia  
 Ponieważ B5G6R5 format nie ma kanału alfa, alfa zawartości nie są zachowywane przez ten typ variant. Jeśli renderowanie aplikacji wymaga kanału alfa w docelowym renderowania, nie można przełączyć tylko na format B5G6R5.  
  
## <a name="example"></a>Przykład  
 **Format docelowy renderowania 16bpp** wariant można odtworzyć dla celów renderowania utworzone za pomocą `CreateTexture2D` przy użyciu kodu w następujący sposób:  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```