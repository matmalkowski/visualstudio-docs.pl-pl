---
title: "DA0022: Wysoki stopień odzyskiwania pamięci Gen 2 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.DA0022
- vs.performance.rules.DA0022
- vs.performance.22
ms.assetid: f871a547-0e6f-4b11-b2d7-174d30fc2ed8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2917ed46a32a6f726a5b484bb1d91e7e277854c1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="da0022-high-rate-of-gen-2-garbage-collections"></a>DA0022: Wysoki stopień odzyskiwania pamięci Gen 2
|||  
|-|-|  
|Identyfikator reguły|DA0022|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metoda profilowania|Wszystkie|  
|Komunikat|Istnieje stosunkowo wysokie tempo wyrzucania Gen 2 wystąpienia. Jeśli zgodnie z projektem, większość struktur danych programu są przydzielane i utrwalane na dłuższy czas, to nie jest zazwyczaj problem. Jednak w przypadku niezamierzonego to zachowanie aplikacji może być przypinanie obiektów. Jeśli nie masz pewności, możesz zbierać .NET pamięci alokacji danych i obiektów okres istnienia informacje Aby poznać wzorzec przydzielania pamięci, który korzysta z aplikacji.|  
|Typ reguły|Ostrzeżenie|  
  
 Gdy profilu można za pomocą próbkowania, pamięci platformy .NET lub metody kontencji zasobów, należy zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="cause"></a>Przyczyna  
 Dane o wydajności systemu, które zostały zebrane podczas profilowania wskazują, że znaczna część obiekty struktury for.NET pamięci została odzyskana podczas generowania 2 wyrzucanie elementów bezużytecznych w porównaniu do generacji 0 i 1 wyrzucania generacji.  
  
## <a name="rule-description"></a>Opis reguły  
 Program Microsoft .NET wspólnego języka środowiska wykonawczego (CLR) zapewnia mechanizm zarządzania automatyczne pamięci używane przez moduł Garbage Collector do odzyskać pamięci z obiektów, które nie jest już używane przez aplikację. Moduł zbierający elementy bezużyteczne to zorientowane na generowanie oparte na założeniu, że wiele są krótkim okresie. Zmienne lokalne, na przykład należy krótkim okresie. Nowo utworzone obiekty Uruchom podczas generowania 0 (gen 0), a następnie postępu na pokolenie 1 po ich przetrwać wyrzucanie elementów bezużytecznych Uruchom, a na koniec przejście do generacji 2 Jeśli aplikacja nadal używa ich.  
  
 Często i zazwyczaj bardzo wydajnie, są zebrane obiektów generacji 0. Obiekty w generacji 1 są zbierane rzadziej i mniej wydajne. Na koniec długotrwałe obiektów podczas generowania 2 powinny być gromadzone nawet rzadziej. Kolekcja generacji 2, czyli pełnego wyrzucania elementów bezużytecznych, uruchom również jest najbardziej kosztowna operacja.  
  
 Ta zasada uruchamiane w przypadku proporcjonalnie za dużo generacji 2 wyrzucania są wykonywane. Dobrze działające aplikacji .NET Framework ma więcej niż 5 razy jako wiele generacji 1 wyrzucania jako kolekcje generacji 2. (Prawdopodobnie idealne jest współczynnik 10 x).  
  
## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku znaczniki](../profiling/marks-view.md) danych profilowania. Znajdź **pamięci platformy .NET CLR\\# kolekcje pokolenia 0** i **pamięci platformy .NET CLR\\# pamięci Gen 1** kolumn. Określa, czy określone fazy wykonywania programu gdzie wyrzucanie elementów bezużytecznych występuje częściej. Porównanie tych wartości **% czasu potrzebnego na Odzyskiwanie** kolumny, aby zobaczyć, czy wzorzec przydziału pamięci zarządzanej powoduje nadmiernego pamięci nakład pracy osób.  
  
 Dużą część wyrzucania generacji 2 nie zawsze jest problem. Może to być zgodne z projektem. Aplikacja, która przydziela struktury dużej ilości danych, które muszą pozostać aktywne przez dłuższy czas podczas wykonywania mogą wyzwalać tę regułę. Podczas takiej aplikacji występuje duże wykorzystanie pamięci, mogą zostać zmuszeni do wykonywania częstych wyrzucania. Jeśli tańszego generacji 0 i wyrzucania generacja 1 można odzyskać tylko niewielką ilość zarządzane pamięci, zostanie zaplanowane częstsze wyrzucania generacji 2.  
  
 Istnieją dodatkowe kolumny pamięci platformy .NET CLR w widoku znaczniki, które mogą ułatwić identyfikację problemów kolekcji pamięci. **% Czasu potrzebnego na Odzyskiwanie** kolumny pomaga w zrozumieniu występuje nakład pracy ilość pamięci. Jeśli aplikacja używa zwykle dość niewielkiej liczby obiektów dużych, ale trwałe, następnie częste kolekcje generacji 2 nie może przekroczyć nadmiernej ilości czasu Procesora. Jeśli aplikacja jest wykorzystanie pamięci, ponieważ więcej pamięci fizycznej (RAM) jest wymagane, powiązanych reguł, które zwrócą **Pamięć\Strony/s** również mogą wyzwalać wartości w kolumnie.  
  
 Aby poznać wzorzec aplikacji użycia pamięci zarządzanej, będzie ponownie działać profilu alokacji pamięci a.NET profilu, a następnie wybierz okres istnienia obiektu profilowania opcji.  
  
 Aby dowiedzieć się, jak poprawić wydajność kolekcji pamięci, zobacz [podstawy modułu zbierającego elementy bezużyteczne i wskazówki dotyczące wydajności](http://go.microsoft.com/fwlink/?LinkId=148226) w witrynie sieci Web firmy Microsoft. Uzyskać informacji o obciążenie automatyczne odzyskiwanie pamięci, zobacz [niepokrytego sterty obiektu dużych](http://go.microsoft.com/fwlink/?LinkId=177836).