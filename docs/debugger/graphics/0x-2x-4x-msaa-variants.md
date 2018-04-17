---
title: 0 wariantów x-2 x-4 x MSAA | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09ec8c25a076fd9f74690b3be92715aa62b60f65
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="0x2x4x-msaa-variants"></a>0 x / 2 x / 4 x MSAA wariantów
Zastąpienia wielu przykładowa Wygładzanie (MSAA) ustawienia na wszystkich obiektów docelowych renderowania i łańcucha wymiany.  
  
## <a name="interpretation"></a>Interpretacja  
 Przykład wielu wygładzanie zwiększa jakości visual pobierania próbek w wielu lokalizacjach w każdego piksela; wyższy poziom MSAA zajmuje więcej przykładów i bez MSAA, tylko jeden próbka jest pobierana z centrum piksela. Włączanie MSAA w aplikacji zwykle ma niewielkie oprócz znaczącej koszt wydajności renderowania, ale w niektórych obciążeń lub na niektórych procesorach GPU, może być miał prawie bez wpływu.  
  
 Jeśli aplikacja ma już MSAA włączone, mniejszym wariantów MSAA wskazuje koszt względną wydajność, który wiąże się z MSAA istniejących, wyższego poziomu. W szczególności 0 x MSAA variant wskazuje względną wydajność aplikacji bez MSAA.  
  
 Jeśli aplikacja nie ma już MSAA włączone, 2 x MSAA i 4 wariantów x MSAA wskazuje koszt względną wydajność włączenie ich w aplikacji. Gdy koszt brakuje prawidłowo, należy rozważyć włączenie MSAA do poprawy jakości obrazu aplikacji.  
  
> [!NOTE]
>  Sprzęt może nie pełni obsługiwać MSAA we wszystkich formatach. Ograniczenie sprzętu, który nie pracuje wokół żadnego z tych wariantów wystąpienia, jej kolumny w tabeli podsumowania wydajności jest pusta i jest generowany komunikat o błędzie.  
  
## <a name="remarks"></a>Uwagi  
 Te wariantów Zastąp przykładowe jakość próbkowania i liczba argumentów w wywołań `ID3DDevice::CreateTexture2D` aby tworzenia obiektów docelowych renderowania. W szczególności parametry te zostaną zastąpione po:  
  
-   `D3D11_TEXTURE2D_DESC` Przekazano obiekt `pDesc` opis obiektu docelowego renderowania; który jest:  
  
    -   Element członkowski BindFlags ma flagę D3D11_BIND_TARGET albo Ustaw flagę D3D11_BIND_DEPTH_STENCIL.  
  
    -   Użycie elementu członkowskiego ustawiono D3D11_USAGE_DEFAULT.  
  
    -   Element członkowski CPUAccessFlags jest równa 0.  
  
    -   Element członkowski MipLevels jest ustawiona na 1.  
  
-   Urządzenie obsługuje liczność próbki żądanego (0, 2 lub 4) i jakość próbkowania (0) dla żądany format docelowy (D3D11_TEXTURE2D_DESC::Format członek), na podstawie renderowania `ID3D11Device::CheckMultisampleQualityLevels`.  
  
 Jeśli element członkowski D3D11_TEXTURE2D_DESC::BindFlags ma D3D_BIND_SHADER_RESOUCE lub D3D11_BIND_UNORDERED_ACCESS ustawionych flag, są tworzone dwie wersje tekstury; pierwszy ma te flagi wyczyszczone do użycia jako obiektu docelowego renderowania, a drugi to tekstury MSAA z systemem innym niż, który ma te flagi pozostanie bez zmian do działania jako bufor rozwiązanie dla pierwszej wersji. Jest to konieczne, ponieważ przy użyciu metody MSAA tekstury jako zasób programu do cieniowania lub nieuporządkowanego dostępu jest mało prawdopodobne identyfikator był prawidłowy, na przykład cieniowania, działające na nim może wygenerować niepoprawne wyniki, ponieważ mogą spodziewać tekstury nie MSAA. Jeśli variant został utworzony dodatkowej z systemem innym niż MSAA tekstury, następnie zawsze, gdy nie ustawiono z kontekstu urządzenia jest obiektu docelowego renderowania MSAA jego zawartość zostaną rozpoznane do tekstury nie MSAA. Podobnie, w przypadku gdy renderowania MSAA docelowy powinien zostać powiązany jako zasobów programu do cieniowania lub jest używana w widok nieuporządkowanego dostępu, tekstury rozwiązany z systemem innym niż MSAA jest powiązany zamiast tego.  
  
 Te wariantów również zastąpić ustawienia MSAA wszystkie łańcuchy wymiany utworzone za pomocą `IDXGIFactory::CreateSwapChain`, `IDXGIFactory2::CreateSwapChainForHwnd`, `IDXGIFactory2::CreateSwapChainForCoreWindow`, `IDXGIFactory2::CreateSwapChainForComposition`, i `ID3D11CreateDeviceAndSwapChain`.  
  
 Net tych zmian powoduje, że wszystkie renderowania odbywa się do obiektu docelowego renderowania MSAA, ale jeśli aplikacja korzysta z jednego z tych renderowania elementów docelowych lub buforów łańcucha wymiany jako widok zasobów programu do cieniowania lub widok nieuporządkowanego dostępu, a następnie dane z rozwiązany , z systemem innym niż MSAA kopię obiektu docelowego renderowania.  
  
## <a name="restrictions-and-limitations"></a>Ograniczenia i ograniczenia  
 W Direct3D11 tekstury MSAA są bardziej ograniczony z systemem innym niż MSAA tekstury. Na przykład nie można wywołać `ID3D11DeviceContext::UpdateSubresource` tekstury MSAA i wywoływania `ID3D11DeviceContext::CopySubresourceRegion` zakończy się niepowodzeniem, jeśli liczba próbek i jakość próbkowania zasobu źródłowego i docelowego zasobu nie są zgodne, które mogą wystąpić, gdy ten wariant zastępuje ustawienia MSAA jednego zasób, ale nie dla drugiego.  
  
 Podczas odtwarzania wykryje rodzaju konflikty, ułatwia optymalnego replikowanie zamierzone zachowanie, ale może nie być możliwe do jego wyniki są takie same. Nietypowe tej wpływa na wydajność tych wariantów w taki sposób, aby posiadałaby ich wpływ, ale jest możliwe — na przykład gdy sterowania przepływem programu do cieniowania pikseli jest określany przez dokładnej zawartości tekstury — ponieważ replikowanych tekstury może nie mieć identyczną zawartość.  
  
## <a name="example"></a>Przykład  
 Te wariantów można odtworzyć dla celów renderowania utworzone za pomocą `ID3D11Device::CreateTexture2D` przy użyciu kodu w następujący sposób:  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead  
target_description.SampleDesc.Quality = 0;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```  
  
## <a name="example"></a>Przykład  
 Lub łańcuchy wymiany utworzone przy użyciu IDXGISwapChain::CreateSwapChain lub D3D11CreateDeviceAndSwapChain przy użyciu kodu w następujący sposób:  
  
```  
DXGI_SWAP_CHAIN_DESC chain_description;  
chain_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead  
chain_description.SampleDesc.Quality = 0;  
  
// Call IDXGISwapChain::CreateSwapChain or D3D11CreateDeviceAndSwapChain, etc.  
```