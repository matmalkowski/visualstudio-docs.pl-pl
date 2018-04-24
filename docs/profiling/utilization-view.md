---
title: Widok wykorzystania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cpuutilization
helpviewer_keywords:
- Concurrency Visualizer, CPU Utilization View
ms.assetid: b4f7ceab-3653-4069-bb74-c309aec62866
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb49d47dbd01b1d84228e1f01dc4cbf7f49dfc8d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="utilization-view"></a>Widok wykorzystania
**Widok wykorzystania** Wyświetla informacje dotyczące Procesora GPU i innych zasobów systemowych, które są używane przez bieżący proces (wybierz **Analizuj** > **współbieżności Wizualizator** można uruchomić narzędzia concurrency visualizer). Pokazuje użycie średni core przez proces przeanalizowane, proces bezczynny, proces systemu i innych procesów uruchomionych w systemie, wraz z upływem czasu. Nie wyświetla, które określonym rdzeniu jest aktywny w danym momencie. Na przykład jeśli każdy dwa rdzenie są uruchamiane o pojemności 50 procent w określonym czasie, ten widok przedstawia jednego rdzenia logicznego jej użycia. Widok jest generowany przez podzielenie profilowania czasu na segmenty w krótkim czasie. Dla każdego segmentu wykres zawiera średnią liczbę wątków procesu, które są wykonywane na rdzeni logicznych podczas tego interwału.  
  
 ![Widok wykorzystania CPU](../profiling/media/vsts_ppacpuutil.png "VSTS_PPAcpuUtil")  
  
 Wykres przedstawia czas (na osi x) i średni rdzenie logiczne, które są wykorzystywane przez proces docelowy, proces bezczynny i procesów systemowych. (Proces bezczynny pokazuje bezczynnych rdzeni. Proces systemowy jest procesu w systemie Windows, które może wykonać pracę w imieniu innych procesów). Pozostałe procesy, które są uruchomione na koncie systemowym wykorzystania wszelkie pozostałe rdzeni.  
  
 Liczba rdzeni logicznych jest wyświetlana na osi y. Windows traktuje jednoczesnych Obsługa wielowątkowości w sprzęcie jako rdzenie logiczne (na przykład funkcji Hyper-Threading). W związku z tym systemu, które ma procesor czterordzeniowy obsługującej dwoma wątkami sprzętu na podstawowych jest wyświetlany jako system ośmiu logiczne — podstawowe. Dotyczy to również widoku rdzeni. Aby uzyskać więcej informacji, zobacz [widok rdzeni](../profiling/cores-view.md).  
  
 Wykres aktywności GPU pokazuje liczbę aparatów DirectX używana wraz z upływem czasu.  Aparat jest używana, jeśli pakiet DMA przetwarzania.  Wykres nie wyświetla określonego aparatu programu DirectX (na przykład aparatu 3D, aparat wideo i innych).  
  
## <a name="purpose"></a>Cel  
 Firma Microsoft zaleca z widoku wykorzystania jako punktu wyjścia do badania wydajności, korzystając z narzędzia Concurrency Visualizer. Ponieważ zapewnia przegląd stopień współbieżność w aplikacji wraz z upływem czasu, można użyć do szybką identyfikację obszarów, które wymagają dostrajania wydajności lub paralelizacja.  
  
 Jeśli interesuje Cię dostrajania wydajności, może podjąć próbę zidentyfikować problem, który nie spełnia Twoich oczekiwań. Może również być szukasz istnienia i Przyczyna regionów, które mają niskiego poziomu wykorzystania rdzeni Procesora logicznego. Może być również szukasz wzorców użycia między procesora CPU i procesora GPU.  
  
 Jeśli interesuje Cię parallelizing aplikacji, jest to najprawdopodobniej albo obszarów procesora wykonywania lub obszary, w którym nie są wykorzystanie procesora CPU.  
  
 Obszary procesora są zielone. Wykres przedstawia jednego rdzenia jej użycia, jeśli aplikacja jest szeregowego.  
  
 Obszary, w którym nie są wykorzystanie procesora CPU jest szary. Te może reprezentować punktów, w których aplikacja jest w stanie bezczynności lub wykonywania blokowania We/Wy, zapewniających możliwości równoległości przy nakładających się z innymi pracy procesora.  
  
 Po znalezieniu zachowanie zainteresowania można powiększyć w tym regionie przez zaznaczenie go. Po przejściu, można przełączyć do widoku wątków lub widok rdzeni dla bardziej szczegółowej analizy.  
  
 Jeśli używasz procesora GPU za pomocą C++ AMP lub DirectX, może Cię zainteresować identyfikowanie Liczba aparatów procesora GPU w użyciu lub obszary, w którym procesor GPU jest nieoczekiwanie bezczynności.  
  
## <a name="zooming"></a>Powiększanie  
 Aby powiększyć wykres wykorzystania CPU lub wykres aktywności GPU, zaznacz sekcję, lub użyj narzędzia suwaka powiększenia powyżej wykresu. Ustawienie powiększenia będzie się powtarzać, podczas przełączania z innymi widokami. Aby zmniejszyć ponownie, należy użyć narzędzia suwaka powiększenia. Można również powiększyć przy użyciu klawiszy Ctrl + przewijania.  
  
## <a name="see-also"></a>Zobacz też  
 [CONCURRENCY Visualizer](../profiling/concurrency-visualizer.md)   
 [Widok rdzeni](../profiling/cores-view.md)