---
title: Zbieranie statystyk wydajności za pomocą metody pobierania próbek | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,sampling
- sampling profiling method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6deab9a5c2957dfe53e973318879b012db483c22
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="collecting-performance-statistics-by-using-sampling"></a>Zbieranie statystyk wydajności za pomocą metody pobierania próbek

Domyślnie program Visual Studio Profiling Tools metody próbkowania zbiera informacje profilowania co 10 000 000 cykli procesora (około co setną sekundy na komputerze, 1 GHz). Metody pobierania próbek jest przydatne w przypadku znalezienia problemy dotyczące użycia procesora i Sugerowane metody uruchamiania większości dochodzenia wydajności.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

Metoda pobierania próbek można określić za pomocą jednej z następujących procedur:

- Na pierwszej stronie kreatora profilowania, kliknij przycisk **próbkowania procesora CPU (zalecane)**.
- Na **Eksplorator wydajności** paska narzędzi w **metody** kliknij **próbkowania**.
- Na **ogólne** strony okna dialogowego właściwości sesji wydajności, kliknij przycisk **próbkowania**.

## <a name="common-tasks"></a>Wspólne zadania

Możesz określić dodatkowe opcje w *sesji wydajności *** strony właściwości** okno dialogowe sesji wydajności. Aby otworzyć okno dialogowe:

- W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij przycisk **właściwości**.

 Zadania w poniższej tabeli opisano opcje, które można określić w *sesji wydajności *** strony właściwości** okno dialogowe, gdy profilu przy użyciu metody pobierania próbek.

|Zadanie|Zawartość pokrewna|
|----------|---------------------|
|Na **ogólne** strony, Dodaj alokacji pamięci .NET i zbieranie danych okres istnienia i określ szczegóły nazewnictwa profilowania wygenerowany plik danych (Vsp).|- [Zbieranie alokacji pamięci .NET i okres istnienia obiektu](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [Porady: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na **próbkowania** strony, zmienić częstotliwość próbkowania, Zmień zdarzenie próbkowania z cykli zegara procesora do innego licznika wydajności procesora lub zmienić jednocześnie.|- [Porady: Wybieranie zdarzeń pobierania próbek](../profiling/how-to-choose-sampling-events.md)|
|Na **uruchamianie** Określ aplikację do uruchomienia i rozpoczęcia zlecenia, jeśli masz wiele .exe projektów w rozwiązaniu kodu.|- [Zbieranie danych o interakcji między warstwy](../profiling/collecting-tier-interaction-data.md)|
|Na **interakcja warstwowa** Dodaj informacje o wywołaniach ADO.NET do danych zbieranych w theprofiling Uruchom.|- [Zbieranie danych o interakcji między warstwy](../profiling/collecting-tier-interaction-data.md)|
|Na **zdarzeń systemu Windows** Określ co najmniej jednego zdarzenia funkcji Śledzenie zdarzeń systemu Windows () do zbierania danych próbkowania.|- [Porady: zbieranie zdarzeń śledzenia dla danych systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Na **liczników systemu Windows** strony, określ co najmniej jeden liczników wydajności systemu operacyjnego można dodać do danych profilowania jako znaczniki.|- [Porady: zbieranie danych liczników systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na **zaawansowane** strony, określ wersję środowiska uruchomieniowego .NET Framework do profilowania, jeśli moduły aplikacji używać wielu wersji. Domyślnie jest profilowane pierwszej wersji załadowane.|- [Porady: Określanie środowiska wykonawczego .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|