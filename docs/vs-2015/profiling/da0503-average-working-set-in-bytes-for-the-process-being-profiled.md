---
title: 'DA0503: Średni zestaw roboczy w bajtach dla PROFILOWANEGO procesu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.503
- vs.performance.DA0503
- vs.performance.rules.DA0503
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e71d7e630505d44392610ab5ba94c19b3928f7f9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42674820"
---
# <a name="da0503-average-working-set-in-bytes-for-the-process-being-profiled"></a>DA0503: Średni rozmiar zestawu roboczego w bajtach dla procesu poddawanego profilowaniu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [DA0503: średni zestaw roboczy w bajtach dla procesu poddawanego profilowaniu](https://docs.microsoft.com/visualstudio/profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled).  
  
Identyfikator reguły | DA0503 |  
| Kategoria | Monitorowanie zasobów |  
| Metoda profilowania | Wszystkie |  
| Komunikat | Te dane zostały zebrane wyłącznie w celach informacyjnych. Licznik zestawu roboczego procesu mierzy fizyczne użycie pamięci przez profilowany proces. Zgłaszana wartość to średnia obliczona dla wszystkich interwałów pomiarowych. |  
| Typ reguły | Informacji |  
  
 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="rule-description"></a>Opis reguły  
 Ten komunikat raporty średniej ilości pamięci fizycznej w bajtach (zestaw roboczy) aktualnie używanej przez proces. Proces Zestaw roboczy reprezentuje stron z przestrzeni adresowej procesu, które obecnie znajdują się w pamięci fizycznej.  
  
 Wystąpienia wartości zgłoszonej zawiera rezydentnego strony z segmentów pamięci współużytkowanej, których proces ma odwołania. Współdzielone Dlll przetwarzania odwołania są objęte segmentów pamięci współużytkowanej, które są uwzględniane. Wartość zestawu roboczego mogą być większe niż ilość pamięci wirtualnej, która ze względu na segmenty udostępnionej pamięci przydzielonej przez proces.  
  
 Wystąpienia wartości zgłoszonej jest średnią we wszystkich interwałach pomiarowych, w których była aktywna PROFILOWANEGO procesu.  
  
 Rozmiar zestawu roboczego procesu odzwierciedla ilość pamięci wirtualnej aktywnie używanej przez proces. Również jest zależna od ilości pamięci fizycznej (lub pamięci RAM) dostępna do uruchamiania aplikacji i rywalizacji o tej pamięci fizycznej z innych uruchomionych procesów. Jeśli pamięci fizycznej jest ograniczony, wartość zestawu roboczego procesu jest stanie różnią się znacznie jako systemów operacyjnych próbuje saldo użycie pamięci przez aktywne procesy według okresowo przycinania dość nieaktywne strony z zestawu roboczego procesu.  
  
 Aby uzyskać więcej informacji na temat zestawów roboczych procesu, zobacz [rozmiar zestawu roboczego](http://go.microsoft.com/fwlink/?LinkId=177830) w dokumentacji MSDN zarządzanie pamięcią Windows.  
  
## <a name="how-to-use-rule-data"></a>Sposób użycia danych reguły  
 Użyj wartości reguły, aby porównać wydajność różnych wersji lub kompilacjach programu lub aby zrozumieć wydajność aplikacji w różnych scenariuszach profilowania.  
  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczniki](../profiling/marks-view.md) widoku danych profilowania. Znajdź **Ustaw Process\Working** i **Pamięć\Strony/s** kolumn. Porównaj dwie kolumny i ustalić, czy określonych faz wykonywania programu, które mogą być skojarzone z zwiększoną aktywność We/Wy stronicowania.



