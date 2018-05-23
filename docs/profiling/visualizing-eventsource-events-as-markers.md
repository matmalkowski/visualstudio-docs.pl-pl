---
title: Wizualizowanie zdarzeń EventSource znaczników | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d144728d86bf57a5af837fb8740becd1b6ee4c22
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="visualize-eventsource-events-as-markers"></a>Wizualizowanie zdarzeń EventSource znaczników
Concurrency Visualizer można wyświetlać zdarzenia EventSource jako znaczniki i kontrolować sposób wyświetlania znaczników. Aby wyświetlić znaczników EventSource, należy zarejestrować identyfikator GUID dostawców ETW za pomocą [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okno dialogowe. Narzędzia Concurrency Visualizer ma domyślnych Konwencji reprezentują zdarzenia EventSource jako [znaczniki typu Flaga](../profiling/flag-markers.md), [znaczniki zakresu](../profiling/span-markers.md), i [znaczniki komunikatu](../profiling/message-markers.md). Można dostosować sposób wyświetlania zdarzeń EventSource przez dodanie pola niestandardowe do zdarzenia. Aby uzyskać więcej informacji na temat znaczników, zobacz [znaczników wizualizatora współbieżności](../profiling/concurrency-visualizer-markers.md). Aby uzyskać więcej informacji o zdarzeniach EventSource, zobacz <xref:System.Diagnostics.Tracing>.  
  
## <a name="default-visualization-of-eventsource-events"></a>Wizualizacja domyślna zdarzeń źródła zdarzeń  
 Domyślnie Concurrency Visualizer używa następujących konwencji reprezentują zdarzenia EventSource.  
  
### <a name="marker-type"></a>Typ znacznika  
  
1.  Zdarzenia, które mają [Opcode](http://msdn.microsoft.com/en-us/d97953df-669b-4c55-b1a8-925022b339b7) win: Start lub win: Stop są traktowane jako początku lub na końcu zakresu, odpowiednio.  Zagnieżdżone lub nakładających się zakresów nie można wyświetlić. Nie można wyświetlić pary zdarzeń, które zaczynają się jeden wątek i kończyć w innym.  
  
2.  Zdarzenie, którego kod operacji nie jest win: Rozpocznij ani win: Stop jest traktowany jako flagi znacznika, chyba że jego [poziom](http://msdn.microsoft.com/en-us/dfa4e0a9-4d89-4f50-aef9-1dae0dc11726) (pole EVENT_RECORD. EVENT_HEADER. EVENT_DESCRIPTOR) jest win: pełne lub nowszej.  
  
3.  We wszystkich innych przypadkach zdarzenie jest traktowany jako wiadomości.  
  
### <a name="importance"></a>Znaczenie  
 W poniższej tabeli opisano sposób mapowania poziom zdarzenia znaczenie znacznika.  
  
|Poziom funkcji ETW|Znaczenie wizualizatora współbieżności|  
|---------------|---------------------------------------|  
|Windows: LogAlways|Normalny|  
|win: krytyczne|Krytyczny|  
|Windows: Wystąpił błąd|Krytyczny|  
|Windows: ostrzeżenie|Wysoka|  
|win: informacyjny|Normalny|  
|win: pełne|Niski|  
|Większa niż win: pełne|Niski|  
  
### <a name="series-name"></a>Nazwa serii  
 Nazwa zadania zdarzenia jest używany dla nazwy serii. Nazwa serii jest pusta, jeśli zadanie nie został zdefiniowany dla zdarzenia.  
  
### <a name="category"></a>Kategoria  
 Jeśli poziom jest win: krytyczne lub win: Wystąpił błąd, a następnie kategorii jest Alert (-1). W przeciwnym razie kategoria jest wartość domyślna (0).  
  
### <a name="text"></a>Tekst  
 Tekst sformatowany komunikat printf typ został zdefiniowany dla zdarzenia, jest on wyświetlany jako opis znacznika. W przeciwnym razie opis jest nazwą zdarzenia i wartość każdego pola ładunku.  
  
## <a name="customize-visualization-of-eventsource-events"></a>Dostosowywanie wizualizacji zdarzeń źródła zdarzeń  
 Można dostosować sposób wyświetlania zdarzeń EventSource, dodając odpowiednie pola do zdarzenia, zgodnie z opisem w poniższych sekcjach.  
  
### <a name="marker-type"></a>Typ znacznika  
 Użyj `cvType` pola, byte, aby kontrolować typ znacznika, który jest używany do reprezentowania zdarzenia. Poniżej przedstawiono dostępne wartości cvType:  
  
|wartość cvType|Wynikowy typ znacznika|  
|------------------|---------------------------|  
|0|Komunikat|  
|1|Początek zakresu|  
|2|Koniec zakresu|  
|3|Flaga|  
|Wszystkie inne wartości|Komunikat|  
  
### <a name="importance"></a>Znaczenie  
 Można użyć `cvImportance` pola, byte, aby kontrolować ustawienia znaczenie dla zdarzenia EventSource. Firma Microsoft zaleca jednak sterować znaczenie wyświetlane zdarzenia przy użyciu jego poziom.  
  
|wartość cvImportance|Znaczenie wizualizatora współbieżności|  
|------------------------|---------------------------------------|  
|0|Normalny|  
|1|Krytyczny|  
|2|Wysoka|  
|3|Wysoka|  
|4|Normalny|  
|5|Niski|  
|Wszystkie inne wartości|Niski|  
  
### <a name="series-name"></a>Nazwa serii  
 Użyj `cvSeries` pole zdarzeń, ciąg, do kontrolowania nazwy serii, zapewniająca Concurrency Visualizer do zdarzenia EventSource.  
  
### <a name="category"></a>Kategoria  
 Użyj `cvCategory` pola, byte, aby kontrolować kategorię, która zapewnia narzędzia Concurrency Visualizer na zdarzenie EventSource.  
  
### <a name="text"></a>Tekst  
 Użyj `cvTextW` pola ciąg do kontrolowania opis, który zapewnia narzędzia Concurrency Visualizer na zdarzenie EventSource.  
  
### <a name="spanid"></a>SpanID  
 Użyj pola cvSpanId, int, aby dopasować pary zdarzeń. Wartość dla każdej pary uruchamiania i zatrzymywania zdarzenia, które reprezentują zakres musi być unikatowa. Zwykle równoczesnych kodu wymaga użyciem pierwotnych obiektów synchronizacji takich jak <xref:System.Threading.Interlocked.Exchange%2A> aby upewnić się, że klucz (wartość, która jest używana do CvSpanID) jest poprawny.  
  
> [!NOTE]
>  Użycie SpanID Aby zagnieździć zakresy, zezwolić im na częściowo nakładają się na tym samym wątku, lub zezwolić im na uruchomić w jednym wątku i zakończenia na innym nie jest obsługiwany.  
  
## <a name="see-also"></a>Zobacz także  
 [Znaczniki CONCURRENCY visualizer](../profiling/concurrency-visualizer-markers.md)