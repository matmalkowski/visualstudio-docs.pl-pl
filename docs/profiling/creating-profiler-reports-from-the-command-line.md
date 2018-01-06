---
title: "Tworzenie raportów profilera z wiersza polecenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 474b7c0167b02665a5bc2ff5c1297f768facbc32
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="creating-profiler-reports-from-the-command-line"></a>Tworzenie raportów profilera z wiersza polecenia
**VSPerfReport** narzędzia wiersza polecenia umożliwia tworzenie XML lub plik wartości rozdzielanych przecinkami (.csv) raportów z profilowania pliki danych (Vsp). Typy raportów VSPerfReport ściśle odpowiadające widoków na podstawie tabeli interfejsu dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Można filtrować raport do wyświetlenia tylko kodu i wyświetlania tylko jeden segment pliku danych profilowania. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
 Możesz również wprowadzić plików danych profilowania łatwiej można udostępnić przez osadzanie symboli plików Vsp i tworzenia raportu wstępnie przeanalizowane plików (vsps), które są one mniejsze i szybsze otworzyć.  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Tworzenie podstawowych raportów.** Utwórz wszystkie lub podzbiór VSPerfReport typów raportów.|-   [Tworzenie raportów podstawowych](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|  
|**Porównanie dwóch plików danych profilowania.** Utwórz raport "różnicowego", który porównuje dane dotyczące wydajności w dwóch plików danych profilowania.|-   [Porady: Tworzenie raportu porównania profilera z wiersza polecenia](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|  
|**Wyświetl ślad wywołania i dane zdarzenia śledzenia dla systemu Windows (ETW).** Tworzenie raportu śledzenia wywołań, w którym wyświetlane są informacje o chronometrażu dla każdego punktu wejścia i wyjścia funkcji aplikacji i każde wywołanie innych funkcji w funkcji. Lub Utwórz szczegółowe listę wszystkich zdarzeń funkcji ETW, które zostały zebrane w przebiegu profilowania.|-   [Porady: Tworzenie raportu śledzenia wywołań](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|  
|**Filtrowanie raportu.** Ogranicz raportu tylko funkcje kodu lub określony czas, w pliku danych profilowania.|-   [Porady: filtrowanie raportów z wiersza polecenia](../profiling/how-to-filter-reports-from-the-command-line.md)|  
|**Tworzenie przenośnych plików danych profilowania.** Aby udostępnianie danych profilowania, można osadzić symboli dla profilowania do pliku Vsp. Można także utworzyć wstępnie przeanalizowane profilowania plik danych (vsps), który mniejszej i szybsze otworzyć.|-   [Tworzenie przenośnych plików danych profilowania](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|