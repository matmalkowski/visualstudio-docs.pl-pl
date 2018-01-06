---
title: 'DA0506: Maksymalne Bajty prywatne przydzielone dla procesu poddawanego profilowaniu | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.rules.DA0506
- vs.performance.DA0506
- vs.performance.506
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4a624e790a618f923f5a70981fc3fef32809966d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="da0506-maximum-private-bytes-allocated-for-the-process-being-profiled"></a>DA0506: Maksymalne bajty prywatne przydzielone dla procesu poddawanego profilowaniu
|||  
|-|-|  
|Identyfikator reguły|DA0506|  
|Kategoria|Monitorowanie zasobów|  
|Metoda profilowania|Wszystkie|  
|Komunikat|Te dane zostały zebrane wyłącznie do celów informacyjnych. Licznik bajtów prywatnych procesu mierzy pamięć wirtualną alokowaną przez profilowany proces, który jest profilowania. Zgłaszana wartość to maksimum zaobserwowane we wszystkich interwałach pomiarowych.|  
|Typ reguły|Informacje|  
  
 Gdy profilu można za pomocą próbkowania, pamięci platformy .NET lub metody kontencji zasobów, należy zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="rule-description"></a>Opis reguły  
 Ten komunikat raporty maksymalną ilość pamięci wirtualnej, która w bajtach (bajty prywatne) aktualnie przydzielonej przez proces. Bajty prywatne reprezentuje lokalizacje pamięci wirtualnej, które zostały przydzielonej przez proces, który jest dostępny tylko przez wątki uruchomione wewnątrz procesu.  
  
 Do uruchamiania na maszynie 32-bitowych procesach 32-bitowych górny limit prywatna część przestrzeni adresowej procesu wynosi 2 GB. Przy użyciu [3 GB](http://go.microsoft.com/fwlink/?LinkId=177831) przełącznika Boot.ini procesy 32-bitowe mogą uzyskiwać do 3 GB pamięci wirtualnej. Proces 32-bitowy, który jest uruchomiony na komputerze 64-bitowe mogą uzyskiwać do 4 GB pamięci wirtualnej prywatnych.  
  
 Proces 64-bitowym, który jest uruchomiona na komputerze 64-bitowe mogą uzyskiwać do 8 TB pamięci wirtualnej prywatnych.  
  
 Wartość zgłaszaną to maksymalna we wszystkich interwałach pomiarowych, w których był aktywny PROFILOWANEGO procesu.  
  
 Aby uzyskać więcej informacji na temat przestrzeni adresowych procesu, zobacz [wirtualnej przestrzeni adresowej](http://go.microsoft.com/fwlink/?LinkId=177832) w dokumentacji systemu Windows zarządzania pamięcią.  
  
## <a name="how-to-use-rule-data"></a>Jak używać danych reguły  
 Użyj podanej wartości do porównania wydajności z różnych wersji lub kompilacji programu lub zrozumieć wydajność aplikacji w różnych scenariuszach profilowania.  
  
 Maksymalna wartość bajtów prywatnych procesu, który zbliża się do limitu architektury dla jak duży może zwiększyć przestrzeń adresowa procesu może prowadzić do poza wyjątkami pamięci. Aby uzyskać więcej informacji, zobacz [badanie problemy z pamięcią](http://go.microsoft.com/fwlink/?LinkID=177833) w MSDN Magazine.