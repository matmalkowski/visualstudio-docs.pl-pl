---
title: 'DA0029: Nieobsługiwana wersja CLR | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad41dc48303fa836e4c15f0e450b3fade60ff646
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Nieobsługiwana wersja CLR
|||  
|-|-|  
|Identyfikator reguły|DA0029|  
|Kategoria|Użycie narzędzia profilowania|  
|Metoda profilowania|Profilowanie z wiersza polecenia|  
|Komunikat|Wykryto nieobsługiwaną wersję środowiska CLR podczas zbierania. Symbole zarządzane mogą nie być rozpoznawane poprawnie.|  
|Typ reguły|Informacje.|  
  
## <a name="cause"></a>Przyczyna  
 Próbujesz profilu aplikacji, która używa [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] nie jest obsługiwana za pomocą narzędzi do profilowania.  
  
## <a name="rule-description"></a>Opis reguły  
 To ostrzeżenie występuje, ponieważ narzędzi profilowania nie będzie można rozwiązać symboli dla kodu zarządzanego uruchomionego w aplikacji. Narzędzia profilowania nie można rozpoznać symboli zarządzanego kodu dla aplikacji, które są uruchomione [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)].  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Brak.