---
title: 'Porady: zbieranie danych pobierania próbek na poziomie wiersza | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a10c8db7a9706c406cb192f9418c1fd8d04e888a
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765703"
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
  
-   Wiersze rozpocząć — numer wiersza próbki kodu.  
  
-   Koniec linii - końcowy numer wiersza źródłowego. Zazwyczaj jest taka sama jak danych "Wiersza begin", z wyjątkiem po jednej instrukcji program obejmuje wiele wierszy kodu źródłowego.  
  
-   Znaki rozpocząć - kolumnę początku próbka. Zwykle jest to 0 z wyjątkiem przypadków, gdy jeden wiersz zawiera wiele instrukcji programu.  
  
-   Znak end - końcowy kolumny próbka.  
  
-   Adres IP — adres, w której próbka została wykonana (tylko w widoku IP).  
  
 W **modułów** wyświetlić, jeśli funkcja statystyki na poziomie wiersza, statystyki są zagnieżdżone w każdej funkcji. Ponadto przedstawiono statystyki na poziomie protokołu IP, które są zagnieżdżone w każdym wierszu.  
  
### <a name="turn-off-line-level-sampling-for-managed-code"></a>Wyłącz pobierania próbek na poziomie wiersza dla zarządzanego kodu  
 Próbkowanie na poziomie wiersza jest domyślnie włączona. Można wyłączyć kolekcji danych na poziomie wiersza dla zarządzanego kodu za pomocą jednej z następujących poleceń:  
  
-   Przed rozpoczęciem profilowania, wpisz **VSPerfCLREnv /samplelineoff**. Dotyczy to zarówno aplikacji i usług.  
  
     — lub —  
  
-   Podczas uruchamiania aplikacji, wpisz **VSPerfCmd /lineoff \<inne argumenty >**.  
  
## <a name="see-also"></a>Zobacz także  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Analizowanie danych dotyczących narzędzi do oceny wydajności](../profiling/analyzing-performance-tools-data.md)