---
title: "Porady: Wybieranie zdarzeń pobierania próbek | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.sampling
helpviewer_keywords:
- clock cycles sample event
- sample events, choosing
- profiling tools, sample events
- page faults sample event
- system calls sample event
- performance counter sample event
- performance tools, sample events
ms.assetid: ce7cb734-80ac-4930-a4ef-e24395e1cc07
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8475544d6ecb822a25a423b73543d7364d79da10
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-choose-sampling-events"></a>Porady: wybieranie zdarzeń pobierania próbek
Domyślnie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędziach profilowania zbiera dane dotyczące wydajności w przedziale czasu, który jest określony jako liczba cykli procesora, które są używane przez PROFILOWANEGO procesu. Domyślna liczba cykli w interwale jest 10 000 000, czyli około 0,01 sekund na 1 komputerze GH. Można zmienić liczby cykli w interwale, i można zmienić zdarzenie próbkowania. Dostępne są następujące zdarzenia próbkowania:  
  
-   Cykle zegara - problemów procesora.  
  
-   Błędy strony - problemów związanych z pamięcią.  
  
-   Wywołania systemowe — I/E związane z problemów.  
  
-   Licznik wydajności — liczniki CPU problemy z wydajnością niskiego poziomu.  
  
> [!IMPORTANT]
>  Jeśli są zbieranie danych pamięci .NET (alokacji okresy istnienia obiektów i/lub), za pomocą metody pobierania próbek, zdarzenia próbkowania wszystkie określone przez użytkownika są ignorowane, a alokacje odpowiedniej ilości pamięci i/lub zdarzenia wyrzucania elementów bezużytecznych są używane do zbierania danych.  
  
### <a name="to-select-a-sample-event"></a>Aby wybrać zdarzenie próbkowania  
  
1.  W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij przycisk **właściwości**.  
  
2.  W **strony właściwości**, kliknij przycisk **próbkowania** właściwości.  
  
3.  Z **zdarzenie próbkowania** listy rozwijanej wybierz zdarzenie próbkowania chcesz użyć do profilu aplikacji.  
  
    > [!NOTE]
    >  **Dostępnych liczników wydajności** są włączone, tylko jeśli wybierzesz **licznika wydajności** z **zdarzenie próbkowania** listy rozwijanej.  
  
4.  W przypadku wybrania **licznika wydajności**, wybierz określonego licznika Procesora z **dostępnych liczników wydajności** kontrolki widok drzewa.  
  
    -   Liczniki **przenośne zdarzenia** węzła są dostępne na wszystkich typach procesorów.  
  
    -   Liczniki **zdarzenia platformy** węzeł specyficznych dla procesora na bieżącym komputerze i mogą nie być dostępne dla innych typów procesorów.  
  
5.  Po wybraniu zdarzenie próbkowania domyślną wartość interwału próbkowania jest wyświetlany w **interwał próbkowania** pola tekstowego. W razie potrzeby można wprowadzić wartość w polu tekstowym.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Porady: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md)   
 [Procesor CPU i liczniki systemu Windows](../profiling/cpu-and-windows-counters.md)   
 [Opis pobierania wartości danych](../profiling/understanding-sampling-data-values.md)   
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)