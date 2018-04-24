---
title: 'DA0505: Średnie Bajty prywatne przydzielone dla procesu poddawanego profilowaniu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0505
- vs.performance.rules.DA0505
- vs.performance.505
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b078a920f84037ec9a90e4e050a070bf73b0f47
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505: Średnie bajty prywatne przydzielone dla procesu poddawanego profilowaniu
|||  
|-|-|  
|Identyfikator reguły|DA0505|  
|Kategoria|Zarządzanie zasobami|  
|Metoda profilowania|Wszystkie|  
|Komunikat|Te dane zostały zebrane wyłącznie do celów informacyjnych. Licznik bajtów prywatnych procesu mierzy pamięć wirtualną alokowaną przez profilowany proces, który jest profilowania. Zgłaszana wartość to średnia obliczona dla wszystkich interwałów pomiarowych.|  
|Typ reguły|Informacje|  
  
 Gdy profilu można za pomocą próbkowania, pamięci platformy .NET lub metody kontencji zasobów, należy zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="rule-description"></a>Opis reguły  
 Ten komunikat raporty średnia ilość pamięci wirtualnej, która w bajtach (bajty prywatne) aktualnie przydzielonej przez proces. Bajty prywatne reprezentuje lokalizacje pamięci wirtualnej, które zostały przydzielonej przez proces, który jest dostępny tylko przez wątki uruchomione wewnątrz procesu.  
  
 Do uruchamiania na maszynie 32-bitowych procesach 32-bitowych górny limit prywatna część przestrzeni adresowej procesu wynosi 2 GB. Przy użyciu [3 GB](http://go.microsoft.com/fwlink/?LinkId=177831) przełącznika Boot.ini procesy 32-bitowe mogą uzyskiwać do 3 GB pamięci wirtualnej. Proces 32-bitowy, który jest uruchomiony na komputerze 64-bitowe mogą uzyskiwać do 4 GB pamięci wirtualnej prywatnych.  
  
 Proces 64-bitowym, który jest uruchomiona na komputerze 64-bitowe mogą uzyskiwać do 8 TB pamięci wirtualnej prywatnych.  
  
 Wartość zgłaszaną jest średnią we wszystkich interwałach pomiarowych, w których był aktywny PROFILOWANEGO procesu.  
  
 Aby uzyskać więcej informacji na temat przestrzeni adresowych procesu, zobacz [wirtualnej przestrzeni adresowej](http://go.microsoft.com/fwlink/?LinkId=177832) w dokumentacji systemu Windows zarządzania pamięcią.  
  
## <a name="how-to-use-rule-data"></a>Jak używać danych reguły  
 Użyj podanej wartości do porównania wydajności z różnych wersji lub kompilacji programu lub zrozumieć wydajność aplikacji w różnych scenariuszach profilowania.