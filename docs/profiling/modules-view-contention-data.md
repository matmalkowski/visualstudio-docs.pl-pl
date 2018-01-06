---
title: "Widok modułów - dane Kontencji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Modules view
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5503422ece5847018e8d321dba9cf674dff9e623
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="modules-view---contention-data"></a>Widok modułów - dane Kontencji
Widok modułów danych kontencji współbieżności dane są pogrupowane według modułów, które zostały poddane próbkowaniu w danych profilowania. Każdy moduł jest katalogiem głównym drzewa hierarchicznej. Funkcji modułu, w którym wystąpił zdarzenia rywalizacji są wyświetlane w węźle modułu.  
  
 Jeśli funkcja została uruchomiona własny kod po wystąpieniu zdarzenia rywalizacji, oznacza to, funkcja znajdowała się u góry stosu wywołań, wierszy źródłowych i instrukcji się, że adresy, które były wykonywane są wyświetlane w węźle funkcji. Ponieważ dane są gromadzone dla wiersza źródłowego lub wskaźnik instrukcji, gdy wiersz lub instrukcji jest wykonywany, wartości włącznie i wyłącznego są zawsze takie same dla wiersza danych i instrukcji danych.  
  
 W poniższej tabeli opisano wartości kolumn w widoku moduły danych rywalizacji.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Wyłączny czasu blokowania**|— Dla funkcji, czasu, która to funkcja została zablokowana wykonywanie kodu w treści funkcji. Czas blokowania w funkcje, które zostały wywołane przez funkcję nie jest włączony.<br />— Dla modułu sumę własny czas zablokowanych funkcji w module.<br />— Dla wiersza lub instrukcji, podczas tego wiersza lub wykonywania instrukcji został zablokowany.|  
|**% Wyłącznego czasu blokowania**|-Modułu lub funkcji odsetek wszystkich czas blokowania w przebiegu, który profilowania zostało wyłączne czas blokowania w tej funkcji lub modułu.<br />— Dla wiersza lub instrukcji procent wszystkich czasu blokowania w przebiegu profilowania, w którym ten wiersz lub instrukcji zostało zablokowane z wykonywania.|  
|**Wyłączny rywalizacji**|— Dla funkcji, ile razy tej funkcji została zablokowana wykonywanie kodu w treści funkcji. Rywalizacji w funkcjach, które zostały wywołane przez funkcję nie są uwzględniane.<br />— Dla modułu sumę wyłącznego rywalizacji funkcji w module.<br />— Dla wiersza lub instrukcji, ile razy tego wiersza lub instrukcji zostało zablokowane z wykonywania.|  
|**% Wyłącznego rywalizacji**|— Dla modułu lub funkcji wartość procentowa rywalizacji wszystkie, w którym profilowania były wyłącznego rywalizacji tej funkcji lub modułu.<br />— Dla wiersza lub instrukcji wartość procentowa rywalizacji wszystkie, w którym profilowania były rywalizacji, dla których blokowany dostęp do tego wiersza lub wykonywania instrukcji.|  
|**Całkowity czas blokowania**|— Dla funkcji podczas tej funkcji lub funkcja, która została wywołana przez tę funkcję zostało zablokowane z wykonywania.<br />— Dla modułu Suma zablokowanych czasu, w których co najmniej jedna funkcja ten moduł został na stosie.<br />— Dla wiersza lub instrukcji, podczas tego wiersza lub wykonywania instrukcji został zablokowany.|  
|**Całkowity czas blokowania %**|-Funkcji lub moduł odsetek wszystkich czas blokowania w przebiegu, który profilowania zostało całkowity czas blokowania w tej funkcji lub modułu.<br />— Dla wiersza lub instrukcji odsetek wszystkich czas blokowania w profilowania uruchomione w którym ten wiersz lub instrukcji wykonywania.|  
|**Wraz z wartościami granicznymi rywalizacji**|— Dla funkcji, ile razy tej funkcji lub funkcja, która została wywołana przez tę funkcję zostało zablokowane z wykonywania.<br />— Dla modułu liczba rywalizacji mających, w których co najmniej jedna funkcja ten moduł został na stosie.<br />— Dla wiersza lub instrukcji, ile razy tego wiersza lub instrukcji zostało zablokowane z wykonywania.|  
|**% Rywalizacji włącznie**|— Dla modułu lub funkcji wartość procentowa rywalizacji wszystkie, w którym profilowania były rywalizacji włącznie tej funkcji lub modułu.<br />— Dla wiersza lub instrukcji odsetek wszystkich czas blokowania w profilowania uruchomione w którym ten wiersz lub instrukcji wykonywania.|  
|**Numer wiersza — funkcja**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Nazwa modułu**|Nazwa modułu, w którym znajduje się wskaźnik funkcji, wiersz lub instrukcji.|  
|**Ścieżka modułu**|Ścieżka modułu, w którym znajduje się wskaźnik modułu, funkcji, wiersz lub instrukcji.|  
|**Nazwa**|Nazwa modułu lub funkcji.|  
|**Identyfikator procesu**|Identyfikator PID profilowania Uruchom proces.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok modułów](../profiling/modules-view.md)   
 [Widok modułów - Instrumentacja](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Moduły View - próbkowanie](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Widok modułów](../profiling/modules-view-instrumentation-data.md)   
 [Widok modułów](../profiling/modules-view-sampling-data.md)