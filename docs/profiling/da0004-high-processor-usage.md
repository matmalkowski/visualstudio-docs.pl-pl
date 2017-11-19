---
title: "DA0004: Znaczące wykorzystanie czasu procesora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5eeb6d43ff388050ad9c1fa8140f2e6bdfb352ac
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 Użycie procesora (CPU) był znacznie wysoki w profilowania dane zebrane przy użyciu metody instrumentacji. Należy rozważyć użycie próbki metoda profilowania, gdy profilowanie procesora CPU powiązana aplikacji.  
  
## <a name="rule-description"></a>Opis reguły  
 W tym przebiegu profilowania były stale bardzo zajęty procesora (lub procesorów). Wysokie użycie procesora CPU może wskazywać aplikacji procesora. Instrumentowanych profile nie są zwykle najbardziej efektywny sposób zbadać scenariuszy użycia procesora CPU. Próbkowanie jest zazwyczaj bardziej skuteczne, gdy są profilowanie aplikacji, które poświęcać dużo czasu wykonywania instrukcji na procesor.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Należy rozważyć profilowania aplikację ponownie przy użyciu metody próbkowania zamiast metody instrumentacji, chyba że wymagają funkcji chronometrażu lub więcej planuje się opis wejścia/wyjścia niż wąskich gardeł.