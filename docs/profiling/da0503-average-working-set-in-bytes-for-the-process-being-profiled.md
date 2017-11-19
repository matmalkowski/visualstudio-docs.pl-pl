---
title: "DA0503: Średni rozmiar zestawu roboczego w bajtach dla PROFILOWANEGO procesu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.503
- vs.performance.DA0503
- vs.performance.rules.DA0503
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e47af0282eb5731a931be35a6acf16c776204574
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="da0503-average-working-set-in-bytes-for-the-process-being-profiled"></a>DA0503: Średni rozmiar zestawu roboczego w bajtach dla procesu poddawanego profilowaniu
|||  
|-|-|  
|Identyfikator reguły|DA0503|  
|Kategoria|Monitorowanie zasobów|  
|Metoda profilowania|Wszystkie|  
|Komunikat|Te dane zostały zebrane wyłącznie do celów informacyjnych. Licznik zestawu roboczego procesu mierzy fizyczne użycie pamięci przez proces, która jest profilowania. Zgłaszana wartość to średnia obliczona dla wszystkich interwałów pomiarowych.|  
|Typ reguły|Informacje|  
  
 Gdy profilu można za pomocą próbkowania, pamięci platformy .NET lub metody kontencji zasobów, należy zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="rule-description"></a>Opis reguły  
 Ten komunikat raporty średnia ilość pamięci fizycznej obecnie używanej przez proces w bajtach (zestaw roboczy). Zestaw roboczy procesu reprezentuje stron przestrzeni adresowej procesu, które aktualnie znajdują się w pamięci fizycznej.  
  
 Podanej wartości zawiera rezydentna strony z segmentów w pamięci współużytkowanej, które odwołuje się do procesu. Pliki dll odwołania do procesów są objęte segmentów pamięci współużytkowanej, które są uwzględniane. Wartość zestawu roboczego procesu może być większa niż ilość pamięci wirtualnej przydzielonej przez proces z powodu pamięci współużytkowanej segmentów.  
  
 Podanej wartości jest średnią we wszystkich interwałach pomiarowych, w których był aktywny PROFILOWANEGO procesu.  
  
 Rozmiar zestawu roboczego procesu odzwierciedla ilość pamięci wirtualnej aktywnie używanej przez proces. Jest dotyczy także według ilości pamięci fizycznej (lub pamięci RAM) dostępna do uruchamiania aplikacji i rywalizacji o fizycznej pamięci z innych procesów uruchomionych. Jeśli ilość pamięci fizycznej jest ograniczony, wartość zestawu roboczego procesu jest stanie różnić jako systemy operacyjne próbuje Równoważenie wykorzystania pamięci na aktywnych procesów poprzez okresowo przycinanie dość nieaktywne strony z zestawu roboczego procesu.  
  
 Aby uzyskać więcej informacji na temat zestawów roboczych procesu, zobacz [zestaw roboczy](http://go.microsoft.com/fwlink/?LinkId=177830) w dokumentacji systemu Windows, zarządzanie pamięcią MSDN.  
  
## <a name="how-to-use-rule-data"></a>Jak używać danych reguły  
 Użyj wartości reguły do porównania wydajności z różnych wersji lub kompilacji programu lub aby zrozumieć działanie aplikacji w różnych scenariuszach profilowania.  
  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczniki](../profiling/marks-view.md) widoku danych profilowania. Znajdź **ustawić Process\Working** i **Pamięć\Strony/s** kolumn. Porównanie tych dwóch kolumn, aby ustalić, jeśli są określone fazy wykonywania programu, które mogą być skojarzone z zwiększoną aktywność We/Wy stronicowania.