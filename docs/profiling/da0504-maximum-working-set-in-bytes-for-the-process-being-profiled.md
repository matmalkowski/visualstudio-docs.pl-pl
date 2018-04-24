---
title: 'DA0504: Maksymalny rozmiar zestawu roboczego w bajtach dla PROFILOWANEGO procesu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0504
- vs.performance.504
- vs.performance.rules.DA0504
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6bb6c62a785815db0c678d0a1f0ff38ebea14d70
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="da0504-maximum-working-set-in-bytes-for-the-process-being-profiled"></a>DA0504: Maksymalny rozmiar zestawu roboczego w bajtach dla procesu poddawanego profilowaniu
|||  
|-|-|  
|Identyfikator reguły|DA0504|  
|Kategoria|Zarządzanie zasobami|  
|Metoda profilowania|Wszystkie|  
|Komunikat|Te dane zostały zebrane wyłącznie do celów informacyjnych. Licznik zestawu roboczego procesu mierzy fizyczne użycie pamięci przez proces, która jest profilowania. Zgłaszana wartość to maksimum zaobserwowane we wszystkich interwałach pomiarowych.|  
|Typ reguły|Informacje|  
  
 Gdy profilu można za pomocą próbkowania, pamięci platformy .NET lub metody kontencji zasobów, należy zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="rule-description"></a>Opis reguły  
 Ten komunikat raporty maksymalną ilość pamięci fizycznej w bajtach, które aktualnie używanej przez proces. Zestaw roboczy procesu reprezentuje stron przestrzeni adresowej procesu, które aktualnie znajdują się w pamięci fizycznej. Ta zasada raporty maksymalną wartość zestawu roboczego procesu podczas profilowania jest aktywny.  
  
 Wartość zgłaszaną zawiera rezydentna strony z segmentów w pamięci współużytkowanej, które odwołuje się do procesu. Pliki dll odwołania do procesów są objęte segmentów pamięci współużytkowanej, które są uwzględniane. Wartość proces zestaw roboczy może być większa niż ilość pamięci wirtualnej przydzielonej przez proces z powodu pamięci współużytkowanej segmentów.  
  
 Rozmiar zestawu roboczego procesu odzwierciedla ilość pamięci wirtualnej aktywnie używanej przez proces. Jest dotyczy także według ilości pamięci fizycznej (lub pamięci RAM) dostępna do uruchamiania aplikacji i rywalizacji o fizycznej pamięci z innych procesów uruchomionych. Aby uzyskać więcej informacji na temat zestawów roboczych procesu, zobacz [zestaw roboczy](http://go.microsoft.com/fwlink/?LinkId=177830) w dokumentacji systemu Windows, zarządzanie pamięcią MSDN.  
  
## <a name="how-to-use-rule-data"></a>Jak używać danych reguły  
 Reguła zbiera dane te miary z funkcje monitorowania wydajności systemu Windows i zgłasza wyłącznie w celach informacyjnych. Należy użyć do porównania wydajności z różnych wersji lub kompilacji programu lub zrozumienie wydajność aplikacji w scenariuszach różnych testu.  
  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczniki](../profiling/marks-view.md) danych profilowania. Znajdź **ustawić Process\Working** i **Pamięć\Strony/s** licznika kolumn. Następnie znajdź wartość maksymalną **ustawić Process\Working** i porównania go do **Pamięć\Strony/s** wartość. Często maksimum zestawu roboczego jest skojarzony z interwał, w którym się zmniejszyć aktywność We/Wy stronicowania, zwłaszcza, jeśli komputer jest ograniczone pamięci.