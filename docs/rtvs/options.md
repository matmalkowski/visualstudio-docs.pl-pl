---
title: "R narzędzia Opcje w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
f1_keywords:
- vs.toolsoptionspages.text_editor.r.advanced
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: dd21ba3c54ed274f181c036ed0121d8d3c5a180e
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2017
---
# <a name="r-tools-for-visual-studio-options"></a>Narzędzia języka R w opcjach programu Visual Studio

Opcje i ustawienia właściwe dla języka R są dostępne przy użyciu poniższych metod. Musisz wybrać **Pokaż wszystkie ustawienia** u dołu **opcje** wszystkich tych sekcjach, aby można było wyświetlane okno dialogowe.

- Opcje formatowania kodu (zobacz [opcji edytora](code-editing.md#editor-options): **Narzędzia > Opcje** menu, następnie wybierz **Edytor tekstu > R > Formatowanie**
- Opcje linting (zobacz [Linting](code-linting.md)): **Narzędzia > Opcje** menu, następnie wybierz **Edytor tekstu > R > wierszu**
- Zaawansowane opcje edytora ([opisanych w tym temacie](#text-editor-r-advanced-options)): **Narzędzia > Opcje** menu, następnie wybierz **Edytor tekstu > R > Zaawansowane**
- Opcje zachowania ([opisanych w tym temacie](#r-tools-advanced-options)): **R Narzędzia > Opcje** menu lub **Narzędzia > Opcje**, następnie przewiń do **narzędzia R**.

**Narzędzia R > Ustawienia nauki danych** polecenie dotyczy również wiele różnych ustawień w programie Visual Studio ogólnej. To polecenie jest opisany w następnej sekcji.

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>Narzędzia języka R > Ustawienia nauki danych

**Narzędzia R > Ustawienia nauki danych** element menu konfiguruje środowiska IDE programu Visual Studio z układem, który jest zoptymalizowana pod kątem potrzeb analityków danych. W szczególności tej opcji otwiera [Interactive](interactive-repl.md), [Explorer zmiennej](variable-explorer.md), i [obszarów roboczych](workspaces.md) systemu windows:

![Układ okna naukowca danych w programie Visual Studio](media/installation-data-scientist-layout-result.png)

Aby później przywrócić pozostałe ustawienia programu Visual Studio, należy najpierw użyć **Narzędzia > Import i eksport ustawień** polecenia select **Eksportuj wybrane ustawienia środowiska**i określ nazwę pliku. Aby przywrócić te ustawienia, użyj tego samego polecenia, a następnie wybierz **Importuj wybrane ustawienia środowiska**. Umożliwia także te same polecenia po zmianie układu naukowca danych i chcesz do niej powrócić w późniejszym czasie na zamiast używania **ustawienia nauki danych** polecenia bezpośrednio.

## <a name="text-editor--r--advanced-options"></a>Edytor tekstu > R > Opcje zaawansowane

Te opcje umożliwiają kontrolowanie zachowania formatowania, IntelliSense, obramowanie, wcięcia i składni sprawdzanie R.

![Okno dialogowe Opcje dla opcje zaawansowane edytora tekstu R](media/options-dialog-advanced-text-editor.png)

Każda opcja ustawiono lub wyłącz kontrolowania zachowania w. Szczegółowe informacje o każdej opcji wpływa można znaleźć w okienku pomocy w dolnej części okna dialogowego. Należy pamiętać, przeciągnąć górnej części okienka Pomocy do Sprawdź okienko większy.

![Rozszerzona okienko pomocy w oknie dialogowym Zaawansowane opcje edytora tekstowego R](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>R Narzędzia > Opcje zaawansowane

**R Narzędzia > Opcje** otwiera menu polecenie **opcje** okna dialogowego Opcje R:

  ![Okno dialogowe Opcje dla narzędzi R](media/options-dialog.png)

W poniższych sekcjach opisano różne opcje dostępne na tej stronie.

### <a name="debugging"></a>Debugowanie

Te opcje umożliwiają kontrolowanie sposobu obsługi wartości w [Explorer zmiennej](variable-explorer.md) w oknach debugera czujki i zmienne lokalne (zobacz [debugowanie](debugging.md)).

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Ocena active powiązania | `True` | Gdy `True`, zapewnia zawsze widzieć najnowsze wartości podczas sprawdzania zmiennych i właściwości. Ryzyko jest, że obliczania wyrażenia może powodować efekty uboczne, w zależności od tego, jak zostały wprowadzone. |
| Pokaż zmienne poprzedzona kropką | `False` | Określa, czy zmienne prefiksem `.` są wyświetlane. |

### <a name="grid-view"></a>Widok siatki

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Dynamiczne oceny | `False` | Domyślnie `View(<expression>)` funkcja wykonuje migawkę danych jako ramki danych, jaką może wykorzystać znaczne pamięci o dużych zestawów danych. Ustawienie tej opcji na `True` oznacza, że wyrażenie jest obliczane, gdy siatki odświeża można pobrać tylko te dane, która jest wyświetlana. Jednak w przypadku zmiany wyrażenie również zmiany danych, które mogą być nieodpowiednie dla dplyr pip wyrażeń. |

### <a name="help"></a>Pomoc

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Przeglądarki sieci Web F1 | `Internal` | Określa, jak uzyskać pomoc jest wyświetlane, gdy wyszukiwany termin przy użyciu klawiszy Ctrl + F1. Jeśli wartość `Internal`, pomoc jest renderowany w ramach okna narzędzia w programie Visual Studio. Jeśli wartość `External`, pomoc jest wyświetlany w domyślnej przeglądarce sieci web. |
| F1 Ciąg wyszukiwania sieci Web | `R site:stackoverflow.com` | Określa, jak warunki wyszukiwania są przekazywane do aparat wyszukiwania, po naciśnięciu klawiszy Ctrl + F1 termin w edytorze. Domyślnie ten ciąg jest `R site:stackoverflow.com`, które dołącza `R` do wyszukiwanego terminu. `site:stackoverflow.com` Jest dyrektywą do aparatu wyszukiwania z instrukcją, aby zawęzić zakres wyszukiwania do stron w obrębie `stackoverflow.com` domeny. |
| R pomocy przeglądarki | `Automatic` | Określa, jak pomoc jest wyświetlany podczas wyszukiwania w dokumentacji R przy użyciu F1, `?`, lub `??`. Jeśli wartość `Automatic`, renderuje pomocy w oknie odpowiednie. Na przykład pomocy HTML pojawi się okna narzędzia Visual Studio, plików PDF znajdują się w domyślnym programie PDF. Jeśli wartość `External`, pomoc jest renderowany w domyślnej przeglądarce sieci web. |

### <a name="history"></a>Historia

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Zawsze zapisuj historii | `True` | Określa, czy RTVS zapisuje historii poleceń do `.RHistory` plików w katalogu roboczym, gdy projekt jest zamknięty. Zapisywanie historii odbywa się nawet wtedy, gdy nie można zapisać projekt przed zakończeniem pracy. |
| Resetuj filtr wyszukiwania | `True` | Określa, czy okno Historia można filtrować historii poleceń do wyświetlenia wyłącznie z poleceniami, które podciąg dopasowywania termin filtr w oknie dialogowym Historia R. To ustawienie określa, czy można zresetować historii filtru wyszukiwania zawsze, gdy nowe polecenie Uruchom lub przełącz się do nowego projektu, który wyzwala ładowania innej `.RHistory` pliku. Domyślne ustawienie `True` minimalizuje niespodziewanego, gdy należy uruchomić polecenie z zestaw filtrów i zastanawiasz się, dlaczego polecenie został przeprowadzony nie pojawiają się w historii. |
| Zaznacz pole wyboru wielowierszowy | `True` | Określa, czy wiele wierszy instrukcji można wybrać w historii za pomocą jednego kliknięcia. Strzałka nawigacji interaktywnego systemu Windows w górę lub w dół umożliwia również instrukcje zamiast wierszy. |

### <a name="html"></a>HTML

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Przeglądarka strony HTML | `External` | Określa, gdzie zawartości, takich jak `ggvis` wykres, lub `shiny` aplikacji jest renderowany. `Internal`Pokazuje danych wyjściowych HTML w oknie narzędzia w programie Visual Studio; `External` wyświetla danych wyjściowych HTML w domyślnej przeglądarce. |

### <a name="logging"></a>Rejestrowanie

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Zdarzenia dziennika | `Normal` | Określa poziom szczegółowości rejestrowania używane RTVS diagnostyki. Domyślne ustawienie `Normal` tworzy plik dziennika w Twojej `TEMP` katalogu. Jeśli wartość `Traffic`, RTVS dzienników wszystkich poleceń i odpowiedzi w sesji. Te pliki dziennika nigdy nie pozostaw na komputerze, ale może okazać się przydatne przy diagnozowaniu problemów w RTVS. |

### <a name="markdown"></a>Język znaczników markdown

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Przeglądarka Podgląd markdown | `External` | Określa, gdzie danych wyjściowych RMarkdown HTML jest wyświetlany. `Internal`zawiera dokumentu RMarkdown HTML okna narzędzia w programie Visual Studio; `External` Wyświetla RMarkdown HTML za pomocą domyślnej przeglądarki. |

### <a name="r-engine"></a>Aparat R

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Strona kodowa | `(OS Default)` | Ustawia R. strony kodowej (ustawienia regionalne) Domyślnie używa podstawowych ustawień regionalnych systemu operacyjnego. | 
| Dublowany sieci CRAN | `(Use .Rprofile)` | Ustawia dublowany sieci CRAN domyślnej instalacji pakietu. Domyślne ustawienie `Use .Rprofile` szanuje ustawienia sieci CRAN dublowania w Twojej `.RProfile` pliku. |

### <a name="workspace"></a>Obszar roboczy

| Opcja | Wartość domyślna | Opis |
| --- | --- | --- |
| Obciążenia roboczego po otwarciu projektu | `No` | Ustawienie `Yes` umożliwia ładowanie danych sesji z `.RData` pliku do globalnego środowiska po otwarciu projektu. |
| Monituj o zapisanie obszaru roboczego na resetowanie | `Yes` | Ustawienie `No` Wyłącza monitowanie o zapisywanie obszaru roboczego po kliknięciu przycisku resetowania w oknie interaktywnym. |
| Zapisywanie obszaru roboczego po zamknięciu projektu | `No` | Ustawienie `Yes` umożliwia zapisywanie w środowisku globalne `.RData` plików, gdy projekt jest zamknięty. |
| Pokaż okno dialogowe potwierdzenia przed przełączeniem obszary robocze | `Yes` | Ustawienie `No` Wyłącza monitowanie użytkownika o potwierdzenie podczas przełączania między różnych obszarów roboczych. Zobacz [przełączanie między obszarami roboczymi](workspaces.md#switching-between-workspaces) |
| Pokazuje wskaźnika obciążenia komputera | `False` | Określa widoczność wskaźnika obciążenia procesora CPU i pamięci/sieci na pasku stanu. Ponieważ wskaźnika ponosi ruchu sieciowego, warto przechowywać to `False` w scenariuszach naliczane zdalnego. Zmiana tej opcji wymaga ponownego uruchomienia programu Visual Studio. |
