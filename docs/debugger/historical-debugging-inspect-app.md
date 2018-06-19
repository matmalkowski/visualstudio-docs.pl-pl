---
title: Sprawdź aplikację z debugowania historycznego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6a8e4ec27c73516d2eb4ea79ee8beee91dfd19c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476825"
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio"></a>Sprawdź aplikację z programem IntelliTrace historical debugowania w programie Visual Studio
Można użyć [debugowania historycznego](../debugger/historical-debugging.md) do tyłu i do przodu przez wykonanie aplikacji i sprawdzić jego stan.  
  
Można użyć funkcji IntelliTrace w Visual Studio Enterprise edition, ale nie wersji Professional lub społeczności.  
  
## <a name="navigate-your-code-with-historical-debugging"></a>Przejdź do kodu za pomocą debugowania historycznego  
 Zacznijmy prosty program, który ma usterki. W języku C# aplikacji konsoli Dodaj następujący kod:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    int resultInt = AddAll(testInt);  
    Console.WriteLine(resultInt);  
}  
private static int AddAll(int j)  
{  
    for (int i = 0; i < 20; i++)  
    {  
        j = AddInt(j);  
    }  
    return j;  
}  
  
private static int AddInt(int add)  
{  
    if (add == 10)  
    {  
        return add += 25;  
    }  
    return ++add;  
}  
```  
  
 Będzie przyjęto założenie, że wartość oczekiwana `resultInt` po wywołaniu `AddAll()` wynosi 20 (zwiększanie wyniku `testInt` 20 razy). (Przyjmiemy również, że nie widać błędów w `AddInt()`). Ale wynik jest rzeczywiście 44. Jak możemy znaleźć usterki bez krokowe `AddAll()` 10 razy? Możemy użyć debugowania historycznego, aby znaleźć usterki szybsze i łatwiejsze. Oto jak:  
  
1.  W **Narzędzia > Opcje > IntelliTrace > Ogólne**, upewnij się, że funkcja IntelliTrace jest włączona i wybierz **zdarzeń funkcji IntelliTrace i informacji o wywołaniach**. Jeśli nie zaznaczysz tej opcji, nie można wyświetlić trasę nawigacji (jak wyjaśniono poniżej).  
  
2.  Ustaw punkt przerwania na `Console.WriteLine(resultInt);` wiersza.  
  
3.  Rozpocznij debugowanie. Wykonuje kod do punktu przerwania. W **zmiennych lokalnych** okna, można stwierdzić, że wartość `resultInt` jest 44.  
  
4.  Otwórz **narzędzia diagnostyczne** okna (**Debuguj > Pokaż narzędzia diagnostyczne**). W oknie Kod powinien wyglądać następująco:  
  
     ![W oknie Kod na punkt przerwania](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5.  Powinny pojawić się podwójną strzałkę obok lewy margines, nad punktu przerwania. Ten obszar jest nazywany trasę nawigacji i jest używana do debugowania historycznego. Kliknij strzałkę.  
  
     W oknie Kod powinien zostać wyświetlony który poprzedni wiersz kodu (`int resultInt = AddIterative(testInt);`) jest pokolorowane różowy. Nad oknem powinien zostać wyświetlony komunikat, którego jesteś teraz z debugowania historycznego.  
  
     W oknie Kod teraz wygląda następująco:  
  
     ![Okno kodu w trybie debugowania historycznego](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6.  Teraz można przejść do `AddAll()` — metoda (**F11**, lub **Step Into** przycisk w trasę nawigacji. Krok do przodu (**F10**, lub **przejdź do następnego wywołania** w trasę nawigacji. Różowa linia jest teraz na `j = AddInt(j);` wiersza. **F10** w takim przypadku nie krok do następnego wiersza kodu. Zamiast tego kroki do następnego wywołania funkcji. Debugowanie historyczne przechodzi z wywołaniami i pomija wiersze kodu, które nie zawierają wywołania funkcji.  
  
7.  Teraz Wkrocz `AddInt()` metody. W tym kodzie błędu powinna zostać wyświetlona natychmiast.  

## <a name="next-steps"></a>Następne kroki

Ta procedura wewnętrzna właśnie powierzchni co można zrobić z debugowania historycznego.

- Aby wyświetlić migawki podczas debugowania, zobacz [wyświetlić migawki IntelliTrace krok zwrotnego pomocą](../debugger/how-to-use-intellitrace-step-back.md).
- Aby dowiedzieć się więcej o różnych ustawieniach i efekty różnych przycisków w trasę nawigacji, zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md).