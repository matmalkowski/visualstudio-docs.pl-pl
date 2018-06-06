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
ms.openlocfilehash: 3433bef9b30c9b912d721b526ab11692a8de78af
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749274"
---
# <a name="create-profiler-reports-from-the-command-line"></a>Tworzenie raportów profilera z wiersza polecenia
**VSPerfReport** narzędzia wiersza polecenia umożliwia utworzenie. *XML* lub wartości oddzielanych przecinkami (. *CSV*) raporty z danych profilowania (. *Vsp*) plików. Typy raportów VSPerfReport ściśle odpowiadające widoków na podstawie tabeli interfejsu dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Można filtrować raport do wyświetlenia tylko kodu i wyświetlania tylko jeden segment pliku danych profilowania. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
 Można również ustawić plików danych profilowania łatwiej można udostępnić osadzanie symboli. *vsp* pliki i przez tworzenie raportu wstępnie przeanalizowane (. *vsps*) plików, które są one mniejsze i szybsze do otwarcia.  
  
## <a name="common-tasks"></a>Wspólne zadania
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Tworzenie podstawowych raportów.** Utwórz wszystkie lub podzbiór VSPerfReport typów raportów.|-   [Tworzenie podstawowych raportów](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|  
|**Porównanie dwóch plików danych profilowania.** Utwórz raport "różnicowego", który porównuje dane dotyczące wydajności w dwóch plików danych profilowania.|-   [Porady: Tworzenie raportu porównania profilera z wiersza polecenia](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|  
|**Wyświetl ślad wywołania i dane zdarzenia śledzenia dla systemu Windows (ETW).** Tworzenie raportu śledzenia wywołań, w którym wyświetlane są informacje o chronometrażu dla każdego punktu wejścia i wyjścia funkcji aplikacji i każde wywołanie innych funkcji w funkcji. Lub Utwórz szczegółowe listę wszystkich zdarzeń funkcji ETW, które zostały zebrane w przebiegu profilowania.|-   [Porady: Tworzenie raportu śledzenia wywołań](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|  
|**Filtrowanie raportu.** Ogranicz raportu tylko funkcje kodu lub określony czas, w pliku danych profilowania.|-   [Porady: filtrowanie raportów z wiersza polecenia](../profiling/how-to-filter-reports-from-the-command-line.md)|  
|**Tworzenie przenośnych plików danych profilowania.** Aby udostępnianie danych profilowania, można osadzić symboli dla przebiegu do profilowania. *vsp* pliku. Można również utworzyć wstępnie analizowanych danych profilowania (. *vsps*) mniejszej i szybsze otworzyć plik.|-   [Tworzenie przenośnych plików danych profilowania](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|