---
title: 'DA0004: Znaczące wykorzystanie czasu procesora | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: b5a1c001a5a0f23d008345ebd5f0c228c166c49f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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