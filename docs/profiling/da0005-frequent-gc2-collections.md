---
title: "DA0005: Częste kolekcje GC2 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.DA0005
- vs.performance.rules.DAManyGC2Collections
- vs.performance.5
- vs.performance.rules.DA0005
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a8b529672868ac2ad3b8d1a9dd7faaeaefb98084
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="da0005-frequent-gc2-collections"></a>DA0005: Częste kolekcje GC2
|||  
|-|-|  
|RuleId|DA0005|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metoda profilowania|Pamięci platformy .NET|  
|Komunikat|Wiele obiektów podlega odzyskiwaniu w generacji 2 wyrzucanie elementów bezużytecznych.|  
|Typ komunikatu|Ostrzeżenie|  
  
## <a name="cause"></a>Przyczyna  
 Duża liczba obiektów pamięci .NET jest odzyskane w generacji 2 wyrzucanie elementów bezużytecznych.  
  
## <a name="rule-description"></a>Opis reguły  
 Program Microsoft .NET środowisko uruchomieniowe języka wspólnego (CLR) zapewnia mechanizm zarządzania automatyczne pamięci używane przez moduł Garbage Collector do odzyskać pamięci z obiektów, które nie jest już używane przez aplikację. Moduł zbierający elementy bezużyteczne to zorientowane na generowanie oparte na założeniu, że wiele są krótkim okresie. Zmienne lokalne, na przykład należy krótkim okresie. Nowo utworzone obiekty Uruchom podczas generowania 0 (gen 0), a następnie postępu na pokolenie 1 po ich przetrwać wyrzucanie elementów bezużytecznych Uruchom, a na koniec przejście do generacji 2 Jeśli aplikacja nadal używa ich.  
  
 Często i zazwyczaj bardzo wydajnie, są zebrane obiektów generacji 0. Obiekty w generacji 1 są zbierane rzadziej i mniej wydajne. Na koniec długotrwałe obiektów podczas generowania 2 powinny być gromadzone nawet rzadziej. Kolekcja generacji 2, czyli pełnego wyrzucania elementów bezużytecznych, uruchom również jest najbardziej kosztowna operacja.  
  
 Ta zasada uruchamiane w przypadku proporcjonalnie za dużo generacji 2 wyrzucania wystąpiły. Jeśli zbyt wiele obiektów względnie krótkim okresie przetrwać kolekcji generacji 1, ale będą w stanie mają być zbierane w kolekcji pełne generacji 2, kosztów zarządzania pamięci można łatwo stają się nadmierne. Aby uzyskać więcej informacji, zobacz [kryzysami Średni czas życia](http://go.microsoft.com/fwlink/?LinkId=177835) post na informacje o wydajności Rico Mariani technologii w witrynie MSDN.  
  
## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Przegląd [widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md) raporty, aby poznać wzorce przydzielania pamięci aplikacji. Użyj [widok okresu istnienia obiektu](../profiling/object-lifetime-view.md) umożliwia określenie, które obiekty są zachowane w generacji 2, a następnie odzyskać z niego danych tego programu. Użyj [Widok alokacji](../profiling/dotnet-memory-allocations-view.md) można ustalić ścieżki wykonywania, które spowodowały tych przydziałów.  
  
 Aby dowiedzieć się, jak poprawić wydajność kolekcji pamięci, zobacz [podstawy modułu zbierającego elementy bezużyteczne i wskazówki dotyczące wydajności](http://go.microsoft.com/fwlink/?LinkId=148226) w witrynie sieci Web firmy Microsoft. Uzyskać informacji o obciążenie automatyczne odzyskiwanie pamięci, zobacz [niepokrytego sterty obiektu dużych](http://go.microsoft.com/fwlink/?LinkId=177836).