---
title: "Zarządzaj wynikami testu obciążenia w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
ms.assetid: 1cd63c4b-4f74-4133-b675-5e8fbeab25f3
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: f5b09a2350efadafaacdc5fcd530b3c3f50c7419
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
---
# <a name="manage-load-test-results-in-the-load-test-results-repository"></a>Zarządzanie wyników testów obciążenia w repozytorium wyników testów obciążenia

Po uruchomieniu testów obciążenia, wszystkie informacje zebrane podczas uruchomienia testu obciążenia może być przechowywany w *repozytorium wyników testów obciążenia*, która jest bazą danych SQL. Repozytorium wyników testów obciążenia zawiera dane licznika wydajności i informacje o błędach zarejestrowane. Bazy danych repozytorium wyników utworzoną przez Instalatora dla kontrolerów lub tworzone automatycznie przy pierwszym uruchomieniu lokalnego testu obciążenia. Dla przebiegu lokalnego bazy danych zostaną utworzone automatycznie Jeśli schemat testu obciążenia nie istnieje.

 Jeśli zmodyfikujesz ciąg połączenia repozytorium wyników kontrolera do korzystania z innego serwera, nowy serwer musi mieć skryptu loadtestresultsrepository.sql Uruchom, aby utworzyć schemat.

 Visual Studio Enterprise zapewnia licznik nazwane zestawy, które zbierać podstawowe liczniki wydajności oparte na technologii. Te zestawy są przydatne podczas analizowania serwera IIS, platformy ASP.NET server lub programu SQL server. Wszystkie dane zebrane z zestawów liczników są przechowywane w repozytorium wyników testów obciążenia.

> [!IMPORTANT]
> Ma różnicy między zbiór liczników i dane licznika wydajności. Zbiór liczników jest metadanych. Definiuje grupę liczniki wydajności, które powinny być zbierane z komputera, który wykonuje określoną rolę, takich jak usługi IIS lub SQL Server. Zbiór liczników jest częścią definicji testu obciążenia. Dane liczników wydajności zbieranych na podstawie zbiorów liczników, mapowanie licznika ustawioną na określonym komputerze oraz częstotliwość próbkowania.

## <a name="sql-server-versions"></a>Wersje programu SQL Server

 Aby użyć testów obciążenia, można użyć programu SQL Server Express LocalDB, który jest zainstalowany program Visual Studio. Jest to domyślny serwer bazy danych dla testów obciążenia (łącznie z integracji programu Microsoft Excel). SQL Server Express LocalDB jest tryb wykonywania programu SQL Server Express, która jest przeznaczona dla deweloperów programu. Instalacja programu SQL Server Express LocalDB kopiuje minimalny zbiór pliki niezbędne do uruchomienia aparatu bazy danych programu SQL Server.

 Jeśli zespół oczekuje potrzeb duże bazy danych lub projektów pokonać programu SQL Server Express LocalDB, należy rozważyć uaktualnienie do programu SQL Express lub pełnego serwera SQL zapewnienie możliwości skalowania dalszych. Po uaktualnieniu programu SQL Server dla programu SQL Server Express LocalDB pliki MDF i LDF są przechowywane w folderze profilu użytkownika. Te pliki mogą służyć do importowania bazy danych testów obciążenia do programu SQL Server Express lub SQL Server.

## <a name="load-test-results-store-considerations"></a>Zagadnienia dotyczące magazynu wyników testów obciążenia

 Po zainstalowaniu programu Visual Studio Enterprise magazynu wyników testów obciążenia został skonfigurowany do używania wystąpienia programu SQL Express, która jest zainstalowana na komputerze. Program SQL Express jest ograniczone do maksymalnie 4 GB miejsca na dysku. Jeśli program będzie uruchamiany wiele testów obciążenia przez dłuższy czas, należy rozważyć Konfigurowanie magazynie wyników testu obciążenia, aby użyć wystąpienia pełnej produktu SQL Server, jeśli jest dostępna.

## <a name="load-test-analyzer-tasks"></a>Zadania analizatora testu obciążenia

|Zadania|Skojarzone — tematy|
|-----------|-----------------------|
|**Repozytorium wyników — Konfiguracja testu obciążenia:** można zdefiniować repozytorium wyników testów obciążenia w bazie danych SQL. **Uwaga:** podczas instalacji kontrolera testu można także utworzyć repozytorium testu obciążenia. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).||
|**Wybierając i wyświetlając repozytorium wyników:** możesz wybrać repozytorium określonych wyników. Nie są ograniczone do magazynu lokalnego wyników. Często testów obciążenia są uruchamiane na zdalnym zestaw komputerów agenta. Mogą zostać zapisane wyniki testu z agentów programu lub komputera lokalnego do dowolnego serwera SQL, na którym utworzono magazynu wyników testów obciążenia. W obu przypadkach należy określić miejsce przechowywania wyników testu obciążenia za pomocą **administrować kontrolerami testów** okna.|-   [Porady: Wybieranie repozytorium wyników testów obciążenia](../test/how-to-select-a-load-test-results-repository.md)<br />-   [Porady: dostęp do analizy wyników testu obciążenia](../test/how-to-access-load-test-results-for-analysis.md)|
|**Usuwanie wyniku testu obciążenia z repozytorium:** można usunąć wyniku testu obciążenia z **edytorze testu obciążenia** za pomocą **otwarte i zarządzanie wynikami testów obciążenia** okno dialogowe.|-   [Porady: usuwanie wyników testu obciążenia z repozytorium](../test/how-to-delete-load-test-results-from-a-repository.md)|
|**Importowanie i eksportowanie wyników do repozytorium:** można importować i eksportować wyników testu obciążenia z **edytorze testu obciążenia**.|-   [Porady: importowanie wyników testu obciążenia do repozytorium](../test/how-to-import-load-test-results-into-a-repository.md)<br />-   [Porady: eksportowanie wyników testu obciążenia z repozytorium](../test/how-to-export-load-test-results-from-a-repository.md)|

## <a name="related-tasks"></a>Zadania powiązane

 [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

 Aby wyświetlić wyniki działania testu obciążenia i zakończonego testu obciążenia, należy za pomocą analizatora testu obciążenia.

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Porady: dostęp do analizy wyników testu obciążenia](../test/how-to-access-load-test-results-for-analysis.md)