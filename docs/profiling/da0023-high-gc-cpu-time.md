---
title: 'DA0023: Wysokie GC CPU czasu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0023
- vs.performance.23
- vs.performance.rules.DA0023
ms.assetid: aba875fe-9cbc-418d-a2c4-6eb47519a5bb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1509c4fda8759e3ad8dece654921fc56b8b9c2e7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="da0023-high-gc-cpu-time"></a>DA0023: Wysokie wykorzystanie czasu GC CPU
|||  
|-|-|  
|Identyfikator reguły|DA0023|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metoda profilowania|Wszystkie|  
|Komunikat|% Czasu odzyskiwania pamięci jest stosunkowo wysokie. Wskazuje to na nadmierne ilości pamięci kolekcji obciążenie może mieć wpływ na czas odpowiedzi aplikacji. Możesz zbierać .NET pamięci alokacji danych i obiektów okres istnienia informacje Aby poznać wzorzec przydzielania pamięci, którą aplikacja korzysta z lepiej.|  
|Typ reguły|Informacyjny|  
  
 Gdy profilu można za pomocą próbkowania, pamięci platformy .NET lub metody kontencji zasobów, należy zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="cause"></a>Przyczyna  
 Dane wydajności systemu, które są zbierane podczas profilowania oznacza ilość czasu przeznaczonego na wyrzucanie elementów bezużytecznych — w znaczący w porównaniu z czasem przetwarzania całkowita liczba aplikacji.  
  
## <a name="rule-description"></a>Opis reguły  
 Program Microsoft .NET wspólnego języka środowiska wykonawczego (CLR) zapewnia mechanizm zarządzania automatyczne pamięci używane przez moduł Garbage Collector do odzyskać pamięci z obiektów, które nie jest już używane przez aplikację. Moduł zbierający elementy bezużyteczne to zorientowane na generowanie oparte na założeniu, że wiele są krótkim okresie. Zmienne lokalne, na przykład należy krótkim okresie. Nowo utworzone obiekty Uruchom podczas generowania 0 (gen 0), a następnie postępu na pokolenie 1 po ich przetrwać wyrzucanie elementów bezużytecznych Uruchom, a na koniec przejście do generacji 2 Jeśli aplikacja nadal używa ich.  
  
 Często i zazwyczaj bardzo wydajnie, są zebrane obiektów generacji 0. Obiekty w generacji 1 są zbierane rzadziej i mniej wydajne. Na koniec długotrwałe obiektów podczas generowania 2 powinny być gromadzone nawet rzadziej. Kolekcja generacji 2, czyli pełnego wyrzucania elementów bezużytecznych, uruchom również jest najbardziej kosztowna operacja.  
  
 Ta zasada generowane, gdy ilość czasu przeznaczonego na wyrzucanie elementów bezużytecznych — w porównaniu z aplikacji całkowity czas przetwarzania jest znacząca.  
  
> [!NOTE]
>  Gdy część czasu poświęcana w pamięci jest nadmierne w porównaniu z aplikacji całkowity czas przetwarzania, [DA0024: nadmierne wykorzystanie czasu GC CPU](../profiling/da0024-excessive-gc-cpu-time.md) uruchamiany ostrzeżenie zamiast tej reguły.  
  
## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczniki](../profiling/marks-view.md) danych profilowania. Znajdź **pamięci platformy .NET CLR\\% czasu potrzebnego na Odzyskiwanie** kolumny. Określa, czy określone fazy wykonywania programu obciążenie pamięci zarządzanej operacji wyrzucania elementów bezużytecznych w przypadku większych niż inne faz. Porównaj wartości wartości % czasu odzyskiwania pamięci na stopień wyrzucania elementów bezużytecznych zgłoszone w **# kolekcje pokolenia 0**, **# pamięci Gen 1**, **# pamięci Gen 2** wartości .  
  
 Czas w wartości GC (%) próbuje ilość czasu, jaki aplikacja zużywa wykonywania wyrzucanie elementów bezużytecznych proporcjonalny do sumy przetwarzania raportu. Należy pamiętać, że istnieją okoliczności, gdy czas w wartości GC (%) może raportować bardzo wysokiej wartości, ale nie jest z powodu nadmiernego wyrzucanie elementów bezużytecznych. Aby uzyskać więcej informacji o sposobie czas wartości GC (%) jest obliczane, zobacz [różnica między wydajności dane zgłoszone przez różnych narzędzi - 4](http://go.microsoft.com/fwlink/?LinkId=177863) wpisu **Weblog w Maoni** w witrynie MSDN. Jeśli występują błędy strony lub aplikacji są zastępowane przez inne wyższy priorytet pracy na komputerze podczas wyrzucania elementów bezużytecznych, czas licznika GC (%), zostaną one zastosowane te dodatkowe opóźnienia.