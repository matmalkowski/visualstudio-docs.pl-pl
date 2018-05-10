---
title: Instalowanie obsługi języka Python
description: Jak zainstalować narzędzia Python Tools dla programu Visual Studio (PTVS) w Visual Studio 2017 r. 2015, 2013, 2012 i 2010, łącznie z opcjami i lokalizację instalacji.
ms.date: 02/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 6f4af615091751f1076a5fe8659a8749fc41ca37
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Jak zainstalować obsługę języka Python w programie Visual Studio w systemie Windows

Aby zainstalować obsługę języka Python dla programu Visual Studio (znanej także jako narzędzi Python Tools for Visual Studio lub PTVS), postępuj zgodnie z instrukcjami w sekcji odpowiadający posiadanej wersji programu Visual Studio:

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 lub starszej](#visual-studio-2013-and-earlier)

Dla programu Visual Studio 2015 lub starszym należy również oddzielnie [instalowanie interpretera Python](installing-python-interpreters.md) wybranych przez użytkownika (Python 3.5 i wcześniej; 3,6 nie jest obsługiwana i generuje komunikat "Python nieobsługiwana wersja 3,6"). Tej samej stronie zawiera również instrukcje dotyczące dodawania istniejącego interpreter języka Python do programu Visual Studio 2017 r.

Aby szybko testowania obsługi języka Python po wykonaniu czynności instalacyjne, Otwórz okno interaktywne Python, naciskając klawisz Alt-I i wprowadzania `2+2`. Jeśli nie widzisz dane wyjściowe `4`, sprawdź ponownie wszystkie czynności.

> [!Tip]
> Obciążenie Python zawiera przydatne rozszerzenia Cookiecutter, które zawiera graficzny interfejs użytkownika do odnalezienia szablony, wprowadź opcje szablonu oraz tworzenie projektów i pliki. Aby uzyskać więcej informacji, zobacz [przy użyciu Cookiecutter](using-python-cookiecutter-templates.md).

> [!Note]
> Obsługa języka Python nie jest obecnie dostępna w programie Visual Studio dla komputerów Mac, ale jest dostępna w Mac i Linux za pomocą programu Visual Studio Code. Zobacz [pytania i odpowiedzi](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. Pobierz i Uruchom najnowszą wersję Instalatora programu Visual Studio 2017 r. Jeśli masz już zainstalowanego programu Visual Studio, uruchomić Instalator programu Visual Studio, wybierz **Modyfikuj** opcji (zobacz [zmodyfikować Visual Studio](../install/modify-visual-studio.md)) i przejdź do kroku 2.

    > [!div class="nextstepaction"]
    > <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Zainstaluj program Visual Studio 2017 Community</a>

    >[!Tip]
    > Wersja Community to dla indywidualnych deweloperów, uczenie klasy academic badań i rozwoju typu open source. Do innych celów, należy zainstalować <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Professional</a> lub <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Enterprise</a>.

1. Instalator wyświetla listę obciążeń, grup powiązane opcje dla rozwoju określonych obszarów. Dla języka Python, wybierz **programowania Python** obciążenia.

    ![Obciążenie programowania Python w Instalatorze programu Visual Studio](media/installation-python-workload.png)

    Opcjonalnie: podczas pracy z analizy danych, należy również rozważyć **nauki dane i aplikacje analitycznych** obciążenia. To obciążenie obejmuje obsługę języka Python, a także języków R i F #. Aby uzyskać więcej informacji, zobacz [nauki danych i obciążenia aplikacji analitycznych](../rtvs/data-science-and-analytical-applications-workload.md).

    > [!Note]
    > Python i analizy danych obciążenia są dostępne tylko w wersji Visual Studio 2017 15,2 i nowszym.

1. Po prawej stronie Instalatora wybierz dodatkowe opcje, w razie potrzeby. Pomiń ten krok, aby zaakceptować wartości domyślne.

    ![Opcje wdrażania języka Python w Instalatorze programu Visual Studio](media/installation-python-options.png)

    | Opcja | Opis |
    | --- | --- |
    | Dystrybucje Python | Wybierz dowolną kombinację wariantów 32-bitowe i 64-bitowe języka Python, 2, Python 3 Anaconda2 i Anaconda3 dystrybucji, które mają pracować z. Każdy zawiera dystrybucji interpreter środowiska uruchomieniowego i bibliotek. Anaconda, w szczególności to platforma nauki Otwórz danych, która zawiera szereg wstępnie zainstalowane pakiety. (Można powrócisz do Instalator programu Visual Studio w dowolnym momencie, aby dodać lub usunąć dystrybucje.)  **Uwaga**: Jeśli po zainstalowaniu dystrybucji poza Instalator programu Visual Studio, nie istnieje potrzeba do sprawdzenia odpowiednika tej opcji w tym miejscu. Visual Studio automatycznie wykrywa istniejącej instalacji języka Python. Zobacz [środowiska Python](managing-python-environments-in-visual-studio.md). |
    | Obsługa szablonów Cookiecutter | Instaluje Cookiecutter graficznego interfejsu użytkownika do odnalezienia szablony, wprowadź opcje szablonu oraz tworzenie projektów i pliki. Zobacz [przy użyciu rozszerzenia Cookiecutter](using-python-cookiecutter-templates.md). |
    | Obsługa sieci web języka Python | Instaluje narzędzia do tworzenia aplikacji sieci web w tym HTML, CSS i JavaScript edycji pomocy technicznej, wraz z szablonów dla projektów przy użyciu struktury Bottle, Flask i Django. Zobacz [szablony projektów sieci web języka Python](python-web-application-project-templates.md). |
    | Obsługa języka Python IoT | Obsługuje tworzenie Windows IoT Core za pomocą języka Python. |
    | Narzędzia deweloperskie macierzystego języka Python | Instaluje kompilator języka C++ i inne składniki niezbędne do opracowywania rozszerzeń macierzystego dla języka Python. Zobacz [Tworzenie rozszerzenia C++ dla języka Python](working-with-c-cpp-python-in-visual-studio.md). Zainstaluj również **tworzenia klasycznych aplikacji w języku C++** obciążenia dla pełnej obsługi języka C++. |
    | Azure podstawowe narzędzia usługi w chmurze | Udostępnia dodatkowe wsparcie dla deweloperów usług Azure Cloud Services w języku Python. Zobacz [projektów usług w chmurze Azure](python-azure-cloud-service-project-template.md). |

1. Po zakończeniu instalacji Instalator udostępnia opcje umożliwiające modyfikowanie, uruchamianie, napraw lub odinstaluj program Visual Studio. **Modyfikuj** przycisku zmienia się na **aktualizacji** podczas aktualizacji dla programu Visual Studio, kiedy aktualizacje są dostępne dla każdego zainstalowanych składników. (Opcja Modyfikuj, następnie jest dostępne w menu rozwijanym). Wyszukując "Visual Studio", można uruchomić Instalatora z menu Start systemu Windows i Visual Studio.

    ![Uruchamianie, modyfikowanie, modyfikowania lub odinstalowanie programu Visual Studio z Instalatorem](media/installation-vs-launch.png)

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo") | [Obejrzyj film (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Installing-Visual-Studio-Python-Support-go1id3LWE_1705918567) na temat instalowania obsługi języka Python w programie Visual Studio.|

### <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli wystąpią problemy, instalowanie i uruchamianie Python w programie Visual Studio, spróbuj wykonać następujące czynności:

- Określić, czy ten sam błąd wystąpi przy użyciu interfejsu wiersza polecenia języka Python, oznacza to, uruchamianie `python.exe` z wiersza polecenia.
- Użyj [opcja w Instalatorze programu Visual Studio naprawy](../install/repair-visual-studio.md).
- Naprawy lub ponownej instalacji języka Python za pomocą **Ustawienia > aplikacje i funkcje** w systemie Windows.

**Przykład błąd**: nie można uruchomić procesu interaktywnego: System.ComponentModel.Win32Exception (0x80004005): nieznany błąd (0xc0000135) Microsoft.PythonTools.Repl.PythonInteractiveEvaluator.d__43.MoveNext().

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Uruchom Instalator programu Visual Studio za pośrednictwem **Panel sterowania > programy i funkcje**, wybierając żądane **programu Microsoft Visual Studio 2015** , a następnie **zmiany**.

1. W Instalatorze, wybierz **Modyfikuj**.

1. Wybierz **języki programowania > Narzędzia Python Tools for Visual Studio** , a następnie **dalej**:

    ![Opcja PTVS w Instalatorze programu Visual Studio 2015](media/installation-vs2015.png)

1. Po zakończeniu instalacji programu Visual Studio [zainstalować interpreter języka Python wybranym](installing-python-interpreters.md). Jeśli masz już zainstalowany interpreter i Visual Studio nie wykryje on automatycznie, zobacz [ręcznie Zidentyfikuj istniejącego środowiska](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 lub starszej

1. Zainstaluj odpowiednią wersję narzędzi Python Tools for Visual Studio dla używanej wersji programu Visual Studio:

    - Visual Studio 2013: [PTVS 2.2 for Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2). **Plik > Nowy projekt** okno dialogowe w programie Visual Studio 2013 umożliwia skrótu dla tego procesu.
    - Program Visual Studio 2012: [PTVS 2.1 dla programu Visual Studio 2012](https://pytools.codeplex.com/downloads/get/920478)
    - Program Visual Studio 2010: [PTVS 2.1 dla programu Visual Studio 2010](https://pytools.codeplex.com/downloads/get/920479)

1. [Zainstaluj interpreter języka Python wybranym](installing-python-interpreters.md). Jeśli masz już zainstalowany interpreter i Visual Studio nie wykryje on automatycznie, zobacz [ręcznie Zidentyfikuj istniejącego środowiska](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment).

## <a name="install-locations"></a>Lokalizacje instalacji

Domyślnie obsługa języka Python jest zainstalowana dla wszystkich użytkowników na komputerze.

Dla programu Visual Studio 2017 r, Python obciążenie jest zainstalowany w `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\<VS_edition>Common7\IDE\Extensions\Microsoft\Python` gdzie &lt;VS_edition&gt; Community, Professional lub Enterprise.

Dla programu Visual Studio 2015 i starszych wersji ścieżki instalacji są następujące:

- 32-bitowe:
  - Ścieżka: `%Program Files(x86)%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Lokalizacja ścieżka rejestru: `HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS_ver>\InstallDir`
- 64-bitowe:
  - Ścieżka: `%Program Files%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Lokalizacja ścieżka rejestru: `HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS_ver>\InstallDir`

gdzie:

- &lt;VS_ver&gt; jest:
  - 14.0 dla programu Visual Studio 2015
  - 12.0 for Visual Studio 2013
  - 11.0 dla programu Visual Studio 2012
  - 10.0 dla programu Visual Studio 2010
- &lt;PTVS_ver&gt; jest numer wersji, takie jak 2.2, 2.1, 2.0, 1.5, 1.1 i 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Instalacje specyficzne dla użytkownika (1,5 i starsze)

Narzędzia Python Tools dla programu Visual Studio 1.5 i starszych dozwolone instalacji dla bieżącego użytkownika, w którym to przypadku ścieżka instalacji jest `%LocalAppData%\Microsoft\VisualStudio\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>` gdzie &lt;VS_ver&gt; i &lt;PTVS_ver&gt; są takie same, zgodnie z opisem powyżej.

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
