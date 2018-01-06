---
title: "Wariant wymiarów tekstury kwartału półrocza | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 282e9bbb-51aa-4cd0-8e5c-0901268c29e5
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 93431c8863e2b30fb98d00bec5112257e54496f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="halfquarter-texture-dimensions-variant"></a>Wariant wymiarów tekstury połowie/kwartału
Zmniejsza liczbę wymiarów tekstury tekstury, które nie są renderowane elementów docelowych.  
  
## <a name="interpretation"></a>Interpretacja  
 Mniejsze tekstury zajmuje mniej pamięci i w związku z tym zużywają mniej przepustowości pamięci i zmniejszyć nacisk na tekstury procesora GPU w pamięci podręcznej. Ich szczegóły mniejszym może jednak spowodować zmniejszenie obrazu, szczególnie w przypadku, gdy zostaną ściśle wyświetlanych w 3-sceny lub przeglądać w obszarze powiększenia.  
  
 Ten wariant zawiera bardziej wydajne duży, może on wskazywać, że aplikacji zużywa zbyt dużej ilości pamięci przepustowość i używa tekstury Niewydajne pamięci podręcznej. Można również określić, że Twoje tekstury zajmują więcej pamięci procesora GPU nie jest dostępny, co powoduje, że tekstury być stronicowana na pamięci systemowej.  
  
 Jeśli dana aplikacja zużywa zbyt dużej ilości pamięci przepustowość lub Niewydajne używa pamięci podręcznej tekstury, Rozważ zmniejszenie rozmiaru sieci tekstury, ale tylko wtedy, gdy należy rozważyć włączenie MCI mapy tekstury odpowiednie. Takich jak mniejsze tekstury, mapowane MCI tekstury zużywać mniej przepustowości pamięci — mimo że zajmują więcej pamięci GPU — i zwiększyć użycie pamięci podręcznej, ale nie zmniejszyć szczegółów tekstury. Firma Microsoft zaleca MCI mapy zawsze, gdy użycie pamięci nie powoduje tekstury być stronicowana na pamięci systemowej.  
  
 Jeśli Twoje tekstury zajmują więcej pamięci procesora GPU nie jest dostępna, należy wziąć pod uwagę zmniejszenie rozmiaru tekstury, ale tylko wtedy, gdy należy wziąć pod uwagę kompresowania odpowiednie tekstury. Podobnie jak mniejsze tekstury skompresowany tekstury zajmuje mniej pamięci i zmniejsza potrzebę do strony do pamięci, ale zmniejsza się ich wierności kolorów. Kompresja nie jest odpowiedni dla wszystkich tekstury, w zależności od ich zawartość — na przykład kolorów te, które znacząco zmienność mały obszar —, ale dla wielu tekstury kompresji można zachować lepszej ogólnej jakości obrazu niż zmniejszenie jego rozmiar.  
  
## <a name="remarks"></a>Uwagi  
 Wymiarów tekstury zostały zredukowane przy każdym wywołaniu do `ID3D11Device::CreateTexture2D` tworzącą tekstury źródła. W szczególności można ograniczyć wymiarów tekstury przekazano obiekt D3D11_TEXTURE2D_DESC `pDesc` tekstury, który jest używany w przypadku renderowania; opis:  
  
-   Element członkowski BindFlags ma tylko D3D11_BIND_SHADER_RESOURCE flagę.  
  
-   Element członkowski MiscFlags nie ma flagi D3D11_RESOURCE_MISC_TILE_POOL lub Ustaw flagę D3D11_RESOURCE_MISC_TILED (ułożenie sąsiadujące zasobów nie są rozmiaru).  
  
-   Format tekstury jest obsługiwany jako cel renderowania — zgodnie z ustaleniami D3D11_FORMAT_SUPPORT_RENDER_TARGET — co jest niezbędne do zmniejszania rozmiaru tekstury. BC1, BC2 i BC3 są również obsługiwane formaty, nawet jeśli nie są obsługiwane jako obiektów docelowych renderowania.  
  
 Jeśli początkowe dane są dostarczane przez aplikację, ten wariant skaluje dane tekstury odpowiedni rozmiar, przed utworzeniem tekstury. Jeśli początkowe dane są dostarczane w formacie skompresowane bloku, takich jak BC1, BC2 lub BC3, jest zdekodowany, skalowania i ponownie zakodowany, zanim zostanie on użyty do utworzenia mniejszych tekstury. (Rodzaj kompresji opartej na blokach oznacza, że proces bardzo dekodowania skali zakodować prawie zawsze powoduje, że niższej jakości obrazu niż wygenerowano tekstury skompresowane blok wersji skalowana tekstury, które nie były wcześniej zakodowany).  
  
 Jeśli włączono MCI mapy tekstury, wariant powoduje zmniejszenie liczby poziomów mipmapy odpowiednio — jeden mniejszej mniej podczas skalowania do połowie lub dwóch podczas skalowania do rozmiaru kwartału.  
  
## <a name="example"></a>Przykład  
 Ten wariant zmienia rozmiar tekstury w czasie wykonywania przed wywołaniem do `CreateTexture2D`. Firma Microsoft zaleca względem tej metody dla kodu produkcyjnego, ponieważ pełnym rozmiarze tekstury zużywać więcej miejsca na dysku i dodatkowych czynności można zwiększyć czas ładowania w aplikacji — szczególnie w przypadku skompresowanych tekstury, które wymagają znaczących obliczeniowy zasoby do kodowania. Zamiast tego zaleca się zmienić rozmiar tekstury w trybie offline za pomocą edytora obrazów lub procesora obrazu, który jest częścią planowaną kompilacji. Tych sposobów zmniejszyć wymagania dotyczące miejsca na dysku wyeliminować koszty środowiska uruchomieniowego w aplikacji i zapewniają więcej czasu przetwarzania, dzięki czemu można zachować najlepszą jakość obrazu podczas zmniejszania lub kompresowania Twojej tekstury.  
  
## <a name="see-also"></a>Zobacz też  
 [Wariant generowania mapy MCI](mip-map-generation-variant.md)   
 [Wariant kompresji tekstury BC](bc-texture-compression-variant.md)