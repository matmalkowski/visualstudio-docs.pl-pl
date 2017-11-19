---
title: "Porady: zbieranie danych pobierania próbek na poziomie wiersza | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 059443d13579086992228344d23a72408949cc29
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-collect-line-level-sampling-data"></a>Porady: zbieranie danych pobierania próbek na poziomie wiersza
Próbkowanie na poziomie wiersza jest możliwość określenia, gdzie w kodzie funkcji obciążenie procesora, takich jak funkcja, która ma wysoką wyłącznych próbek, procesor ma poświęcić większość czasu profilera.  
  
## <a name="overview"></a>Omówienie  
 Próbkowanie na poziomie wiersza, profilera przeprowadzi program stos wywołań w ustalonych odstępach czasu i agreguje wyniki. Te wyniki wskazują, jakie instrukcje procesor było wykonywane, gdy zostały próbki. Zebrane dane dotyczące wyłącznych próbek jest następnie analizę w celu identyfikowania wierszy kodu i wskaźnik instrukcji (IP).  
  
 Próbkowanie na poziomie wiersza działa w przypadku zarządzanych, jak również natywnego kodu. Raporty wydajności, które zawierają te dane obejmują widok linii i widok modułów.  
  
 Informacje o begin/end znaku nie jest dostępna dla kodu natywnego. Wielowierszowy instrukcje wiersza rozpocząć informacji nie jest dostępna dla kodu natywnego; tylko wiersza końcowego informacje są dostępne.  
  
### <a name="available-data"></a>Dostępnych danych  
 Dostępne próbkowania na poziomie wiersza danych obejmuje następujące informacje:  
  
-   Nazwa funkcji.  
  
-   Adres funkcji.  
  
-   Rozpocznij wiersza — numer wiersza próbki kodu.  
  
-   Koniec linii - końcowy numer wiersza źródłowego. Zazwyczaj jest taka sama jak danych "Wiersza begin", z wyjątkiem po jednej instrukcji program obejmuje wiele wierszy kodu źródłowego.  
  
-   Znak rozpocząć - kolumnę początku próbka. Zwykle jest to 0 z wyjątkiem przypadków, gdy jeden wiersz zawiera wiele instrukcji programu.  
  
-   Znak end - końcowy kolumny próbka.  
  
-   Adres IP — adres, w której próbka została wykonana (tylko w widoku IP).  
  
 W **modułów** wyświetlić, jeśli funkcja statystyki na poziomie wiersza, statystyki są zagnieżdżone w każdej funkcji. Ponadto przedstawiono statystyki na poziomie protokołu IP, które są zagnieżdżone w każdym wierszu.  
  
### <a name="turn-off-line-level-sampling-for-managed-code"></a>Wyłącz pobierania próbek na poziomie wiersza dla zarządzanego kodu  
 Próbkowanie na poziomie wiersza jest domyślnie włączona. Mogą wyłączyć zbieranie danych na poziomie wiersza dla kodu zarządzanego, wykonując jedną z następujących czynności:  
  
-   Przed rozpoczęciem profilowania, wpisz **VSPerfCLREnv /samplelineoff**. Dotyczy to zarówno aplikacji i usług.  
  
     — lub —  
  
-   Podczas uruchamiania aplikacji, wpisz **VSPerfCmd /lineoff \<inne argumenty >**.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Analizowanie wydajności narzędzi danych](../profiling/analyzing-performance-tools-data.md)