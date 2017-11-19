---
title: "DA0018: limitach pamięci zarządzanych aplikacji 32-bitowych uruchomionej w procesie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.18
- vs.performance.DA0018
- vs.performance.rules.DA0018
ms.assetid: 98eb2d96-f92f-42f9-915c-e5ac2330ffbf
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b48ca72793528be42f1fa4a2af674bd76d3d684a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="da0018-32-bit-application-running-at-process-managed-memory-limits"></a>DA0018: aplikacja 32-bitowa działająca w limitach pamięci zarządzanych przez proces
|||  
|-|-|  
|Identyfikator reguły|DA0018|  
|Kategoria|Użycie narzędzia profilowania|  
|Metoda profilowania|Pobierania próbek|  
|Komunikat|Zarządzane zbliża się domyślny limit dla procesu 32-bitowego alokacji pamięci. Aplikacja może być zależna od pamięci.|  
|Typ reguły|Ostrzeżenie|  
  
 Gdy profilu można za pomocą próbkowania, pamięci platformy .NET lub metody kontencji zasobów, należy zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="cause"></a>Przyczyna  
 System dane zebrane podczas przebiegu profilowania wskazuje, że pamięci .NET Framework sterty osiągnięciu maksymalnego rozmiaru zarządzanych stosów może nawiązać połączenie w procesie 32-bitowych. Ten maksymalny rozmiar to wartość domyślna. Jest on oparty na łączną ilość przestrzeni adresowej procesu, który można przydzielić bajtów prywatnych. Zgłaszana wartość to maksimum zaobserwowane wartość stosach z gdy była aktywna PROFILOWANEGO procesu. Należy rozważyć profilowanie ponownie przy użyciu metody profilowania pamięci .NET i optymalizacji wykorzystania zasobów zarządzanych przez aplikację.  
  
 Gdy rozmiar zarządzanej sterty podejścia domyślny limit, proces zbierania automatyczne odzyskiwanie może być konieczne wywoływanej częściej. Powoduje to zwiększenie obciążenia zarządzania pamięcią.  
  
 Reguła generowane tylko dla 32-bitowych aplikacji uruchomionych na maszynach 32-bitowych.  
  
## <a name="rule-description"></a>Opis reguły  
 Program Microsoft .NET wspólnego języka środowiska wykonawczego (CLR) zapewnia mechanizm zarządzania automatyczne pamięci używane przez moduł Garbage Collector do odzyskać pamięci z obiektów, które nie jest już używane przez aplikację. Moduł zbierający elementy bezużyteczne to zorientowane na generowanie oparte na założeniu, że wiele są krótkim okresie. Zmienne lokalne, na przykład należy krótkim okresie. Nowo utworzone obiekty Uruchom podczas generowania 0 (gen 0), a następnie postępu na pokolenie 1 po ich przetrwać wyrzucanie elementów bezużytecznych Uruchom, a na koniec przejście do generacji 2 Jeśli aplikacja nadal używa ich.  
  
 Zarządzane obiekty, które są większe niż 85 KB są przydzielone sterty dużych obiektów, gdy są dłuższe interwały wyrzucanie elementów bezużytecznych i kompaktowanie niż mniejsze obiektów. duże obiekty są zarządzane oddzielnie, ponieważ zakłada się, że znajdują się większą trwałość i ponieważ połączenie trwałe i duże obiekty o często przydzielone obiekty mniejszych może utworzyć rzutowania najgorszy fragmentacji sterty.  
  
 Ponieważ całkowity rozmiar zarządzanej sterty podejścia domyślny limit, obciążenie zarządzania pamięcią zwykle zwiększa do punktu, w którym można uruchomić wpłynąć na elastyczność i skalowalność aplikacji.  
  
## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [znaczniki](../profiling/marks-view.md) widoku. Znajdź **pamięci platformy .NET CLR\\# bajtów we wszystkich Stertach** i **# łączna liczba zadeklarowanych bajtów** kolumn. Określa, czy określone fazy wykonywania programu przydział pamięci zarządzanej w przypadku większych niż inne faz. Porównaj wartości **# bajtów we wszystkich Stertach** kolumny, która ma stopień wyrzucania elementów bezużytecznych zgłoszone w **pamięci platformy .NET CLR\\# kolekcje pokolenia 0**, **.NET CLR pamięci\\# pamięci Gen 1**, i **pamięci platformy .NET CLR\\# pamięci Gen 2** kolumny w celu określenia, jeśli wzorzec przydziału pamięci zarządzanej wpływa na szybkość pamięci Kolekcja.  
  
 W przypadku aplikacji .NET Framework środowisko uruchomieniowe języka wspólnego ogranicza całkowity rozmiar zarządzanej sterty celu nieco mniejsze niż połowa maksymalny rozmiar prywatnego obszaru część przestrzeni adresowej procesu. Dla procesów 32-bitowy, uruchomione na komputerze 32-bitowy 2 GB reprezentuje górny limit prywatna część przestrzeni adresowej procesu. Całkowity rozmiar zarządzanego stosów po rozpoczęciu z rozwiązań jego domyślny limit, może zwiększyć koszty zarządzanie pamięcią i może obniżyć wydajność aplikacji.  
  
 Jeśli pamięci zarządzanej nadmierne obciążenie problem, należy rozważyć jednej z dwóch opcji:  
  
-   Optymalizacja użycia aplikacji zasobów pamięci zarządzanej  
  
     —lub—  
  
-   sposób, aby zwolnić architektury ograniczenia dotyczące maksymalny rozmiar pamięci wirtualnej dla procesu 32-bitowego  
  
 Aby zoptymalizować użycie zasobów pamięci zarządzanej aplikacji, zbieranie danych przydziału pamięci zarządzanej w alokacji pamięci .NET profilowania, uruchom. Przegląd [widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md) raporty, aby poznać wzorce przydzielania pamięci aplikacji.  
  
 Użyj [widok okresu istnienia obiektu](../profiling/object-lifetime-view.md) umożliwia określenie, które obiekty są zachowane w generacji, a następnie odzyskać z niego danych tego programu.  
  
 Użyj [Widok alokacji](../profiling/dotnet-memory-allocations-view.md) można ustalić ścieżki wykonywania, które spowodowały tych przydziałów.  
  
 Aby uzyskać więcej informacji o sposobie poprawić wydajność zbierania danych pamięci, zobacz artykułu technicznego na .NET Framework, [podstawy modułu zbierającego elementy bezużyteczne i wskazówki dotyczące wydajności](http://go.microsoft.com/fwlink/?LinkId=177946) w witrynie MSDN.  
  
 Aby uzyskać architektury zwolnienia z ograniczeń pamięci wirtualnej na rozmiar prywatna część przestrzeni adresowej procesu, spróbuj uruchomienie tego procesu 32-bitowych na komputerze 64-bitowych.  Proces 32-bitowy, na komputerze 64-bitowe mogą uzyskiwać do 4 GB pamięci wirtualnej prywatnych.  
  
 64-bitowych procesu uruchomionego na komputerze 64-bitowych mogą uzyskiwać do 8 TB pamięci wirtualnej. Rozważ ponowną kompilację aplikacji do wykonywania jako natywnych aplikacji 64-bitowych. Ta zasada jest wyłącznie do celów informacyjnych i nie może wymagać działań korygujących.