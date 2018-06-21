---
title: Visual Studio Otwórz Folder rozszerzalności omówienie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: dcb2d1d922b4ebd4943c42c478400c5873af9cc4
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2018
ms.locfileid: "36302979"
---
# <a name="open-folder-extensibility"></a>Otwórz Folder rozszerzalności

[Otwórz Folder](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) funkcja umożliwia użytkownikom otwieranie żadnego kodu w programie Visual Studio bez konieczności pliki projektu lub rozwiązania. Otwórz Folder zawiera użytkownicy funkcji oczekują z programu Visual Studio, takich jak:

* Integracja z Eksploratora rozwiązań i wyszukiwania
* Kolorowanie edytora
* Przejdź do nawigacji
* Znajdź w plikach wyszukiwania

W przypadku użycia z obciążeń, takich jak w przypadku rozwoju .NET i C++, użytkownicy również uzyskać:

* Zaawansowana Intellisense
* Funkcje językowe

Otwórz folder rozszerzenia autorzy mogą tworzyć rozbudowane funkcje dla żadnego języka. Brak interfejsów API do obsługi kompilowanie, debugowanie i wyszukiwania symboli dla ścieżce bazowej kodu każdy plik z użytkownikiem. Bieżący rozszerzeń można aktualizować ich istniejących funkcji programu Visual Studio, aby zrozumieć kodu bez zapasowego projektów lub rozwiązanie.

## <a name="an-api-without-project-systems"></a>Interfejs API bez systemów projektów

W przeszłości Visual Studio zrozumiał plików rozwiązania i jego projekty systemów projektu. System projektu jest odpowiedzialny za interakcje funkcji i użytkownika załadowanego projektu. Sam co pliki jego projektu zawiera wizualną reprezentację zawartości projektu, zależności do innych projektów i modyfikacji podstawowych pliku projektu. Jest za pośrednictwem tych hierarchii i możliwości, które inne składniki działają w imieniu użytkownika. Nie wszystkie codebases również są przedstawiane w strukturze projektu i rozwiązania. Języki skryptów i kodu open source napisana w języku C++ dla systemu Linux są dobre przykłady. Przy otwartym folderze programu Visual Studio pozwala użytkownikom nowy sposób interakcji z ich kodu źródłowego.

Interfejsy API otwarty Folder podlegają `Microsoft.VisualStudio.Workspace.*` przestrzeni nazw i są dostępne dla rozszerzeń do tworzenia i wykorzystywania danych lub akcje wokół plików w otwartym folderze. Rozszerzenia mogą zapewniać funkcje dotyczące wielu obszarów, w tym przy użyciu poniższych interfejsów API:

- [Obszary robocze](workspaces.md) — od punktu Otwórz Folder rozszerzalności jest obszar roboczy i jej interfejsów API.
- [Konteksty i akcje plików](workspace-file-contexts.md) — realizowane za pośrednictwem pliku kontekstów analizy kodu określonych plików.
- [Indeksowanie](workspace-indexing.md) — zbieranie i zachować dane na temat obszarów roboczych Otwórz Folder.
- [Usługi językowe](workspace-language-services.md) -integrowania usług języka Otwórz Folder obszarów roboczych.
- [Tworzenie](workspace-build.md) — Obsługa obszarów roboczych Otwórz Folder kompilacji.

Funkcje korzystające z następujących typów konieczne będzie wdrożenie nowych interfejsów API do obsługi Otwórz Folder:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Opinie, komentarze, problemy

Otwórz Folder i `Microsoft.VisualStudio.Workspace.*` opracowywane active są interfejsów API. Jeśli widzisz nieoczekiwanego zachowania, zobacz znane problemy dotyczące wersji zainteresowań. [Społeczność deweloperów](https://developercommunity.visualstudio.com) jest zalecane miejsce do głosowania i tworzyć problemy. Dla każdego opinii zdecydowanie zaleca się szczegółowy opis problemu. Obejmują projektujesz dla używanej wersji programu Visual Studio, interfejsy API używasz (zostały zaimplementowane i co w przypadku interakcji z), oczekiwany wynik i rzeczywiste wyniki. Jeśli to możliwe zawierać zrzut procesu devenv.exe. Użyj śledzenia do przekazywania opinii na ten problem GitHub i związanych z dokumentacją.

## <a name="next-steps"></a>Następne kroki

* [Obszary robocze](workspaces.md) — informacje o obszarze roboczym otwórz Folder interfejsu API.