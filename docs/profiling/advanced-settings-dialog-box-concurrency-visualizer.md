---
title: Okno dialogowe Zaawansowane ustawienia (Concurrency Visualizer) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.settings
ms.assetid: bb3d90aa-5f08-4953-9be0-be6cea11633d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d697ee37cb8412e4fa0a51096858d9fa4b17877
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34690796"
---
# <a name="advanced-settings-dialog-box-concurrency-visualizer"></a>Okno dialogowe Zaawansowane ustawienia (Concurrency Visualizer)
Za pomocą **Zaawansowane ustawienia** okno dialogowe w narzędzia Concurrency Visualizer można kontrolować, jak zbierane są dane śledzenia.  Okno dialogowe zawiera karty symbole, tylko mój kod, buforowanie, filtrowanie, CLR zdarzenia, znaczniki, dostawców i plików.  
  
## <a name="symbols"></a>Symbole  
 Narzędzia Concurrency Visualizer używa tych samych ustawień symboli jako debuger programu Visual Studio. Concurrency Visualizer korzysta z ustawień, aby rozwiązać stosy wywołań, które są skojarzone z danych dotyczących wydajności.  Podczas przetwarzania śladów, Concurrency Visualizer uzyskuje dostęp do serwerów symboli, które są określone na stronie ustawień.  Jeśli te dane uzyskuje się dostęp za pośrednictwem sieci, przetwarzania śledzenia działa wolniej.  Aby zmniejszyć ilość czasu, która jest wymagana do rozpoznawania symboli, pamięci podręcznej symboli lokalnie. Jeśli pobrano symbole, Visual Studio pobierze je z lokalnej pamięci podręcznej.  
  
## <a name="just-my-code"></a>Tylko mój kod  
 Domyślnie tylko mój kod jest zestaw. *exe* i. *biblioteki dll* pliki, które są skojarzone z bieżącym rozwiązaniem w programie Visual Studio. Narzędzia Concurrency Visualizer daje w wyniku tego zestawu plików przy użyciu funkcji tylko mój kod do filtrowania stosy wywołań. Na karcie tylko mój kod można dodać katalogi, które zawierają. *exe* i. *biblioteki dll* pliki do lokalizacji, które używa narzędzia Concurrency Visualizer tylko mój kod.  
  
 Ścieżek. *exe* i. *biblioteki dll* pliki są przechowywane w pliku śledzenia podczas zbierania śladu.  Zmiana tego ustawienia nie wpływa na wszystkie uprzednio zebrane ślady.  
  
## <a name="buffering"></a>Buforowanie  
 Jeśli zbiera śledzenia, Concurrency Visualizer używa funkcji Śledzenie zdarzeń systemu Windows ().  ETW używa różnych buforów przechowuje zdarzenia.  Domyślne ustawienia bufora ETW może nie być optymalne we wszystkich przypadkach, a w niektórych przypadkach, może spowodować problemy, takie jak zdarzenia utracone.  Karta buforowanie Aby skonfigurować ustawienia bufora ETW. Aby uzyskać więcej informacji, zobacz [śledzenie zdarzeń](http://go.microsoft.com/fwlink/?LinkId=234579) i [struktury EVENT_TRACE_PROPERTIES](http://go.microsoft.com/fwlink/?LinkId=234580).  
  
## <a name="filter"></a>Filtr  
 Na karcie Filtr można wybrać zestaw zdarzeń, które zbiera wizualizatora współbieżności. Wybór podzbioru zdarzeń ogranicza typy danych, które są wyświetlane w raportach, zmniejsza rozmiar każdego śledzenia i skraca czas, która jest wymagana do przetwarzania śladów.  
  
### <a name="clr-events"></a>zdarzenia CLR  
 Zdarzenia generowane przez środowisko uruchomieniowe języka wspólnego (CLR) Włącz Concurrency Visualizer rozwiązywać zarządzane stosy wywołań.  Jeśli wyłączysz zbieranie zdarzeń CLR zmniejszy rozmiar śledzenia, ale niektóre stosy wywołań nie zostanie rozwiązany.  W związku z tym niektóre aktywności wątku procesora CPU może być niepoprawnie kategorii.  
  
### <a name="collect-for-native-processes"></a>Zbieraj dla natywnych procesów  
 Domyślnie zdarzenia CLR są zbierane tylko wtedy, gdy proces zarządzany jest profilowane, ponieważ są one zazwyczaj potrzebne natywnych procesów.  W niektórych przypadkach (na przykład podczas procesu natywnego jest hostingu środowiska CLR) może być konieczne zbieranie zdarzeń CLR dla natywnych procesu.  Jeśli jest to możliwe, wybierz **gromadzenia dla natywnych procesów** pole wyboru.  
  
### <a name="disable-rundown-events"></a>Wyłącz zdarzenia stert  
 Środowisko CLR generuje zdarzenia na podstawie dwóch dostawców: środowisko uruchomieniowe i zamknięcia.  Jeśli chcesz zbierać zdarzenia środowiska uruchomieniowego CLR, ale aby uniknąć zbierania zdarzeń zamknięcia, wybierz **wyłączyć zdarzenia uwalniania** pole wyboru.  Zmniejsza rozmiar pliku śledzenia, który jest generowany przez kolekcję, ale nie może rozpoznać niektórych stosów. Aby uzyskać więcej informacji, zobacz [dostawcy ETW CLR](/dotnet/framework/performance/clr-etw-providers)  
  
### <a name="sample-events"></a>Zdarzenia próbkowania  
 Zdarzenia próbkowania służy do zbierania stosy wywołań, skojarzonych z wykonanie wątku. Te zdarzenia są zbierane w przybliżeniu ciągu milisekundy wątków, które są wykonywane w ramach bieżącego procesu. Jeśli wyłączysz zbieranie zdarzeń próbki zmniejsza rozmiar zbieranego śladu, ale nie można wyświetlić wszystkie stosy wywołań skojarzonych z wykonanie wątku.  
  
### <a name="gpu-events"></a>Zdarzenia procesora GPU  
 Zdarzenia generowane przez DirectX są zdarzenia procesora GPU. Jeśli wyłączysz kolekcji zdarzenia procesora GPU zmniejsza rozmiar zbieranego śladu, ale żadnej aktywności procesora GPU nie można wyświetlić w widoku wykorzystania lub aktywności aparatu programu DirectX w widoku wątków.  
  
### <a name="file-io-events"></a>Zdarzenia We/Wy pliku  
 Zdarzenia We/Wy pliku reprezentują uzyskuje dostęp do dysku w imieniu bieżącego procesu.  Jeśli wyłączysz zdarzenia We/Wy plików zmniejsza rozmiar śledzenia, ale widok wątki nie zgłosi żadnych informacji o kanały dysku lub dysku operacji.  
  
## <a name="markers"></a>Znaczniki  
 Na **znaczniki** kartę, można skonfigurować zestaw dostawcy ETW, które są wyświetlane jako znaczniki Concurrency Visualizer.  Można również filtrować znacznika kolekcji na podstawie poziomu ważności i ETW kategorii.  Jeśli używasz [SDK wizualizatora współbieżności](../profiling/concurrency-visualizer-sdk.md) się przy użyciu własnego dostawcę znacznika, możesz zarejestrować go tutaj aby był on wyświetlany w widoku wątków.  
  
### <a name="add-a-new-provider"></a>Dodaj nowego dostawcę  
 Jeśli używa Twój kod [SDK wizualizatora współbieżności](../profiling/concurrency-visualizer-sdk.md) lub generuje zdarzenia ETW, które należy wykonać <xref:System.Diagnostics.Tracing.EventSource> Konwencji, można wyświetlać te zdarzenia w Concurrency Visualizer przez zarejestrowanie ich w tym oknie dialogowym.  
  
 W **nazwa** wprowadź nazwę opisującą typy zdarzeń, które są generowane przez dostawcę.  W **GUID** wprowadź identyfikator GUID, który jest skojarzony z tym dostawcą. (Identyfikator GUID jest skojarzony z każdego dostawcy ETW).  
  
 Opcjonalnie można określić, czy filtrowanie zdarzeń z tym dostawcą, na podstawie poziomu kategorii lub ważności.  Za pomocą kategorii pole ma zostać przefiltrowane na podstawie zestawu SDK wizualizatora współbieżności kategorii.  Aby to zrobić, wprowadź ciągów rozdzielanych przecinkami, kategorii lub zakresy kategorii.  To ustawienie określa kategorie zdarzeń w bieżącym dostawcy do wyświetlenia.  Jeśli dodajesz <xref:System.Diagnostics.Tracing.EventSource> dostawcy, służy pole kategorii do filtrowania według słów kluczowych funkcji ETW.  Ponieważ słowo kluczowe jest maską bitów, umożliwia określenie, które bity maski są ustawiane przez osoby rozdzielany przecinkami ciąg liczb całkowitych. Na przykład "1,2" ustawia bity pierwszego i drugiego i przekłada się 6 w dziesiętnych.  
  
 Lista poziom ważności umożliwia odfiltrowywania zdarzeń, które mają znaczenie lub poziom funkcji ETW, która jest mniejsza niż określona wartość.  
  
### <a name="configure-an-existing-provider"></a>Konfigurowanie istniejącego dostawcy  
 Aby edytować ustawienia, które są skojarzone z istniejącego dostawcy, wybierz z listy, a następnie wybierz **dostawcy edycji** przycisku.  Można zmienić nazwę, identyfikator GUID i ustawienia filtrowania.  
  
### <a name="filter-marker-data-out-of-concurrency-visualizer-reports"></a>Filtrowanie danych znacznika poza raporty Concurrency Visualizer  
 Jeśli nie chcesz danych dla określonego dostawcy się pojawić w przyszłości śladów, wyczyść pole wyboru obok dostawcy, który ma zostać usunięty.  
  
## <a name="files"></a>Pliki  
 Na **pliki** kartę, można określić katalog, w obszarze śledzenia pliki przechowywane są zawsze śledzenia są zbierane.  Narzędzia Concurrency Visualizer generuje cztery pliki do każdego śledzenia, który zbiera:  
  
-   Plik dziennika (ETL) śledzenia zdarzeń w trybie jądra (*.* Kernel.etl*)  
  
-   Plik dziennika śledzenia zdarzeń trybu użytkownika (*.* User.etl*)  
  
-   Plik dane narzędzia Concurrency Visualizer (*.* CVData*)  
  
-   Plik śledzenia wizualizatora współbieżności (*.* CVTrace*)  
  
 Dwa pliki ETL przechowywania danych pierwotnych śledzenia i dwa pliki Concurrency Visualizer przechowywania przetworzonych danych.  Nieprzetworzone pliki ETL zwykle nie są używane po przetworzeniu śledzenia.  Wybieranie **pliki usunąć zdarzenia śledzenia dziennika (ETL) po analizie** pole wyboru zmniejsza ilość danych śledzenia, który jest przechowywany na dysku.  
  
## <a name="see-also"></a>Zobacz także  
 [Tylko mój kod](../profiling/just-my-code-threads-view.md)   
 [Znaczniki CONCURRENCY Visualizer](../profiling/concurrency-visualizer-markers.md)