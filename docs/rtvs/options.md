---
title: "R narzędzia Opcje w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 06/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
f1_keywords:
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
ms.topic: article
ms.assetid: 554dc602-ecad-4cd0-8e6f-a60bb8a2328f
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 82e17109ff595ae566ea326dae9237274ee5ad15
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="r-tools-for-visual-studio-options"></a>Narzędzia języka R w opcjach programu Visual Studio
 
Ustawienia są dostęp za pośrednictwem **R Narzędzia > Opcje** menu lub za pomocą **Narzędzia > Opcje** i przewijania **narzędzia R**:
 
  ![Okno dialogowe Opcje dla narzędzi R](media/options-dialog.png)

W poniższych sekcjach opisano różne opcje dostępne na tej stronie.

> [!Note]
> Podczas uzyskiwania dostępu do opcji za pośrednictwem ogólne **Narzędzia > Opcje** menu, konieczne może być wybierz **Pokaż wszystkie ustawienia** u dołu dla **narzędzia R** strony.

< name = "data naukowca układu"</a>

**Narzędzia R > Ustawienia nauki danych** element menu konfiguruje również środowiska IDE programu Visual Studio z układem, który jest zoptymalizowana pod kątem potrzeb analityków danych. W szczególności tej opcji otwiera [Interactive](interactive-repl.md), [Explorer zmiennej](variable-explorer.md), i [obszarów roboczych](workspaces.md) systemu windows:

![Układ okna naukowca danych w programie Visual Studio](media/installation-data-scientist-layout-result.png)

> [!Important]      
> Aby później przywrócić pozostałe ustawienia programu Visual Studio, należy najpierw użyć **Narzędzia > Import i eksport ustawień** polecenia select **Eksportuj wybrane ustawienia środowiska**i określ nazwę pliku. Aby przywrócić te ustawienia, użyj tego samego polecenia, a następnie wybierz **Importuj wybrane ustawienia środowiska**. Umożliwia także te same polecenia po zmianie układu naukowca danych i chcesz do niej powrócić w późniejszym czasie na zamiast używania **ustawienia nauki danych** polecenia bezpośrednio.

## <a name="debugging"></a>Debugowanie

Te opcje umożliwiają kontrolowanie sposobu obsługi wartości w [Explorer zmiennej](variable-explorer.md) w oknach debugera czujki i zmienne lokalne (zobacz [debugowanie](debugging.md).

| Opcja | Wartość domyślna | Opis | 
| --- | --- | --- |
| Ocena active powiązania | `True` | Gdy `True`, zapewnia zawsze widzieć najnowsze wartości podczas sprawdzania zmiennych i właściwości. Ryzyko jest, że obliczania wyrażenia może powodować efekty uboczne, w zależności od tego, jak zostały wprowadzone. |
| Pokaż zmienne poprzedzona kropką | `False` | Określa, czy zmienne prefiksem `.` są wyświetlane. |

## <a name="general"></a>Ogólne

| Opcja | Wartość domyślna | Opis | 
| --- | --- | --- |
| Sprawdź ankiety/wiadomości | `Once a week` | Określa, jak często narzędzia R skontaktować się z serwera aktualizacji wiadomości i ankiet. | 

## <a name="help"></a>Pomoc

| Opcja | Wartość domyślna | Opis | 
| --- | --- | --- |
| Przeglądarki sieci Web F1 | `Internal` | Określa, jak uzyskać pomoc jest wyświetlane, gdy wyszukiwany termin przy użyciu klawiszy Ctrl + F1. Jeśli wartość `Internal`, pomoc jest renderowany w ramach okna narzędzia w programie Visual Studio. Jeśli wartość `External`, pomoc jest wyświetlany w domyślnej przeglądarce sieci web. | 
| F1 Ciąg wyszukiwania sieci Web | `R site:stackoverflow.com` | Określa, jak warunki wyszukiwania są przekazywane do aparat wyszukiwania, po naciśnięciu klawiszy Ctrl + F1 termin w edytorze. Domyślnie ten ciąg jest `R site:stackoverflow.com`, które dołącza `R` do wyszukiwanego terminu. `site:stackoverflow.com` Jest dyrektywą do aparatu wyszukiwania z instrukcją, aby zawęzić zakres wyszukiwania do stron w obrębie `stackoverflow.com` domeny. | 
| R pomocy przeglądarki | `Automatic` | Określa, jak pomoc jest wyświetlany podczas wyszukiwania w dokumentacji R przy użyciu F1, `?`, lub `??`. Jeśli wartość `Automatic`, renderuje pomocy w oknie odpowiednie. Na przykład pomocy HTML pojawi się okna narzędzia Visual Studio, plików PDF znajdują się w domyślnym programie PDF. Jeśli wartość `External`, pomoc jest renderowany w domyślnej przeglądarce sieci web. |

## <a name="history"></a>Historia

| Opcja | Wartość domyślna | Opis | 
| --- | --- | --- |
| Zawsze zapisuj historii | `True` | Określa, czy RTVS zapisuje historii poleceń do `.RHistory` plików w katalogu roboczym, gdy projekt jest zamknięty. Zapisywanie historii odbywa się nawet wtedy, gdy nie można zapisać projekt przed zakończeniem pracy. |
| Resetuj filtr wyszukiwania | `True` | Określa, czy okno Historia można filtrować historii poleceń do wyświetlenia wyłącznie z poleceniami, które podciąg dopasowywania termin filtr w oknie dialogowym Historia R. To ustawienie określa, czy można zresetować historii filtru wyszukiwania zawsze, gdy nowe polecenie Uruchom lub przełącz się do nowego projektu, który wyzwala ładowania innej `.RHistory` pliku. Domyślne ustawienie `True` minimalizuje niespodziewanego, gdy należy uruchomić polecenie z zestaw filtrów i zastanawiasz się, dlaczego polecenie został przeprowadzony nie pojawiają się w historii. |
| Zaznacz pole wyboru wielowierszowy | `True` | Określa, czy wiele wierszy instrukcji można wybrać w historii za pomocą jednego kliknięcia. Strzałka nawigacji interaktywnego systemu Windows w górę lub w dół umożliwia również instrukcje zamiast wierszy. |

## <a name="html"></a>HTML

| Opcja | Wartość domyślna | Opis | 
| --- | --- | --- |
| Przeglądarka strony HTML | `External` | Określa, gdzie zawartości, takich jak `ggvis` wykres, lub `shiny` aplikacji jest renderowany. `Internal`Pokazuje danych wyjściowych HTML w oknie narzędzia w programie Visual Studio; `External` wyświetla danych wyjściowych HTML w domyślnej przeglądarce. | 

## <a name="logging"></a>Rejestrowanie

| Opcja | Wartość domyślna | Opis | 
| --- | --- | --- |
| Zdarzenia dziennika | `Normal` | Określa poziom szczegółowości rejestrowania używane RTVS diagnostyki. Domyślne ustawienie `Normal` tworzy plik dziennika w Twojej `TEMP` katalogu. Jeśli wartość `Traffic`, RTVS dzienników wszystkich poleceń i odpowiedzi w sesji. Te pliki dziennika nigdy nie pozostaw na komputerze, ale może okazać się przydatne przy diagnozowaniu problemów w RTVS. |

## <a name="markdown"></a>Język znaczników markdown

| Opcja | Wartość domyślna | Opis | 
| --- | --- | --- |
| Przeglądarka Podgląd markdown | `External` | Określa, gdzie danych wyjściowych RMarkdown HTML jest wyświetlany. `Internal`zawiera dokumentu RMarkdown HTML okna narzędzia w programie Visual Studio; `External` Wyświetla RMarkdown HTML za pomocą domyślnej przeglądarki. | 

## <a name="r-engine"></a>Aparat R

| Opcja | Wartość domyślna | Opis | 
| --- | --- | --- |
| Strona kodowa | `(OS Default)` | Ustawia R. strony kodowej (ustawienia regionalne) Domyślnie używa podstawowych ustawień regionalnych systemu operacyjnego. | 
| Dublowany sieci CRAN | `(Use .Rprofile)` | Ustawia dublowany sieci CRAN domyślnej instalacji pakietu. Domyślne ustawienie `Use .Rprofile` szanuje ustawienia sieci CRAN dublowania w Twojej `.RProfile` pliku. |
| Katalog roboczy | folder użytkownika | Ustawia jest bieżący katalog roboczy, który jest zwykle ustawiana tylko przy każdym otwarciu projektu. |

## <a name="workspace"></a>Obszar roboczy

| Opcja | Wartość domyślna | Opis | 
| --- | --- | --- |
| Obciążenia roboczego po otwarciu projektu | `No` | Ustawienie `Yes` umożliwia ładowanie danych sesji z `.RData` pliku do globalnego środowiska po otwarciu projektu. |
| Monituj o zapisanie obszaru roboczego na resetowanie | `Yes` | Ustawienie `No` Wyłącza monitowanie o zapisywanie obszaru roboczego po kliknięciu przycisku resetowania w oknie interaktywnym. |
| Zapisywanie obszaru roboczego po zamknięciu projektu | `No` | Ustawienie `Yes` umożliwia zapisywanie w środowisku globalne `.RData` plików, gdy projekt jest zamknięty. |
| Pokaż okno dialogowe potwierdzenia przed przełączeniem obszary robocze | `Yes` | Ustawienie `No` Wyłącza monitowanie użytkownika o potwierdzenie podczas przełączania między różnych obszarów roboczych. Zobacz [przełączanie między obszarami roboczymi](workspaces.md#switching-between-workspaces) |
 
