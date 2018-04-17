---
title: Widok szczegółów funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.functiondetails
helpviewer_keywords:
- Function Details view
- Profiling Tools, Function Details view
ms.assetid: 8806954f-cf28-48d5-81b2-d722ceaf7d27
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7078b1d5b831ded10ad3d0f474e0656d8e99ddb1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="function-details-view"></a>Widok szczegółów funkcji
**Widok szczegółów funkcji** wyświetlane są następujące informacje:  
  
-   **Dystrybucji** wykres słupkowy przedstawia relacje między funkcja i wywołanie funkcji wykonanych wybranej funkcji oraz między wybranej funkcji i funkcji, które zostały wywołane przez go.  
  
-   **Szczegółów wydajności funkcji** tabeli przedstawiono podsumowanie danych profilowania funkcji, który określisz.  
  
-   **Widoku kodu funkcji** okna, które zawiera kod funkcji, jeśli kod jest dostępny.  
  
 **Widoku kodu funkcji** okno jest osobnym okienku. Domyślnie dwa okienka dzieli się poziomo i **widoku kodu funkcji** okna znajduje się w dolnej części ramki.  
  
-   Aby podzielić dwa okienka w pionie, kliknij przycisk **Podziel pionowo ekranu** na pasku narzędzi.  
  
-   Aby zmienić rozmiar względny okienek, kliknij przyciemnione obramowania klatek i przeciągnij obramowanie do innej lokalizacji.  
  
## <a name="cost-distribution-bar-chart"></a>Wykres słupkowy dystrybucji kosztów  
  
### <a name="performance-metrics"></a>Metryki wydajności  
 W **metryki wydajności** listy rozwijanej można określić wartości, które są wyświetlane w widoku. Wartości, które są dostępne są zależne od metodę profilowania, który był używany w pliku danych profilowania. Nazwy w nawiasach są nazwami wierszy w **szczegółów wydajności funkcji** tabeli.  
  
### <a name="bar-chart"></a>Wykres słupkowy  
 **Wywoływanie funkcji**  
  
 **Podczas wywoływania funkcji** pasek zawiera funkcje, które wywołuje wybranej funkcji. Rozmiar bloku, który zawiera wywołanie funkcji jest proporcjonalnie do udziału funkcji wywołującej do całkowitej wartości metryki wydajności dla wybranej funkcji.  
  
 Możesz kliknąć nazwę wywołania funkcji, aby była funkcja wybranego w widoku.  
  
-   W przypadku zbyt wielu wywoływanie funkcji, aby wyświetlić listę funkcji z najmniejszą udziałami są gromadzone w **innych** bloku. Kliknij przycisk **innych** do wyświetlenia wszystkich funkcji wywołującego i o nazwie wybranej funkcji w **widok wywołujący/wywoływany** okna. Aby uzyskać więcej informacji, zobacz [widok wywołujący/wywoływany](../profiling/caller-callee-view.md).  
  
-   Jeśli nie ma żadnych wywoływania funkcji lub funkcja jest funkcją wejścia wątku lub procesu, **góry stosu** pojawi się blok.  
  
 **Wybranej funkcji**  
  
 Na pasku wybranej funkcji zawiera wkładów funkcji o nazwie i kodu w wybranej funkcji metryce całkowitej wydajności wybranych funkcji. Rozmiar bloku zawierającego wywołana funkcja lub treści funkcji jest proporcjonalnie jej udziału łączną wartość metryki wydajności dla wybranych funkcji.  
  
 Możesz kliknąć nazwę wywołanej funkcji, aby była funkcja wybranego w widoku.  
  
-   **Całkowita** wartość metryki wydajności dla wybranej funkcji.  
  
-   **Treści funkcji** blok reprezentuje ilość łączną wartość metryki wydajności, który wystąpił na bezpośrednie wykonywanie kodu w treści funkcji.  
  
-   Funkcje, które są wywoływane przy wybranej funkcji są wyświetlane w blokach. Rozmiar bloku funkcji reprezentuje ilość metryki całkowitej wydajności dla wybranej funkcji, który wystąpił w wywoływana funkcja.  
  
-   W przypadku zbyt wielu wywoływanie funkcji, aby wyświetlić listę funkcji z najmniejszą udziałami są gromadzone w **innych** bloku. Kliknij przycisk **innych** do wyświetlenia wszystkich funkcji wywołującego i o nazwie wybranej funkcji w **widok wywołujący/wywoływany** okna. Aby uzyskać więcej informacji, zobacz [widok wywołujący/wywoływany](../profiling/caller-callee-view.md).  
  
-   Jeśli nie ma żadnych funkcji o nazwie, **dolnej stosu** pojawi się blok.  
  
## <a name="function-performance-details"></a>Szczegóły wydajności — funkcja  
 Tabela szczegółów wydajności funkcji zawiera podsumowania danych dla metryki wydajności wybranych funkcji. Zarówno wartość i wartość procentowa są wyświetlane. Określ Określ dane profilowania, których wykresu i szczegóły są wyświetlane w tabeli **metryki wydajności** listy.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Wyłączności**|-Ilość metryki wydajności, który wystąpił podczas wykonywania treści funkcji.|  
|**W wywołaniach**|-Ilość metryki wydajności, który wystąpił w funkcje, które wywołuje wybranej funkcji.|  
|**Całkowita liczba włącznie**|-Sumy **wyłącznego** i **w wywołaniach** wartości.|  
  
## <a name="function-code-view"></a>Widok kodu — funkcja  
 **Widoku kodu funkcji** okno zostanie wyświetlona lista kodu źródłowego, gdy jest ona dostępna. Obok wierszy kodu źródłowego, które wywołują inne funkcje przyciemnione kolumna zawiera wartości metryki wydajności dla wywołanej funkcji. Aby edytować kod źródłowy, kliknij łącze do pliku kodu źródłowego.  
  
## <a name="cost-distribution-bar-chart-values"></a>Pasek dystrybucji koszt wartości wykresu  
  
### <a name="sampling"></a>Pobierania próbek  
 W poniższej tabeli przedstawiono wartości na liście metryki wydajności dla danych profilowania, który został zebrany przy użyciu metody pobierania próbek.  
  
|||  
|-|-|  
|**Przykłady z wartościami granicznymi (zebranych — przykłady)**|— Dla wywołania funkcji, liczba próbek, które zostały zebrane podczas wywoływania funkcji wybranych przez tę funkcję wywołania.<br />— Dla treści funkcji liczba próbek, które zostały zebrane podczas wykonywania własny kod wybranej funkcji.<br />— Dla funkcji o nazwie, liczba próbek, które zostały zebrane podczas wykonywania wywołanej funkcji z powodu wywołania z wybranych funkcji.|  
  
### <a name="instrumentation"></a>Oprzyrządowanie  
 W poniższej tabeli przedstawiono wartości na liście metryki wydajności dla danych profilowania, który został zebrany przy użyciu metody instrumentacji.  
  
|||  
|-|-|  
|**Czas, który upłynął włącznie (czas)**|Czas, który upłynął obejmuje czas przeznaczony w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.<br /><br /> — Dla **podczas wywoływania funkcji**, ilość minionego czasu, jaki był poświęcony na wykonywanie wystąpienia wybranej funkcji, które zostały wywołane przez funkcję. Czas spędzony w funkcjach wywoływanych przez wybranej funkcji jest dołączony.<br />— Dla **treści funkcji**, całkowita ilość czasu poświęcony na wykonywanie kodu wybranych funkcji. Czas spędzony w funkcji o nazwie nie jest włączony.<br />— Dla funkcji o nazwie kwota czas wykonywania wystąpienia funkcji, które zostały wywołane przez wybranej funkcji. Obejmuje czas przeznaczony na funkcje, które wywołuje funkcję. Czas spędzony w funkcjach wywoływanych przez wybranej funkcji jest dołączony.|  
|**Całkowity czas aplikacji (czas aplikacji)**|Czas aplikacji nie zawiera czas przeznaczony w wywołaniach systemu operacyjnego, takich jak przełączeń kontekstu i operacje wejścia/wyjścia.<br /><br /> — Dla **podczas wywoływania funkcji**, ilość czasu aplikacji, który był poświęcony na wykonywanie wystąpienia wybranej funkcji, które zostały wywołane przez funkcję. Czas spędzony w funkcjach wywoływanych przez wybranej funkcji jest dołączony.<br />— Dla **treści funkcji**, łączny czas trwania aplikacji poświęcony na wykonywanie kodu wybranych funkcji. Czas spędzony w funkcji o nazwie nie jest włączony.<br />— Dla funkcji o nazwie kwota aplikacji czas wykonywania wystąpienia funkcji, które zostały wywołane przez wybranej funkcji. Obejmuje czas przeznaczony na funkcje, które wywołuje funkcję.|  
  
### <a name="net-memory"></a>Pamięci platformy .NET  
 W poniższej tabeli przedstawiono wartości na liście metryki wydajności dla danych profilowania, który został zebrany przy użyciu metody profilowania pamięci .NET.  
  
|||  
|-|-|  
|**Wraz z wartościami granicznymi alokacji (alokacji)**|— Dla **podczas wywoływania funkcji**, liczba obiektów, które zostały przydzielone wystąpienia wybranej funkcji, która wywołuje funkcję. Liczba obejmuje obiekty, które zostały przydzielone przez funkcje, które wywołuje wybranej funkcji.<br />— Dla **treści funkcji**, liczba obiektów, które zostały przydzielone przez funkcję wybrany, gdy było wykonywane własnego kodu. Obiekty przydzielone w funkcjach wywoływanych przez wybranej funkcji nie są uwzględniane.<br />— Dla funkcji o nazwie, liczbę obiektów, które zostały przydzielone wystąpień funkcji, które zostały wywołane przez wybranej funkcji. Liczba obejmuje obiekty, które zostały przydzielone przez funkcje, które wywołuje funkcję.|  
|**Wraz z wartościami granicznymi bajtów (w bajtach)**|— Dla **podczas wywoływania funkcji**, liczba bajtów przydzielonych przez wystąpienia wybranej funkcji, która wywołuje funkcję. Liczba obejmuje bajtów przydzielonych przez funkcje, które wywołuje wybranej funkcji.<br />— Dla **treści funkcji**, całkowita liczba bajtów przydzielonych przez funkcję wybrany, gdy było wykonywane własnego kodu. Bajtów przydzielonych w funkcjach wywoływanych przez wybranej funkcji nie są uwzględniane.<br />— Dla funkcji o nazwie, liczba bajtów przydzielonych przez wystąpienia funkcji, które zostały wywołane przez wybranej funkcji. Liczba obejmuje bajtów przydzielonych przez funkcje, które wywołuje funkcję.|  
  
### <a name="concurrency"></a>Współbieżność  
 W poniższej tabeli przedstawiono wartości na liście metryki wydajności dla danych profilowania, który został zebrany przy użyciu metody współbieżności.  
  
|||  
|-|-|  
|**Wraz z wartościami granicznymi rywalizacji (rywalizacji)**|— Dla **podczas wywoływania funkcji**, numerem zdarzenia rywalizacji zasobów, które wystąpiły w wystąpieniach wybranej funkcji, która wywołuje funkcję. Liczba zawiera zdarzenia rywalizacji w funkcje, które wywołuje wybranej funkcji.<br />— Dla **treści funkcji**, łączna liczba zdarzeń rywalizacji, które wystąpiły podczas wykonywania funkcji własnego kodu. Rywalizacji występujących w funkcje, które zostały wywołane przez wybranej funkcji nie są uwzględniane.<br />— Dla funkcji o nazwie, numerem zdarzenia rywalizacji, które wystąpiły w wystąpieniach funkcji, które zostały wywołane przez wybranej funkcji. Liczba zawiera zdarzenia rywalizacji, które wystąpiły w funkcje, które wywołuje funkcję.|  
|**Wraz z wartościami granicznymi zablokowane godzina (Time zablokowanych)**|— Dla wywołania funkcji czas przeznaczony w zasobie rywalizacji zdarzenia dla wybranego wystąpienia funkcji, które funkcja wywoływana. Czas zawiera czas blokowania w funkcje, które wybrano funkcję o nazwie.<br />— Dla **treści funkcji**, całkowity czas przeznaczony na zdarzenia rywalizacji, które wystąpiły podczas wykonywania funkcji własnego kodu. Rywalizacji występujących w funkcje, które wywołuje wybranej funkcji nie są uwzględniane.<br />— Dla funkcji o nazwie, czas przeznaczony na zdarzenia rywalizacji zasobów dla wystąpień funkcji, która wywołała wybranej funkcji. Czas zawiera funkcje, które funkcja wywoływana czas blokowania, który wystąpił.|