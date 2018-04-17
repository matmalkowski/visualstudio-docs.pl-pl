---
title: Rozwiązywanie problemów i znane problemy dotyczące debugowania migawki | Dokumentacja firmy Microsoft
ms.date: 11/07/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ae5da4031ceb2716970b028fb15c11348df89c4a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Rozwiązywanie problemów i znane problemy dotyczące migawki debugowania w programie Visual Studio

Jeśli kroki opisane w tym temacie nie rozwiąże problemu, skontaktuj się z snaphelp@microsoft.com.

## <a name="issue-snappoint-does-not-turn-on"></a>Problem: Snappoint jest wyłączone

Jeśli widzisz ikonę ostrzeżenia ![ikona ostrzeżenia Snappoint](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "ikona ostrzeżenia Snappoint") z Twojej snappoint zamiast ikony regularne snappoint następnie snappoint nie jest włączona.

![Nie włączaj Snappoint](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Snappoint jest wyłączone")

Wykonaj następujące czynności:

1. Upewnij się, że korzystasz z tej samej wersji kodu źródłowego, który był używany do tworzenia i wdrażania app.isua1 Twojego. Upewnij się, że są ładowane poprawne symbole dla danego wdrożenia. Aby to zrobić, należy wyświetlić **modułów** okno podczas debugowania migawki i sprawdź kolumna pliku symboli zawiera plik PDB dla modułu debugowania. Należy pamiętać, że debuger migawki podejmie próbę automatycznego pobrania i zastosowania symboli dla danego wdrożenia.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problem: Symbole nie są ładowane, podczas otwierania migawki

Jeśli zostanie wyświetlone następujące okno, symbole nie został załadowany.

![Nie ładuj symbole](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "symbole nie są ładowane.")

Wykonaj następujące czynności:

- Kliknij przycisk **zmiany ustawień symboli...** łącze na tej stronie. W **debugowanie > Symbol** ustawienia, Dodaj katalog pamięci podręcznej symboli. Uruchom ponownie debugowanie migawki po ustawieniu ścieżki symboli.

   Symbole lub .pdb, pliki, dostępne w projekcie musi odpowiadać wdrożenia usługi aplikacji. Większości wdrożeń (wdrożenia za pomocą programu Visual Studio, CI/CD programu VSTS lub Kudu, itp.) będą publikowane plików symboli wraz z usługi aplikacji. Ustawianie katalogu pamięci podręcznej symboli umożliwia Visual Studio, aby użyć tych symboli.

   ![Symbol ustawienia](../debugger/media/snapshot-troubleshooting-symbol-settings.png "ustawień symboli")

- Alternatywnie Jeśli Twoja organizacja korzysta z serwera symboli lub porzuca symbole w inną ścieżkę, należy użyć ustawień symbol załadować poprawne symbole dla danego wdrożenia.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problem: nie widzę opcja "Dołącz debugera migawki" w Eksploratorze chmury

Wykonaj następujące czynności:

- Upewnij się, że jest zainstalowany składnik debugera migawki. Otwórz Instalator programu Visual Studio i sprawdź **debugera migawki** składnika pracą platformy Azure.
- Upewnij się, że aplikacja jest obsługiwana. Obecnie tylko ASP.NET (4.6.1+) i aplikacje platformy ASP.NET Core (2.0 +) wdrożone usługi aplikacji Azure są obsługiwane.

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problem: można wyświetlić tylko ograniczony migawek w narzędziach diagnostycznych

![Throttled snappoint](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Zdławionych snappoint")

Wykonaj następujące czynności:

- Migawki potrwać bardzo mała ilość pamięci, ale ma opłat zatwierdzania. Jeśli debuger migawki wykrywa, że serwer jest pamięci mocno obciążony, nie będą brane migawki. Można usunąć migawki już przechwyconych zatrzymywania sesji debugera migawki i podjęcie ponownej próby.

## <a name="known-issues"></a>Znane problemy

- Migawki debugowania z wielu klientów programu Visual Studio z tej samej usługi aplikacji nie jest obecnie obsługiwane.
- Optymalizacje Roslyn IL nie są w pełni obsługiwane w projektów platformy ASP.NET Core. Dla niektórych projektów platformy ASP.NET Core mogą nie być mogli zobaczyć niektóre zmienne ani niektóre zmienne w instrukcjach warunkowego. 
- Zmienne specjalne, takie jak *$FUNCTION* lub *$CALLER*, nie można obliczyć w instrukcji warunkowej lub logpoints dla projektów platformy ASP.NET Core.
- Debugowanie migawki nie działa na usługi aplikacji, która ma [buforowanie lokalne](/azure/app-service/app-service-local-cache) włączona.
- Debugowanie aplikacji interfejsu API migawki nie jest obecnie obsługiwane.

## <a name="site-extension-upgrade"></a>Uaktualnienie rozszerzenia lokacji

Migawki debugowanie i usługa Application Insights zależą od ICorProfiler, który ładuje z procesem lokacji i powoduje problemy podczas uaktualniania. Zalecamy, aby ten proces, aby upewnić się, że nie nie czas przestoju do swojej witryny produkcji.

- Utwórz [miejsce wdrożenia](/azure/app-service/web-sites-staged-publishing) w usłudze App Service i wdrażanie witryny dla gniazda.
- W Eksploratorze chmury w programie Visual Studio lub z portalu Azure, Zamień miejsca produkcji.
- Zatrzymaj witrynę miejsca. To może zająć kilka sekund kill poza procesu w3wp.exe lokacji ze wszystkich wystąpień.
- Uaktualnienie gniazdo rozszerzenia lokacji w lokacji Kudu lub w portalu Azure (*bloku usługi aplikacji > Narzędzia do programowania > Rozszerzenia > aktualizacji*).
- Uruchom witrynę miejsca. Firma Microsoft zaleca w witrynie do rozgrzewki go ponownie.
- Zamienić miejsca produkcji.

## <a name="see-also"></a>Zobacz także

[Debugowanie w programie Visual Studio](../debugger/index.md)  
[Debugowania na żywo aplikacji ASP.NET, za pomocą debugera migawki](../debugger/debug-live-azure-applications.md)  
[Debugowanie migawek — często zadawane pytania](../debugger/debug-live-azure-apps-faq.md)  
