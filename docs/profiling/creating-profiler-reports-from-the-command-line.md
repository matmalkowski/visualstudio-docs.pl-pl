---
title: Tworzenie raportów profilera z wiersza polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d925e2c20a304239c8b510bf9ecc1fba123c4dfa
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="create-profiler-reports-from-the-command-line"></a>Tworzenie raportów profilera z wiersza polecenia
**VSPerfReport** narzędzia wiersza polecenia umożliwia tworzenie XML lub plik wartości rozdzielanych przecinkami (.csv) raportów z profilowania pliki danych (Vsp). Typy raportów VSPerfReport ściśle odpowiadające widoków na podstawie tabeli interfejsu dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Można filtrować raport do wyświetlenia tylko kodu i wyświetlania tylko jeden segment pliku danych profilowania. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
 Możesz również wprowadzić plików danych profilowania łatwiej można udostępnić przez osadzanie symboli plików Vsp i tworzenia raportu wstępnie przeanalizowane plików (vsps), które są one mniejsze i szybsze otworzyć.  
  
## <a name="common-tasks"></a>Wspólne zadania
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Tworzenie podstawowych raportów.** Utwórz wszystkie lub podzbiór VSPerfReport typów raportów.|-   [Tworzenie podstawowych raportów](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|  
|**Porównanie dwóch plików danych profilowania.** Utwórz raport "różnicowego", który porównuje dane dotyczące wydajności w dwóch plików danych profilowania.|-   [Porady: Tworzenie raportu porównania profilera z wiersza polecenia](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|  
|**Wyświetl ślad wywołania i dane zdarzenia śledzenia dla systemu Windows (ETW).** Tworzenie raportu śledzenia wywołań, w którym wyświetlane są informacje o chronometrażu dla każdego punktu wejścia i wyjścia funkcji aplikacji i każde wywołanie innych funkcji w funkcji. Lub Utwórz szczegółowe listę wszystkich zdarzeń funkcji ETW, które zostały zebrane w przebiegu profilowania.|-   [Porady: Tworzenie raportu śledzenia wywołań](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|  
|**Filtrowanie raportu.** Ogranicz raportu tylko funkcje kodu lub określony czas, w pliku danych profilowania.|-   [Porady: filtrowanie raportów z wiersza polecenia](../profiling/how-to-filter-reports-from-the-command-line.md)|  
|**Tworzenie przenośnych plików danych profilowania.** Aby udostępnianie danych profilowania, można osadzić symboli dla profilowania do pliku Vsp. Można także utworzyć wstępnie przeanalizowane profilowania plik danych (vsps), który mniejszej i szybsze otworzyć.|-   [Tworzenie przenośnych plików danych profilowania](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|