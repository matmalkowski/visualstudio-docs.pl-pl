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
ms.openlocfilehash: f6ab40efbba692cfa85f14b750d3c853d1112704
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765742"
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
  
## <a name="how-to-fix-violations"></a>Jak rozwiązać naruszeń  
 Brak.