---
title: Wariant generowania mapy MCI | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b4b3583-0b01-4f5d-aacb-3f96d19111d9
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f6b7773562ed7b09ca00f7fc471b7ee2924c0181
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mip-map-generation-variant"></a>Wariant generowania mapy MCI
Umożliwia MCI map na tekstury, które nie są renderowane elementów docelowych.  
  
## <a name="interpretation"></a>Interpretacja  
 Mapy MCI głównie są używane do wyeliminować artefakty aliasów w tekstury w obszarze minimalizację przez wstępnie obliczanie mniejsze wersje tekstury. Chociaż te dodatkowe tekstury używa pamięci procesora GPU — około 33% więcej niż oryginalny tekstury — są one również bardziej efektywne więcej ich powierzchni mieści się w pamięci podręcznej procesora GPU tekstury, ponieważ jego zawartość osiągnięcia lepszego wykorzystania.  
  
 3-w tle zalecamy MCI mapy podczas mało pamięci przechowywać dodatkowe tekstury, ponieważ mogą znacznie zwiększyć jakość obrazu i wydajność renderowania.  
  
 Ten wariant zawiera bardziej znaczących wydajne, wskazuje, bez włączania MCI map i tym samym nie uzyskuje się maksymalnie z pamięci podręcznej tekstury używasz tekstury.  
  
## <a name="remarks"></a>Uwagi  
 Wymusza przy każdym wywołaniu do generowania mapy MCI `ID3D11Device::CreateTexture2D` tworzącą tekstury źródła. W szczególności wymusza generowania mapy MCI podczas przekazano obiekt D3D11_TEXTUR2D_DESC `pDesc` opisuje niezmiennych zasobów programu do cieniowania; będący:  
  
-   Element członkowski BindFlags ma tylko D3D11_BIND_SHADER_RESOURCE flagę.  
  
-   Użycie elementu członkowskiego ustawiono D3D11_USAGE_DEFUALT lub D3D11_USAGE_IMMUTABLE.  
  
-   Element członkowski CPUAccessFlags jest równa 0 (nie dostępu do Procesora).  
  
-   Element członkowski SampleDesc ma jego Count — członek ustawioną wartość 1 (nie próbkowanie Wygładzanie (MSAA)).  
  
-   Element członkowski MipLevels jest ustawiona na 1 (nie istniejących MCI mapowanie).  
  
 Gdy początkowe dane są dostarczane przez aplikację, format tekstury musi obsługiwać generowania automatycznego mapy MCI — zgodnie z ustaleniami D3D11_FORMAT_SUPPORT_MIP_AUTOGEN — chyba, że format jest BC1, BC2 lub BC3; w przeciwnym razie wartość tekstury nie jest modyfikowany, a nie mapy MCI są generowane, gdy początkowe dane są dostarczane.  
  
 Automatycznie wygenerowano MCI mapy tekstury, wywołań `ID3D11Device::CreateShaderResourceView` są modyfikowane podczas odtwarzania na łańcuchu MCI podczas próbkowania tekstury.  
  
## <a name="example"></a>Przykład  
 **Generowania mapy MCI** wariant można odtworzyć za pomocą kodu w następujący sposób:  
  
```  
D3D11_TEXTURE2D_DESC texture_description;  
  
// ...  
  
texture_description.MipLevels = 0; // generate a full mipchain  
  
std::vector<D3D11_SUBRESOURCE_DATA> initial_data(num_mips);  
  
for (auto&& mip_level : initial_data)  
{  
    // fill mip_level with the application-supplied initial data  
}  
  
d3d_device->CreateTexture2D(&texture_description, initial_data.data(), &texture)  
```  
  
 Aby utworzyć tekstury, które ma pełny łańcuch MCI, ustaw `D3D11_TEXTURE2D_DESC::MipLevels` na 0. Liczba poziomów mipmapy pełny łańcuch MCI jest: floor(log2(n) + 1), gdzie n to największa wymiarów tekstury.  
  
 Należy pamiętać, że po udostępnieniu początkowej danych do `CreateTexture2D`, należy podać obiektu D3D11_SUBRESOURCE_DATA w ramach poszczególnych poziomów mipmapy.  
  
> [!NOTE]
>  Jeśli chcesz podać własne MCI poziomu zawartość zamiast generować je automatycznie, należy utworzyć Twoje tekstury za pomocą obrazu edytora obsługującego mapowane MCI tekstury i następnie załaduj plik i przekazać poziomów mipmapy do `CreateTexture2D`.  
  
## <a name="see-also"></a>Zobacz też  
 [Wariant wymiarów tekstury połowie/kwartału](half-quarter-texture-dimensions-variant.md)