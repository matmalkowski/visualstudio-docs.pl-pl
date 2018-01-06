---
title: "Opcje sesji wydajności ogólnej ustawienie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.general
ms.assetid: 6b60bd1b-2198-4261-b84e-9b2d8494a992
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8ca1f5d0c310fa4f9d75f27c6baf73f7a230e87e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="setting-general-performance-session-options"></a>Ustawianie opcji sesji wydajności ogólnej
Można ustawić metod gromadzenia danych i konwencji nazewnictwa danych profilowania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sesji wydajności narzędzi profilowania w **ogólne** strony okna dialogowego właściwości sesji wydajności. Aby otworzyć to okno dialogowe z **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij przycisk **właściwości**.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
## <a name="choosing-data-collection-methods"></a>Wybieranie metody zbierania danych  
 Ustawianie metody podstawowej kolekcji, wybierając jedną z opcji w obszarze **kolekcja profilowania**. Opcje zostały opisane w następujących w poniższej tabeli:  
  
|||  
|-|-|  
|**Próbkowanie**. Metoda pobierania próbek zbiera informacje dotyczące profilowania w regularnych odstępach czasu. Ta metoda jest przydatna do znajdowania problemy dotyczące użycia procesora i Sugerowane metody uruchamiania większości dochodzenia wydajności.|-   [Zbieranie statystyk wydajności za pomocą metody pobierania próbek](../profiling/collecting-performance-statistics-by-using-sampling.md)|  
|**Instrumentacja**. Metoda Instrumentacji injects do kopii modułu profilowania kodu, który rejestruje każdy wpis, zakończenia i wywołanie funkcji funkcji w module podczas przebiegu profilowania. Ta metoda jest przydatne do zbierania czasu szczegółowe informacje o sekcji kodu i zrozumienie wpływu wejściowymi i wyjściowymi operacje na wydajność aplikacji.|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|  
|**Współbieżność**. Metoda współbieżności zbiera dane dla każdego zdarzenia, że wykonanie bloki kodu, na przykład jeśli wątek oczekuje na zablokowany dostęp do zasobów aplikacji ma zostać zwolniony. Ta metoda jest przydatna do analizowania aplikacji wielowątkowych.|-   [Zbieranie danych współbieżności procesu i wątku](../profiling/collecting-thread-and-process-concurrency-data.md)|  
  
 Możliwość zbierania danych pamięci .NET przy użyciu metody próbkowania i instrumentacji. Wybierz typ danych w ramach **profilowania pamięci .NET**.  
  
|||  
|-|-|  
|**Zbierz informacje dotyczące alokacji obiektów platformy .NET**. Domyślnie dane obejmują liczbę i rozmiar przydzielonych obiektów. Wybierz lub wyczyść to pole wyboru, aby włączyć lub wyłączyć zbieranie danych pamięci .NET.<br /><br /> **Zbierz również informacje dotyczące okresu istnienia obiektu platformy .NET**. Zaznacz to pole wyboru, aby dołączyć dane o generacje kolekcji garbage użytych w celu odzyskania pamięci obiektów.|-   [Zbieranie alokacji pamięci .NET i okres istnienia obiektu](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|  
  
 Strona sesji profilowania jest wyświetlany po rozpoczęciu do profilu aplikacji, w którym można wstrzymać, wznowić i zatrzymanie profilowania.  
  
 ![Strona sesji profilowania](../profiling/media/prof_profilingsessionpage.png "PROF_ProfilingSessionPage")  
  
## <a name="setting-profiling-datra-file-options"></a>Ustawianie opcji pliku Datra profilowania  
  
|||  
|-|-|  
|**Raport**. Domyślnie plik danych (Vsp) profilowania podano nazwę PROFILOWANEGO aplikacji i znajduje się w folderze rozwiązania lub projektu. Ciąg daty również jest dołączany do nazwy, a numer zwiększany jest dodawany do plików danych, które w przeciwnym razie byłyby takich samych nazwach. Te opcje można zmienić.|-   [Porady: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|