---
title: "Instalacja dla języka Python w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "11"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 066612a132bf6a092771afd5fc4a876d4b3be425
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="installing-python-support-in-visual-studio-on-windows"></a>Instalowanie obsługi języka Python w programie Visual Studio w systemie Windows

Aby zainstalować obsługę języka Python dla programu Visual Studio, postępuj zgodnie z instrukcjami w sekcji odpowiadający posiadanej wersji programu Visual Studio:

- [Visual Studio 2017 r.](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 lub starszej](#visual-studio-2013-and-earlier)

Dla programu Visual Studio 2015 lub starszym należy oddzielnie zainstalować interpreter języka Python wybranych przez użytkownika (Python 3.5 i wcześniej; 3,6 nie jest obsługiwane). Aby uzyskać więcej informacji, zobacz [środowiska Python](python-environments.md). Tej samej stronie zawiera również instrukcje dotyczące dodawania istniejącego interpreter języka Python do programu Visual Studio 2017 r.

Aby szybko testowania obsługi języka Python po wykonaniu czynności instalacyjne, Otwórz okno interaktywne Python, naciskając klawisz Alt-I i wprowadzania `2+2`. Jeśli nie widzisz dane wyjściowe `4`, sprawdź ponownie wszystkie czynności.

> [!Tip]
> Obciążenie Python zawiera przydatne rozszerzenia Cookiecutter, które zawiera graficzny interfejs użytkownika do odnalezienia szablony, wprowadź opcje szablonu oraz tworzenie projektów i pliki. Aby uzyskać więcej informacji, zobacz [przy użyciu Cookiecutter](cookiecutter.md).

> [!Note]
> Obsługa języka Python nie jest obecnie dostępna w programie Visual Studio dla komputerów Mac, ale jest dostępna w Mac i Linux za pomocą programu Visual Studio Code. Zobacz [pytania i odpowiedzi](python-in-visual-studio.md#questions-and-answers).

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. Pobierz i Uruchom najnowszą wersję Instalatora programu Visual Studio 2017:

    > [!div class="nextstepaction"]
    > <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Zainstaluj program Visual Studio 2017 Community</a>

    >[!Tip]
    > Wersja Community to dla indywidualnych deweloperów, uczenie klasy academic badań i rozwoju typu open source. Do innych celów, należy zainstalować <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Professional</a> lub <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Enterprise</a>.

1. Instalator wyświetla listę obciążeń, grup powiązane opcje dla rozwoju określonych obszarów. Dla języka Python, wybierz **programowania Python** obciążenia.

    ![Obciążenie programowania Python w Instalatorze programu Visual Studio](media/installation-python-workload.png)

    Opcjonalnie: podczas pracy z analizy danych, należy również rozważyć **nauki dane i aplikacje analitycznych** obciążenia. To obciążenie obejmuje obsługę języka Python, a także języków R i F #. Aby uzyskać więcej informacji, zobacz [nauki danych i obciążenia aplikacji analitycznych](../rtvs/data-science-workload.md).

    > [!Note]
    > Python i analizy danych obciążenia są dostępne tylko w wersji Visual Studio 2017 15,2 i nowszym.

1. Po prawej stronie Instalatora wybierz dodatkowe opcje, w razie potrzeby. Pomiń ten krok, aby zaakceptować wartości domyślne.

    ![Opcje wdrażania języka Python w Instalatorze programu Visual Studio](media/installation-python-options.png)

    | Opcja | Opis | 
    | --- | --- |
    | Dystrybucje Python | Wybierz dowolną kombinację wariantów 32-bitowe i 64-bitowe języka Python, 2, Python 3 Anaconda2 i Anaconda3 dystrybucji, które mają pracować z. Każdy zawiera dystrybucji interpreter środowiska uruchomieniowego i bibliotek. Anaconda, w szczególności to platforma nauki Otwórz danych, która zawiera wiele pakietów. (Można powrócisz do Instalator programu Visual Studio w dowolnym momencie, aby dodać lub usunąć dystrybucje.) |
    | Obsługa szablonów Cookiecutter | Instaluje Cookicutter graficznego interfejsu użytkownika do odnalezienia szablony, wprowadź opcje szablonu oraz tworzenie projektów i pliki. Zobacz [przy użyciu rozszerzenia Cookicutter](cookiecutter.md). |
    | Obsługa sieci web języka Python | Instaluje narzędzia do tworzenia aplikacji sieci web w tym HTML, CSS i JavaScript edycji pomocy technicznej, wraz z szablonów dla projektów przy użyciu struktury Bottle, Flask i Django. Zobacz [szablony projektów sieci web języka Python](template-web.md). |
    | Obsługa języka Python IoT | Obsługuje tworzenie Windows IoT Core za pomocą języka Python. |
    | Narzędzia deweloperskie macierzystego języka Python | Instaluje kompilator języka C++ i inne składniki niezbędne do opracowywania rozszerzeń macierzystego dla języka Python. Zobacz [Tworzenie rozszerzenia C++ dla języka Python](cpp-and-python.md). |
    | Azure podstawowe narzędzia usługi w chmurze | Udostępnia dodatkowe wsparcie dla deweloperów usług Azure Cloud Services w języku Python. Zobacz [zure projekty usługi w chmurze](template-azure-cloud-service.md). |

1. Po zakończeniu instalacji Instalator udostępnia opcje umożliwiające modyfikowanie, uruchamianie, napraw lub odinstaluj program Visual Studio. **Modyfikuj** przycisku zmienia się na **aktualizacji** podczas aktualizacji dla programu Visual Studio, kiedy aktualizacje są dostępne dla każdego zainstalowanych składników. (Opcja Modyfikuj, następnie jest dostępne w menu rozwijanym). Wyszukując "Visual Studio", można uruchomić Instalatora z menu Start systemu Windows i Visual Studio.

    ![Uruchamianie, modyfikowanie, modyfikowania lub odinstalowanie programu Visual Studio z Instalatorem](media/installation-vs-launch.png)


> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Installing-Visual-Studio-Python-Support-go1id3LWE_1705918567]

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Uruchom Instalator programu Visual Studio za pośrednictwem **Panel sterowania > programy i funkcje**, wybierając żądane **programu Microsoft Visual Studio 2015** , a następnie **zmiany**.

1. W Instalatorze, wybierz **Modyfikuj**.

1. Wybierz **języki programowania > Narzędzia Python Tools for Visual Studio** , a następnie **dalej**:

    ![Opcja PTVS w Instalatorze programu Visual Studio 2015](media/installation-vs2015.png)    

1. Po zakończeniu instalacji programu Visual Studio [zainstalować interpreter języka Python wybranym](python-environments.md#selecting-and-installing-python-interpreters). Jeśli masz już tłumacza zainstalowana, zobacz [tworzenia środowiska dla istniejących interpreter](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 lub starszej

1. Zainstaluj odpowiednią wersję narzędzi Python Tools for Visual Studio dla używanej wersji programu Visual Studio:

    - Visual Studio 2013: [PTVS 2.2 for Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2). **Plik > Nowy projekt** okno dialogowe w programie Visual Studio 2013 umożliwia skrótu dla tego procesu.
    - Program Visual Studio 2012: [PTVS 2.1 dla programu Visual Studio 2012](https://pytools.codeplex.com/downloads/get/920478)
    - Program Visual Studio 2010: [PTVS 2.1 dla programu Visual Studio 2010](https://pytools.codeplex.com/downloads/get/920479)

1. [Zainstaluj interpreter języka Python wybranym](python-environments.md#selecting-and-installing-python-interpreters). Jeśli masz już tłumacza zainstalowana, zobacz [tworzenia środowiska dla istniejących interpreter](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="install-locations"></a>Lokalizacje instalacji

Domyślnie obsługa języka Python jest zainstalowana dla wszystkich użytkowników na komputerze.

Dla programu Visual Studio 2017 r, Python obciążenie jest zainstalowany w `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\<VS_edition>Common7\IDE\Extensions\Microsoft\Python` gdzie &lt;VS_edition&gt; Community, Professional lub Enterprise.

Dla programu Visual Studio 2015 i starszych wersji ścieżki instalacji są następujące:

- 32-bitowe:
  - Ścieżka:`%Program Files(x86)%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Lokalizacja ścieżka rejestru:`HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS_ver>\InstallDir`
- 64-bitowe:
  - Ścieżka:`%Program Files%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Lokalizacja ścieżka rejestru:`HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS_ver>\InstallDir`

gdzie:

- &lt;VS_ver&gt; jest:    
    - 14.0 dla programu Visual Studio 2015
    - 12.0 dla programu Visual Studio 2013
    - 11.0 dla programu Visual Studio 2012
    - 10.0 dla programu Visual Studio 2010
- &lt;PTVS_ver&gt; jest numer wersji, takie jak 2.2, 2.1, 2.0, 1.5, 1.1 i 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Instalacje specyficzne dla użytkownika (1,5 i starsze)

Narzędzia Python Tools dla programu Visual Studio 1.5 i starszych dozwolone instalacji dla bieżącego użytkownika, w którym to przypadku ścieżka instalacji jest `%LocalAppData%\Microsoft\VisualStudio\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>` gdzie &lt;VS_ver&gt; i &lt;PTVS_ver&gt; są takie same, zgodnie z opisem powyżej.

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
