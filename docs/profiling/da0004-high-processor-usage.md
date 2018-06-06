---
title: 'DA0004: Znaczące wykorzystanie czasu procesora | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5800acfded9d500c68a0e071ffa6501d6b3c77e
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749613"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Znaczące wykorzystanie czasu procesora
|||  
|-|-|  
|Identyfikator reguły|DA0004|  
|Kategoria|Użycie narzędzia profilowania|  
|Metod profilowania|Oprzyrządowanie<br /><br /> Pobierania próbek|  
|Komunikat|Użycie procesora jest stale powyżej 75%. Rozważ użycie trybu próbkowania dla aplikacji powiązanych z Procesora.|  
|Typ reguły|Informacje|  
  
 Gdy profilu można za pomocą próbkowania, pamięci platformy .NET lub metody kontencji zasobów, należy zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="cause"></a>Przyczyna  
 Użycie procesora (CPU) jest wysoka w profilowania dane zebrane przy użyciu metody instrumentacji. Należy rozważyć użycie próbki metoda profilowania, gdy profilowanie procesora CPU powiązana aplikacji.  
  
## <a name="rule-description"></a>Opis reguły  
 W tym przebiegu profilowania procesor (lub procesorów) jest stale zajęte. Wysokie użycie procesora CPU może wskazywać aplikacji procesora. Instrumentowanych profile nie są najbardziej efektywny sposób zbadać scenariuszy użycia procesora CPU. Próbkowanie jest bardziej efektywne, gdy są profilowanie aplikacji, które poświęcać dużo czasu wykonywania instrukcji na procesor.  
  
## <a name="how-to-fix-violations"></a>Jak rozwiązać naruszeń  
 Należy rozważyć profilowania aplikację ponownie przy użyciu metody próbkowania zamiast metody instrumentacji, chyba że wymagają funkcji chronometrażu lub więcej planuje się opis wejścia/wyjścia niż wąskich gardeł.