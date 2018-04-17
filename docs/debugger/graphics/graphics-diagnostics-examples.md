---
title: Przykłady diagnostyki grafiki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 45dd86b2-801e-4b07-a8c4-7bd25641d7f8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e9a1685423e2a8bec56d01444e5a4d0340a456e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="graphics-diagnostics-examples"></a>Przykłady diagnostyki grafiki
Następujące przykłady przedstawiają sposób debugowania problemy z renderowaniem w aplikacjach opartych na technologii DirectX przy użyciu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagnostyki grafiki.  
  
## <a name="capturing-graphics-information"></a>Przechwytywanie informacji graficznych  
 Zanim użyjesz diagnostyki grafiki do diagnozowania problemów renderowania w aplikacji należy przechwytywanie informacji graficznych z aplikacji jest uruchomiona. Z aplikacji, która działa lokalnie lub aplikacji, która jest uruchomiona na komputerze zdalnym lub innych urządzeń, można przechwycić informacji graficznych. Te wskazówki pokazują, jak przechwytywanie informacji graficznych z aplikację ręcznie lub programowo:  
  
-   [Przewodnik: przechwytywanie informacji graficznych](walkthrough-capturing-graphics-information.md)  
  
-   [Przewodnik: programowe przechwytywanie informacji graficznych](walkthrough-capturing-graphics-information-programmatically.md)  
  
## <a name="use-graphics-diagnostics-with-an-arm-based-device"></a>Diagnostyka grafiki za pomocą urządzenia opartego na architekturze ARM  
 Można użyć diagnostyki grafiki do debugowania aplikacji Direct3D na urządzeniu z systemem opartego na architekturze ARM przy użyciu zdalnego debugowania. Aby uzyskać więcej informacji, zobacz [porady: użycie diagnostyki grafiki z urządzeniem ARM](how-to-use-graphics-diagnostics-with-an-arm-device.md).  
  
## <a name="playing-back-graphics-information"></a>Odtwarzanie do tyłu informacji graficznych  
 Po przechwyceniu informacji graficznych w uruchomionej aplikacji można odtwarzać przechwyconych zdarzeń do diagnozowania problemów renderowania. Aby odtworzyć, można użyć komputerze deweloperskim lub można użyć komputera zdalnego lub urządzenia, które są dołączone do. Aby uzyskać więcej informacji, zobacz [porady: zmiana maszyny odtwarzania diagnostyki grafiki](how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="debugging-missing-objects"></a>Debugowanie brakujących obiektów  
 Brak obiektu (lub obiektów) jest jednym z najbardziej typowe problemy renderowania, które deweloperzy grafiki doświadczeniem. Tego rodzaju problemy mogą być trudne do diagnozowania, ponieważ wiele rodzajów błędów może spowodować, że obiekt, aby najwyraźniej znikają. Typowe przyczyny występowania brakujących obiektów obejmują stan nieprawidłowo skonfigurowane urządzenia, problemy podczas transformacji obiektu, który lub potoku grafiki nieprawidłowo skonfigurowane.  
  
 Te scenariusze pokazują, jak można użyć diagnostyki grafiki, aby ustalić, dlaczego brakuje obiektu i znaleźć kod, który jest odpowiedzialny.  
  
-   [Przewodnik: brak obiektów spowodowany stanem urządzenia](walkthrough-missing-objects-due-to-device-state.md)  
  
-   [Przewodnik: brak obiektów spowodowany cieniowaniem wierzchołków](walkthrough-missing-objects-due-to-vertex-shading.md)  
  
-   [Przewodnik: brak obiektów spowodowany błędnie skonfigurowanym potokiem](walkthrough-missing-objects-due-to-misconfigured-pipeline.md)  
  
## <a name="debugging-rendering-errors"></a>Debugowanie błędów renderowania  
 Obiektu (lub obiektów), nie ma poprawny wygląd jest inny powszechny problem, który deweloperzy grafiki doświadczeniem. Tego rodzaju problemy mogą być trudne do diagnozowania ponieważ niepoprawny wygląd i jego przyczyną może należeć do zakresu od bardzo oczywiste — wiązanie niewłaściwy tekstury — do bardzo niewielkie — usterki w kodzie programu do cieniowania lub nieoczekiwany interakcji między programów do cieniowania. Niektóre problemy mogą być spowodowane przez kombinację błędy.  
  
 Poniżej przedstawiono scenariusz, w którym przedstawiono sposób użycia diagnostyki grafiki do śledzenia problem z renderowaniem nie tak niewielkie, powodowany przez usterkę pomocniczych programu do cieniowania:  
  
-   [Przewodnik: debugowanie błędów renderowania spowodowanych cieniowaniem](walkthrough-debugging-rendering-errors-due-to-shading.md)  
  
## <a name="debugging-compute-shaders"></a>Debugowanie programów do cieniowania obliczeń  
 Można użyć diagnostyki grafiki do debugowania DirectCompute cieniowania obliczenia jądra, które generują niepoprawne wyniki. Z DirectCompute moc obliczeniową procesora GPU służy do wykonywania obliczeń na dużą liczbę elementów danych równolegle. Dla niektórych rodzaje problemów, wykorzystanie procesora GPU mogą wykonywać wiele razy szybciej niż nawet dobrze zoptymalizowanego kodu procesora CPU. Jednak tradycyjnych debugery nie może wykryć kodu uruchamianego na procesorze GPU. Debugowanie tego rodzaju kodu wymaga specjalnych narzędzia, które są często specyficznych dla dostawcy, a nie może być zintegrowana z programu Visual Studio. Aby wprowadzić bardziej spójny debugowania cieniowania obliczenia w zakresie GPU, diagnostyki grafiki rejestruje zdarzenia wysyłania DirectCompute — oprócz zdarzeń renderowania Direct3D —, aby znanych narzędzi można używać do debugowania problemów w kodzie cieniowania obliczenia.  
  
 W scenariuszu pokazano, jak można debugować problem symulacji powodowany przez usterkę w cieniowania obliczenia zobacz [wskazówki: przy użyciu diagnostyki grafiki do debugowania cieniowania obliczenia](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md).