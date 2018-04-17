---
title: Widok modułów - dane próbkowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
- sampling profiling method,Modules view
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 80bb263f395930b77ff31cbc68f4f9695879756a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="modules-view---sampling-data"></a>Widok modułów - dane próbkowania
Widok modułów pobierania próbek danych wydajności wyświetla dane są grupowane według modułów, które zostały poddane próbkowaniu w danych profilowania. Każdy moduł jest katalogiem głównym drzewa hierarchicznej. Próbki funkcji modułu są wyświetlane poniżej tego węzła modułu.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Jeśli funkcja została uruchomiona po przykłady zostały zebrane (oznacza to, że funkcja znajdowała się w górnej części stosu wywołań), wierszy źródłowych i adresy instrukcji, które były wykonywane są wymienione poniżej tego węzła funkcji. Ponieważ dane są gromadzone dla wiersza źródłowego lub wskaźnik instrukcji, gdy wiersz lub instrukcji jest wykonywany, wartości włącznie i wyłącznego są zawsze takie same dla wiersza danych i instrukcji danych.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa modułu, funkcji, numer wiersza lub adres wskaźnika instrukcji.|  
|**Identyfikator procesu**|Identyfikator PID profilowania Uruchom proces.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Nazwa modułu**|Nazwa modułu, w którym znajduje się wskaźnik funkcji, wiersz lub instrukcji.|  
|**Ścieżka modułu**|Ścieżka modułu, w którym znajduje się wskaźnik modułu, funkcji, wiersz lub instrukcji.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
|**Numer wiersza — funkcja**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Przykłady włącznie**|— Dla funkcji liczba próbek, w których ta funkcja lub funkcji, która została wywołana przez tę funkcję było wykonywane; oznacza to, że liczba wywołań stosu Przykłady, które zawierały tej funkcji.<br />— Dla modułu liczba próbek w funkcji co najmniej jeden z modułu wykonywania.<br />— Dla wiersza lub instrukcji, liczba próbek w którym ten wiersz lub instrukcji wykonywania.|  
|**% Próbek włącznie**|— W przypadku funkcji lub moduł wartość procentowa próbek wszystkie, w którym profilowania były przykłady włącznie tej funkcji lub modułu.<br />— Dla wiersza lub instrukcji wartość procentowa próbek wszystkich w profilowania Uruchom, w którym ten wiersz lub instrukcja powodowała.|  
|**Wyłącznych próbek**|— Dla funkcji liczbę wywołań stosu próbek, w których ta funkcja bezpośrednio było wykonywane; oznacza to, liczba próbek, w których ta funkcja została u góry stosu wywołań.<br />— Dla modułu sumę wyłącznych próbek funkcji w module.<br />— Dla wiersza lub instrukcji, liczba próbek w którym ten wiersz lub instrukcji wykonywania.|  
|**% Wyłącznych próbek**|— W przypadku funkcji lub moduł wartość procentowa próbek wszystkie, w którym profilowania były wyłącznych próbek w tej funkcji lub modułu.<br />— Dla wiersza lub instrukcji wartość procentowa próbek wszystkich w profilowania Uruchom, w którym ten wiersz lub instrukcja powodowała.|  
  
## <a name="see-also"></a>Zobacz też  
 [Moduły View - próbkowanie](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Widok modułów - Instrumentacja](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Widok modułów](../profiling/modules-view-instrumentation-data.md)