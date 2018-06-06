---
title: 'DA0008: Kilka przykładów zbierane | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13065ac4b55b8ae84d299aa15eeb184e7d864d2e
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749817"
---
# <a name="da0008-few-samples-collected"></a>DA0008: Kilka zebranych przykładów
|||  
|-|-|  
|Identyfikator reguły|DA0008|  
|Kategoria|Użycie narzędzia profilowania|  
|Metoda profilowania|Pobierania próbek|  
|Komunikat|Zebrano tylko kilka przykładów. Należy wziąć pod uwagę dłużej przebiegu lub zwiększenie próbkowania dla uzyskania bardziej znaczących wyników.|  
|Typ reguły|Informacje|  
  
## <a name="cause"></a>Przyczyna  
 Kilka przykładów zostały zebrane w przebiegu profilowania.  
  
## <a name="rule-description"></a>Opis reguły  
 Gdy używana jest metoda pobierania próbek, należy zebrać statystycznie duża liczba próbek, aby upewnić się, że dane reprezentują zachowanie rzeczywistych program. Aby zminimalizować próbkowania błędów, należy zebrać co najmniej 1000 przykłady sposób wykonywania instrukcji programu. Jeśli nie zbieraj wystarczającej liczby próbek, można możesz błąd podczas analizowania danych profilowania.  
  
## <a name="how-to-fix-violations"></a>Jak rozwiązać naruszeń  
 Należy wziąć pod uwagę profilowania już uruchamiania aplikacji lub użycie zwiększenia częstotliwości próbkowania w celu uzyskania statystycznie znaczących wyników. Aby dowiedzieć się, jak zmienić częstotliwość próbkowania w środowisku IDE programu Visual Studio, zobacz [porady: Wybieranie zdarzeń pobierania próbek](../profiling/how-to-choose-sampling-events.md). Aby uzyskać więcej informacji o sposobie zmienić częstotliwość próbkowania, korzystając z wiersza polecenia narzędzi profilowania, zobacz [czasomierza](../profiling/timer.md) w [VSPerfCmd](../profiling/vsperfcmd.md) odwołania.