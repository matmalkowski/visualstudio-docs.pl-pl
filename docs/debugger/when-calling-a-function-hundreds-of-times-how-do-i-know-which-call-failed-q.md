---
title: Skąd wiadomo, gdy funkcja jest wywoływana setki razy, które wywołanie nie powiodło się? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.functions
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdae654dacf7c5965d51cc39f7970bd0347b9dcf
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056238"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Skąd wiadomo, gdy funkcja jest wywoływana setki razy, które wywołanie nie powiodło się?
## <a name="problem-description"></a>Opis problemu  
 Program nie powiedzie się na wywołanie funkcji `CnvtV`. Program prawdopodobnie wywołuje tą funkcją kilka kilkaset razy przed jej nie powiedzie się. Jeśli ustawić punkt przerwania lokalizacji na `CnvtV`, zatrzymuje program przy każdym wywołaniu tej funkcji i nie mają który. Nie wiem, jakie warunki powoduje wywołanie kończy się niepowodzeniem, dlatego nie można ustawić punktu przerwania warunkowego. Co mogę zrobić?  
  
## <a name="solution"></a>Rozwiązanie  
 Można ustawić punktu przerwania w funkcji z **liczba trafień** pola na wartość tak duży, że nigdy nie zostanie on osiągnięta. W takim przypadku ponieważ uważasz funkcji `CnvtV` nazywa się o kilka kilkaset razy, można ustawić **liczba trafień** do 1000 lub większej. Następnie uruchom program i poczekaj, aż to Niepowodzenie wywołania. Gdy nie powiedzie się, Otwórz okno punktów przerwania i przyjrzyj się na liście punktów przerwania. Punkt przerwania ustawiony na `CnvtV` pojawia się, że liczba trafień i liczby iteracji pozostałych:  
  
```cpp
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 Teraz wiesz, że funkcja nie powiodło się w wywołaniu 101st. Jeśli możesz zresetować przerwania z liczbą trafień od 101 i ponownie uruchom program program zatrzymuje się w wywołaniu `CnvtV` który spowodował niepowodzenie.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)   
 [Ustawianie punktów przerwania](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
