---
title: 'DA0024: Czas procesora CPU nadmierne GC | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.DA0024
- vs.performance.24
- vs.performance.rules.DA0024
ms.assetid: 228872da-77d0-4da5-b455-ac57fb1867c9
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 094175b329ffbb774d55566dd543795a3469e097
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="da0024-excessive-gc-cpu-time"></a>DA0024: Nadmierne wykorzystanie czasu GC CPU
|||  
|-|-|  
|Identyfikator reguły|DA0024|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metoda profilowania|Wszystkie|  
|Komunikat|% Czasu odzyskiwania pamięci jest bardzo duże. Brak nadmierne obciążenie kolekcji pamięci.|  
|Typ reguły|Ostrzeżenie|  
  
 Gdy profilu można za pomocą próbkowania, pamięci platformy .NET lub metody kontencji zasobów, należy zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="cause"></a>Przyczyna  
 Dane wydajności systemu, które zostały zebrane podczas profilowania wskazuje, czy czas poświęcony na wyrzucanie elementów bezużytecznych jest zbyt wysoka w porównaniu z aplikacji całkowity czas przetwarzania.  
  
## <a name="rule-description"></a>Opis reguły  
 Program Microsoft .NET wspólnego języka środowiska wykonawczego (CLR) zapewnia mechanizm zarządzania automatyczne pamięci używane przez moduł Garbage Collector do odzyskać pamięci z obiektów, które nie jest już używane przez aplikację. Moduł zbierający elementy bezużyteczne to zorientowane na generowanie oparte na założeniu, że wiele są krótkim okresie. Zmienne lokalne, na przykład należy krótkim okresie. Nowo utworzone obiekty Uruchom podczas generowania 0 (gen 0), a następnie postępu na pokolenie 1 po ich przetrwać wyrzucanie elementów bezużytecznych Uruchom, a na koniec przejście do generacji 2 Jeśli aplikacja nadal używa ich.  
  
 Często i zazwyczaj bardzo wydajnie, są zebrane obiektów generacji 0. Obiekty w generacji 1 są zbierane rzadziej i mniej wydajne. Na koniec długotrwałe obiektów podczas generowania 2 powinny być gromadzone nawet rzadziej. Kolekcja generacji 2, czyli pełnego wyrzucania elementów bezużytecznych, uruchom również jest najbardziej kosztowna operacja.  
  
 Ta zasada generowane, gdy czas spędzony w pamięci jest zbyt wysoka w porównaniu z czasem przetwarzania całkowita liczba aplikacji.  
  
> [!NOTE]
>  Gdy część czasu spędzony w pamięci jest ważna, ale nie nadmiernego w porównaniu z czasem przetwarzania całkowita liczba aplikacji [DA0023: czasu wysokiej GC CPU](../profiling/da0023-high-gc-cpu-time.md) uruchamiany ostrzeżenie zamiast tej reguły.  
  
## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczniki](../profiling/marks-view.md) danych profilowania. Znajdź **pamięci platformy .NET CLR\\% czasu potrzebnego na Odzyskiwanie** kolumny. Określa, czy określone fazy wykonywania programu obciążenie pamięci zarządzanej operacji wyrzucania elementów bezużytecznych w przypadku większych niż inne faz. Porównaj wartości wartości % czasu odzyskiwania pamięci na stopień wyrzucania elementów bezużytecznych zgłoszone w **# kolekcje pokolenia 0**, **# pamięci Gen 1**, **# pamięci Gen 2** wartości .  
  
 Czas w wartości GC (%) próbuje ilość czasu, jaki aplikacja zużywa wykonywania wyrzucanie elementów bezużytecznych proporcjonalny do sumy przetwarzania raportu. Należy pamiętać, że istnieją okoliczności, gdy czas w wartości GC (%) może raportować bardzo wysokiej wartości, ale nie jest z powodu nadmiernego wyrzucanie elementów bezużytecznych. Aby uzyskać więcej informacji o sposobie czas wartości GC (%) jest obliczane, zobacz [różnica między wydajności dane zgłoszone przez różnych narzędzi - 4](http://go.microsoft.com/fwlink/?LinkId=177863) wpisu **Weblog w Maoni** w witrynie MSDN. Jeśli występują błędy strony lub aplikacji są zastępowane przez inne wyższy priorytet pracy na komputerze podczas wyrzucania elementów bezużytecznych, czas licznika GC (%), zostaną one zastosowane te dodatkowe opóźnienia.