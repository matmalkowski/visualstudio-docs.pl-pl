---
title: 'Wskazówki: Profilowanie wiersza polecenia przy użyciu próbkowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db4b47582d03a7f040850dd69e61d5fee2b80020
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815259"
---
# <a name="walkthrough-command-line-profiling-using-sampling"></a>Wskazówki: Profilowanie wiersza polecenia przy użyciu pobierania próbek

W tym przewodniku pokazano, jak profile aplikacji za pomocą narzędzia wiersza polecenia i pobierania próbek do identyfikowania problemów z wydajnością.

W tym przewodniku będzie kroków procesu profilowania aplikacji zarządzanych za pomocą narzędzia wiersza polecenia i użyj próbkowania w celu odizolowania i zidentyfikować problemy z wydajnością w aplikacji.

W tym przewodniku będzie wykonaj następujące kroki:

- Profil aplikacji za pomocą narzędzia wiersza polecenia i pobierania próbek.
- Analizuj próbkowanych wyniki profilowania odszukaj i rozwiąż problemy z wydajnością.

## <a name="prerequisites"></a>Wymagania wstępne

- Zrozumienie pośredni [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)]
- Pośredniego opis pracy z narzędzi wiersza polecenia
- Kopię [PeopleTrax — przykład](../profiling/peopletrax-sample-profiling-tools.md)
- Aby pracować z informacjami pochodzącymi profilowania, jest najlepszym rozwiązaniem jest dostępne informacje dotyczące symboli debugowania.

## <a name="command-line-profiling-using-the-sampling-method"></a>Profilowanie wiersza polecenia przy użyciu metody pobierania próbek

Próbkowanie to metodę profilowania za pomocą którego określonego procesu okresowo wysyłane do określenia active funkcji. Dane wynikowe zapewnia liczenie częstotliwość funkcja znajdowała się na szczycie stosu wywołań proces był wtedy próbkowany.

> [!NOTE]
> Narzędzia wiersza polecenia narzędzi profilowania znajdują się w *\Team Tools\Performance narzędzia* podkatalogu w katalogu instalacji programu Visual Studio. Na komputerach 64-bitowych zarówno 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). PeopleTrax jest 32-bitowej aplikacji.

### <a name="to-profile-the-peopletrax-application-by-using-the-sampling-method"></a>Do profilu aplikacji PeopleTrax za pomocą metody pobierania próbek

1. Zainstaluj aplikację przykładową PeopleTrax i kompilacji wersji aplikacji.

2. Otwórz okno wiersza polecenia i Dodaj katalog narzędzi profilowania do lokalnej zmiennej środowiskowej Path.

3. Zmień katalog roboczy na katalog, który zawiera pliki binarne PeopleTrax.

4. Wpisz następujące polecenie, aby ustawić zmienne środowiskowe odpowiednie:

    ```cmd
    VSPerfCLREnv /sampleon
    ```

5. Uruchom profilowanie, uruchamiając *VSPerfCmd.exe*, która jest narzędzie wiersza polecenia, które kontroluje profilera. Następujące polecenie uruchamia aplikację i profilera trybu próbkowania:

    ```cmd
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe
    ```

     Proces profilera uruchamia i dołącza do *PeopleTrax.exe* procesu. Aby zapisywać zebrane dane profilowania do pliku raportu rozpocznie się proces profilera.

6. Kliknij przycisk **uzyskać osób**.

7. Kliknij przycisk **ExportData**.

     Notatnik otwiera i wyświetla nowy plik zawierający wyeksportowane dane z **PeopleTrax**.

8. Zamknij Notatnik, a następnie Zamknij **PeopleTrax** aplikacji.

9. Zamknij profilera. Wpisz następujące polecenie:

    ```cmd
    VSPerfCmd /shutdown
    ```

10. Aby zresetować zmiennych środowiskowych, użyj następującego polecenia:

    ```cmd
    VSPerfCLREnv /sampleoff
    ```

11. Dane profilowania jest przechowywany w. *vsp* analiza pliku wyników przy użyciu jednej z następujących metod:

    - Otwórz. *vsp* pliku w programie Visual Studio IDE.

         — lub —

    - Generowanie wartości rozdzielanych przecinkami (. *CSV*) plików za pomocą narzędzia wiersza polecenia *VSPerfReport.exe*. Aby móc wygenerować raporty do użytku poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, użyj następującego polecenia:

        ```cmd
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all
        ```

## <a name="see-also"></a>Zobacz także

[Sesja wydajności — omówienie](../profiling/performance-session-overview.md)  
[Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)  
[VSPerfCmd](../profiling/vsperfcmd.md)  
[Zrozumienie wartościami danych próbkowania](../profiling/understanding-sampling-data-values.md)  
[Widoki raportu wydajności](../profiling/performance-report-views.md)