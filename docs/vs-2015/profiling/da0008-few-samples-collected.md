---
title: 'DA0008: Zebrano kilka próbek | Dokumentacja firmy Microsoft'
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
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 205bedf2baa7c9fa1e1c5f40ccbaa4041427074b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680520"
---
# <a name="da0008-few-samples-collected"></a>DA0008: Kilka zebranych przykładów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [DA0008: zebrano kilka próbek](https://docs.microsoft.com/visualstudio/profiling/da0008-few-samples-collected).  
  
Identyfikator reguły | DA0008 |  
| Kategoria | Profilowanie użycia narzędzia |  
| Metoda profilowania | Próbkowanie |  
| Komunikat | Zebrano tylko kilka przykładów. Należy wziąć pod uwagę dłużej przebiegu lub zwiększenie częstotliwości próbkowania dla uzyskania bardziej znaczących wyników. |  
| Typ reguły | Informacji |  
  
## <a name="cause"></a>Przyczyna  
 Kilka przykładów zostały zebrane podczas uruchomienia profilowania.  
  
## <a name="rule-description"></a>Opis reguły  
 Gdy używana jest metoda pobierania próbek, należy zbierać są statystycznie istotne liczba próbek, aby upewnić się, że dane reprezentują program rzeczywiste zachowanie. Aby zminimalizować błędy pobierania próbek, należy spróbować zbieranie co najmniej 1000 próbek zachowanie wykonania instrukcji programu. Jeśli nie zbieraj, wystarczająco dużo próbki, można możesz błąd podczas analizowania danych profilowania.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Należy wziąć pod uwagę profilowania już wykonywania aplikacji lub za pomocą próbkowania szybciej uzyskać wyniki są statystycznie istotne. Aby dowiedzieć się, jak zmienić częstotliwość próbkowania w środowisku IDE programu Visual Studio, zobacz [porady: Wybieranie zdarzeń próbkowania](../profiling/how-to-choose-sampling-events.md). Aby uzyskać więcej informacji o tym, jak zmienić częstotliwość próbkowania, korzystając z wiersza polecenia Profiling Tools, zobacz [czasomierza](../profiling/timer.md) w [VSPerfCmd](../profiling/vsperfcmd.md) odwołania.



