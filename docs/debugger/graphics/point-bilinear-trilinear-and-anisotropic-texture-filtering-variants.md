---
title: Punkt, dwuliniowa Trilinear i anizotropowej tekstury filtrowania wariantów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 811b588ffd4e1cb8ac8ffece711d52cb2638d54c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>Punkt, dwuliniowa Trilinear i anizotropowej tekstury filtrowania wariantów
Zastępuje tryb filtrowania na próbników odpowiednie tekstury.  
  
## <a name="interpretation"></a>Interpretacja  
 Różne metody pobierania próbek tekstury ma kosztów różnych wydajności i jakości obrazu. W kolejności zwiększenie kosztów — i zwiększyć jakość — tryby filtru to:  
  
1.  Polecenie filtrowania (jakość najniższych, najgorszych visual)  
  
2.  Filtrowanie dwuliniowa  
  
3.  Filtrowanie trilinear  
  
4.  Anizotropowej filtrowania (jakość najdroższych, najlepiej visual)  
  
 Jeśli koszt wydajności każdego wariantu jest znacząca lub zwiększa się wraz z bardziej intensywnie tryby filtrowania, należy porównać koszt przed jego zwiększona jakość. Na podstawie oceny, może akceptować koszty dodatkowe zwiększyć jakość lub może zaakceptować zmniejszyć visual jakości do osiągnięcia wyższej szybkość klatek lub odzyskiwaniu wydajność, których można użyć w inny sposób.  
  
 Jeśli okaże się, że koszt wydajności jest niewielka lub stałą niezależnie od tego, tryb filtrowania — na przykład, jeśli procesora GPU, który docelowych zawiera wiele przepustowość programu do cieniowania przepływności i pamięci — należy rozważyć użycie filtrowania anizotropowej do osiągnięcia najlepsze obrazu jakość w aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 Te wariantów zastąpienie stanów przykłady na wywołania `ID3D11DeviceContext::PSSetSamplers` w tryb filtru próbnika dostarczony do aplikacji czyli jeden z nich:  
  
-   `D3D11_FILTER_MIN_MAG_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`  
  
-   `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`  
  
-   `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`  
  
-   `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_MAG_MIP_LINEAR`  
  
-   `D3D11_FILTER_ANISOTROPIC`  
  
 W **filtrowania tekstury punktu** variant, tryb filtru dostarczony do aplikacji jest zastępowany `D3D11_FILTER_MIN_MAG_MIP_POINT`; na liście **dwuliniowa filtrowania tekstury** variant, zostaje zastąpiony `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`; i w **Trilinear filtrowania tekstury** variant, zostaje zastąpiony `D3D11_FILTER_MIN_MAG_MIP_LINEAR`.  
  
 W **anizotropowych filtrowania tekstury** variant, tryb filtru dostarczony do aplikacji jest zastępowany `D3D11_FILTER_ANISOTROPIC`, a Anisotropy maksymalna jest ustawiona na 16.  
  
## <a name="restrictions-and-limitations"></a>Ograniczenia i ograniczenia  
 W Direct3D poziom funkcji 9.1 określa maksymalny anisotropy x 2. Ponieważ **anizotropowej filtrowania tekstury** variant próbuje użyć wyłącznie 16 x anisotropy, odtwarzania kończy się niepowodzeniem, gdy analiza ramek jest uruchamiana na urządzeniu 9.1 funkcji na poziomie. Nowoczesne urządzenia, których dotyczy to ograniczenie obejmują tablety Surface RT i Windows 2 powierzchni opartego na architekturze ARM. Starszych procesorów graficznych, które może nadal znajdować się w niektórych komputerów może mieć wpływ, ale są powszechnie uznawane za przestarzałe i są coraz bardziej rzadko.  
  
## <a name="example"></a>Przykład  
 **Filtrowania tekstury punktu** wariant można odtworzyć za pomocą kodu w następujący sposób:  
  
```  
D3D11_SAMPLER_DESC sampler_description;  
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Przykład  
 **Dwuliniowa filtrowania tekstury** wariant można odtworzyć za pomocą kodu w następujący sposób:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Przykład  
 **Trilinear filtrowania tekstury** wariant można odtworzyć za pomocą kodu w następujący sposób:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Przykład  
 **Anizotropowej filtrowania tekstury** wariant można odtworzyć za pomocą kodu w następujący sposób:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;  
sampler_description.MaxAnisotropy = 16;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```