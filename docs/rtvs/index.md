---
title: R Tools for Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: hero-article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: data-science
ms.openlocfilehash: c18eadd6cfcdf6fc77b204f78654126ceb1862db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-r-in-visual-studio"></a>Praca z języka R w programie Visual Studio

R jest wysoce rozszerzalne języka i środowiska do statystycznego przetwarzania danych i grafiki. Go program jest dystrybuowany za darmo GNU General Public License, będą zadowoleni techniczna dla społeczności silne i jest znany dla możliwość utworzenia powierzchni jakości publikacji tym symbole matematyczne i pochodnych. Dowiedz się więcej o R w [r project.org](https://www.r-project.org/about.html) i [wprowadzenie do języka R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html).

R narzędzi dla programu Visual Studio (RTVS) to bezpłatny, [open source](https://github.com/microsoft/RTVS) rozszerzenia dla programu Visual Studio 2017 i Visual Studio 2015 Update 3 (lub nowszej), wydane w ramach licencji MIT. (Drugi składnik open source o nazwie [RHost](https://github.com/microsoft/R-Host), które łączy do plików binarnych interpreter języka R, jest wydane V2 licencji publicznej GNU.)

> [!Note]
> RTVS jest obecnie obsługiwany tylko w Visual Studio w systemie Windows, a nie programu Visual Studio dla komputerów Mac.

Aby skorzystać z języka R w programie Visual Studio:

- [Zainstaluj narzędzia R](installation.md).
- Postępuj zgodnie z [wprowadzenie](getting-started-with-r.md) przewodniku, jak również [przykłady](getting-started-samples.md) i [uzyskiwanie pomocy](getting-started-help.md) tematów.

Następnie wykonaj poniższe łącza, aby dowiedzieć się więcej o funkcjach R, a także ogólne możliwości programu Visual Studio, sama.

| Funkcja | Opis | Dokumentacja ogólna Visual Studio | 
| --- | --- | --- |
| [Program Visual Studio system projektu](projects.md) | Organizowanie Zarządzanie powiązane pliki w strukturze wygodne i skorzystać z szablonów przydatne dla elementów, jak kod języka R, dokumentację języka R R Markdown, zapytania SQL i procedur składowanych. Również kredyty [Menedżera pakietów](package-manager.md) i [integracji programu SQL Server](sql-server.md).  | [Rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Obszar roboczy](workspaces.md) | RTVS można powiązać obszary robocze lokalnych i zdalnych, umożliwiając tworzenie kodu języka R lokalnie mniejszych zestawów danych, a następnie łatwo uruchomić kod na wydajniejsze komputery oparte na chmurze z znacznie większych zestawów danych. | n/d |
| [Opcje narzędzia R](options.md) | Kontrolować różne aspekty RTVS. | [Opcje — okno dialogowe](../ide/reference/options-dialog-box-visual-studio.md) |
| [Edytowanie sformatowanego, IntelliSense i wstawki kodu](code-editing.md) | Obejmuje kolorowania, [IntelliSense](code-intellisense.md) we wszystkich kodu i bibliotek, formatowania pomocy podpisu kodu przejdź do definicji i Znajdź wszystkie odwołania [wstawki kodu](code-snippets.md)itd. | [Pisanie kodu w edytorze kodu i tekstu](../ide/writing-code-in-the-code-and-text-editor.md) |
| [Znaczniki R Markdown](rmarkdown.md) | Dokumenty R Markdown pomóc Udostępnianie wyników dane zintegrowane R kodu wewnątrz bloków kodu w języku znaczników markdown. | n/d |
| [Okno interaktywne](interactive-repl.md) | Zapewnia pełne środowisko REPL dla języka R umożliwia łatwe uruchamianie kodu w pliku źródłowego w oknie interaktywnym. | n/d |
| [Wizualizacja danych](visualizing-data.md) | Kreślenia jest integralną częścią środowisko R i RTVS obsługuje wiele niezależnych kreślenia systemu windows, każdy z własnych historii i możliwość przenoszenia geograficzne między systemem windows. Powierzchnie można zapisać plików PDF i mapy bitowej lub skopiowane do Schowka jako mapa bitowa lub metaplik.  | n/d |
| [Eksplorator zmiennych](variable-explorer.md) | Sprawdź zmienne w zakresach globalnych lub specyficznych dla pakietu, umożliwia wyświetlanie tabel można sortować i wyeksportować do pliku CSV. | n/d |
| [Oferujący wszystkie funkcje debugowania](debugging.md) | Obejmuje integrację z okna interaktywnego. | [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md) |

Zobacz też [— często zadawane pytania](faq.md).

Poniższe wideo są także przegląd możliwości narzędzia R brief (5m 48s):

> [!VIDEO https://www.youtube.com/embed/RcSDEfMgUvU]

## <a name="send-us-your-feedback"></a>Wyślij nam swoją opinię!

1. **Problemy z usługi Github**: to najlepszy sposób, aby osiągnąć zespołu RTVS przez [składanie problemu w serwisie GitHub](https://github.com/Microsoft/RTVS/issues), lub za pomocą **narzędzia R > opinii** menu.

1. **Wyślij uśmiech / łuk w dół**: **narzędzia R > opinie** menu jest szybkim sposobem Wyślij opinię i Dołącz RTVS pliki dziennika, aby pomóc w diagnozowaniu problemu. (Dzienniki są zapisywane w `%temp%/RTVSlogs.zip` w przypadku, gdy chcesz wysyłać je oddzielnie.) Rejestrowanie jest wyłączone, jeśli został wyłączony z telemetrii programu Visual Studio za pomocą **Pomoc > opinię > Ustawienia** menu polecenia, lub podczas instalacji.

1. **Wiadomości e-mail**: możesz wysłać opinię bezpośrednio do zespołu w *rtvsuserfeedback (adresem)*.
