---
title: 'DA0506: Maksymalne Bajty prywatne przydzielone dla procesu poddawanego profilowaniu | Dokumentacja firmy Microsoft'
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
- vs.performance.rules.DA0506
- vs.performance.DA0506
- vs.performance.506
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2475c0c5c8755b89e790a0e10330c9832e7474d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42694221"
---
# <a name="da0506-maximum-private-bytes-allocated-for-the-process-being-profiled"></a>DA0506: Maksymalne bajty prywatne przydzielone dla procesu poddawanego profilowaniu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [DA0506: maksymalne Bajty prywatne przydzielone dla procesu poddawanego profilowaniu](https://docs.microsoft.com/visualstudio/profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled).  
  
Identyfikator reguły | DA0506 |  
| Kategoria | Monitorowanie zasobów |  
| Metoda profilowania | Wszystkie |  
| Komunikat | Te dane zostały zebrane wyłącznie w celach informacyjnych. Licznik bajtów prywatnych procesu mierzy pamięć wirtualną alokowaną przez profilowany proces. Zgłaszana wartość to maksimum zaobserwowane we wszystkich interwałach pomiarowych. |  
| Typ reguły | Informacji |  
  
 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="rule-description"></a>Opis reguły  
 Ten komunikat raporty maksymalną ilość pamięci wirtualnej, która w bajtach (bajty prywatne) aktualnie przydzielonej przez proces. Bajty prywatne reprezentuje lokalizacje pamięci wirtualnej, które zostały przydzielone przez proces, który może zostać oceniony jedynie przez działający proces wątki.  
  
 Dla 32-bitowych procesów uruchomionych na komputerze 32-bitowym górny limit prywatna część przestrzeni adresowej procesu wynosi 2 GB. Za pomocą [3 GB](http://go.microsoft.com/fwlink/?LinkId=177831) przełącznika pliku Boot.ini, procesów 32-bitowych można pobrać do 3 GB pamięci wirtualnej. Proces 32-bitowy, który działa na komputerze 64-bitowym, mogą uzyskiwać maksymalnie 4 GB pamięci wirtualnej prywatny.  
  
 Proces 64-bitowy, który działa na komputerze 64-bitowym, mogą uzyskiwać do 8 TB pamięci wirtualnej prywatny.  
  
 Wartość zgłaszaną jest maksymalną we wszystkich interwałach pomiarowych, w których była aktywna PROFILOWANEGO procesu.  
  
 Aby uzyskać więcej informacji na temat procesu przestrzeni adresowych zobacz [wirtualną przestrzenią adresów](http://go.microsoft.com/fwlink/?LinkId=177832) w dokumentacji programu Windows zarządzania pamięcią.  
  
## <a name="how-to-use-rule-data"></a>Sposób użycia danych reguły  
 Aby porównać wydajność różnych wersji lub kompilacjach programu lub aby zrozumieć wydajność aplikacji w różnych scenariuszach profilowania, należy użyć podanej wartości.  
  
 Maksymalna wartość Prywatne bajty procesu, który zbliża się do limitu architektury dla rozmiar, jaki można powiększać przestrzeni adresowej procesu może prowadzić do poza wyjątki pamięci. Aby uzyskać więcej informacji, zobacz [badanie problemów z pamięcią](http://go.microsoft.com/fwlink/?LinkID=177833) w MSDN Magazine.



