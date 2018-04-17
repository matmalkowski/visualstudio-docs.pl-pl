---
title: Zarządzanie projektami aplikacji Python
description: Objaśnienie jego przeznaczenia projekty w programie Visual Studio, pokazuje, jak utworzyć projektów i zarządzanie nimi dla kodu języka Python i opisano dostępne szablony inny projekt dla języka Python.
ms.custom: ''
ms.date: 03/05/2018
ms.technology:
- devlang-python
dev_langs:
- python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 9009dcb8ae65aa73b85d27458c14c1a866c321c3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="python-projects"></a>Projekty Python

Python aplikacje są zazwyczaj definiowane przy użyciu tylko plików i folderów, ale ta struktura może stać się złożona jako aplikacje większy i może obejmować automatycznie generowanej pliki JavaScript dla aplikacji sieci web i tak dalej. Projektu programu Visual Studio pomaga zarządzać tym złożoności. Projekt ( `.pyproj` pliku) identyfikuje źródła i pliki zawartości skojarzonej z projektem, zawiera informacje o kompilacji dla każdego pliku przechowuje informacje o integracji z systemami kontroli źródła i pomaga organizować aplikacji do składników logicznych.

![Python projekt w Eksploratorze rozwiązań](media/projects-solution-explorer.png)

Ponadto projekty zawsze są zarządzane w programie Visual Studio *rozwiązania*, który może zawierać dowolną liczbę projektów, które mogą odwoływać się do siebie. Na przykład projektów języka Python można odwoływać się do projektów C++, który implementuje moduł rozszerzenia. Z tej relacji programu Visual Studio automatycznie tworzy projektu C++ (w razie potrzeby), po rozpoczęciu debugowania projektu języka Python. (Aby uzyskać ogólne informacje, zobacz [rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).)

Program Visual Studio oferuje różne szablony projektów języka Python, aby szybko skonfigurować szereg struktury aplikacji, w tym szablonu, aby utworzyć projekt z istniejących drzewa folderów i szablon do tworzenia projektu czystą, pusty. Zobacz [szablony projektu](#project-templates) indeksu.

<a name="lightweight-usage-project-free"></a>

> [!Tip]
> Nawet bez projektu programu Visual Studio dobrze działa z kodu języka Python. Można na przykład otwórz Python pliku samodzielnie i korzystać z automatycznego zakończenia, IntelliSense i debugowanie (prawym przyciskiem myszy w edytorze i wybierając **Start [z | bez] debugowanie**). Ponieważ taki kod zawsze używa domyślnego środowiska globalnych, jednak mogą pojawić się błędy lub nieprawidłowe zakończeń Jeśli kod jest przeznaczona dla innego środowiska. Ponadto program Visual Studio analizuje wszystkie pliki i pakiety w folderze, w którym jeden plik jest otwarty, może zużywać znaczną czas procesora CPU.
>
> Zgodnie z opisem w jest proste sprawa do tworzenia projektu programu Visual Studio z istniejącego kodu [tworzenia projektu z istniejących plików](#creating-a-project-from-existing-files).

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo") | [Obejrzyj film (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Getting-Python-Code-iLAv23LWE_3905918567) wprowadzenie do projektów języka Python (2 m 17s). |
| ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo") | Zobacz też [nowości: Używanie kontroli źródła z projektów języka Python](https://youtu.be/Aq8eqApnugM) (witrynie youtube.com, 8 m 55s). |

## <a name="adding-files-assigning-a-startup-file-and-setting-environments"></a>Dodawanie plików, przypisanie pliku uruchamiania oraz ustawienia środowiska

Podczas opracowywania aplikacji zazwyczaj konieczne dodanie nowych plików o różnych typach do projektu. Dodawanie takich plików odbywa się przez kliknięcie prawym przyciskiem myszy projekt i wybierając **Dodaj > istniejący element...** . z którego przeglądania w poszukiwaniu pliku do dodania, lub **Dodaj > Nowy element...** , który wyświetla okno dialogowe z różnych szablonów elementów. Szablony obejmują python puste pliki, python klasy testu jednostkowego i różnych plików związanych z aplikacjami sieci web. Można sprawdzić te opcje z projektu testowego, aby dowiedzieć się, co jest dostępne w używanej wersji programu Visual Studio.

Każdy projekt Python ma jeden plik przypisanej rozruchu, czcionką pogrubioną w Eksploratorze rozwiązań. Uruchamiania jest plik, który jest uruchamiany po rozpoczęciu debugowania (F5 lub **Debuguj > Rozpocznij debugowanie**) lub po uruchomieniu projektu w oknie interaktywnym (Shift + Alt + F5 lub **debugowania > wykonanie projektu w języku Python Interakcyjne**). Aby go zmienić, kliknij prawym przyciskiem myszy nowy plik i wybierz **Ustaw jako plik uruchamiania**.

> [!Tip]
> Usuwanie plików wybranego uruchomienia z projektu i nie zaznaczenie nowego, Visual Studio będą wiedzieć, co Python pliku do uruchomienia z podczas próby uruchomienia projektu. W takim przypadku program Visual Studio 2017 wersji 15.6 i nowszych widoczny błąd; wcześniejszych wersji albo otwórz okno danych wyjściowych z interpreter języka Python uruchomiona, lub zobacz okno danych wyjściowych jest wyświetlana, ale następnie zniknąć niemal natychmiast. Jeśli wystąpiły którekolwiek z tych zachowań, sprawdź, czy plik przypisanej uruchamiania.
>
> Jeśli chcesz nie zamykaj okna dane wyjściowe jakiejkolwiek przyczyny, kliknij prawym przyciskiem myszy projekt, wybierz **właściwości**, wybierz pozycję **debugowania** , a następnie dodaj `-i` do **Interpreter argumentów**  pola. Ten argument powoduje, że interpreter przejść w trybie interakcyjnym, po zakończeniu programu, co utrzymywanie okna otwarte do momentu wprowadzenia Ctrl + Z Enter, aby wyjść.

Nowy projekt zawsze jest skojarzony z domyślnego środowiska Python globalnego. Aby skojarzyć projektu z innego środowiska (również w środowiskach wirtualnych), kliknij prawym przyciskiem myszy **środowiska Python** węzła w projekcie, wybierz opcję **środowiska Python Dodaj lub usuń**, i Wybierz te, które chcesz. Aby zmienić aktywnego środowiska, kliknij prawym przyciskiem myszy wymagane środowisko i wybierz **aktywacji środowiska** jak pokazano poniżej. Aby uzyskać więcej informacji, zobacz [wybierając środowisko dla projektu](selecting-a-python-environment-for-a-project.md).

![Aktywowanie środowisko dla projektów języka Python](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>Szablony projektu

Program Visual Studio pozwala na wiele sposobów, aby skonfigurować projekt języka Python, od początku lub z istniejącego kodu. Aby użyć szablonu, wybierz **Plik > Nowy > Projekt...**  polecenie menu, kliknij prawym przyciskiem myszy rozwiązanie w Eksploratorze rozwiązań i wybierz **Dodaj > Nowy projekt...** , które przywołać **nowy projekt** okna dialogowego poniżej. Aby wyświetlić szablony specyficzne dla języka Python, wyszukaj frazę "Python" lub wybierz **zainstalowana > Python** węzła:

![Okno dialogowe nowego projektu z szablonami Python](media/projects-new-project-dialog.png)

Poniższa tabela zawiera podsumowanie szablony dostępne w Visual Studio 2017 r (nie wszystkie szablony są dostępne wszystkie poprzednie wersje):

| Szablon | Opis |
| --- | --- |
| [Z istniejącego kodu języka Python](#creating-a-project-from-existing-files) | Tworzy projekt programu Visual Studio z istniejącego kodu języka Python w strukturze folderu.  |
| Aplikacji Python | Struktura podstawowego projektu dla nowej aplikacji Python z plikiem źródłowym jednej, pusty. Domyślnie, projekt jest uruchamiany w interpretera konsoli w domyślnej globalnej środowisko, w którym można zmienić [przypisywanie innego środowiska](selecting-a-python-environment-for-a-project.md). |
| [Usługi w chmurze Azure](python-azure-cloud-service-project-template.md) | Projekt usługi w chmurze Azure napisanych w języku Python. |
| [Projekty sieci Web](python-web-application-project-templates.md) | Projekty oparte na różnych platform, na przykład Bottle, Flask, Django i Flask/Jade serwerów sieci web. |
| IronPython aplikacji | Podobnie jak szablon aplikacji Python, ale IronPython przez domyślne włączenie .NET międzyoperacyjnego i trybu mieszanego debugowania w językach .NET. |
| Aplikacja IronPython WPF | Struktury projektu przy użyciu IronPython z plikami Windows Presentation Foundation XAML dla interfejsu użytkownika aplikacji. Program Visual Studio udostępnia projektanta XAML interfejsu użytkownika, związane z kodem mogą być napisane w języku Python i aplikacja jest uruchamiana bez wyświetlania konsoli. |
| Strony sieci Web IronPython Silverlight | Projekt IronPython, który jest uruchamiany w przeglądarce, za pomocą programu Silverlight. Kodu Python aplikacji znajduje się na stronie sieci web jako skryptu. Tag skryptu umożliwiającego ściąga dół niektórych kod JavaScript, która inicjuje IronPython działają w ramach Silverlight, z którego kodu Python mogą prowadzić interakcję z modelu DOM. |
| Aplikacji formularzy systemu Windows IronPython | Struktury projektu za pomocą withUI IronPython tworzone przy użyciu kodu z formularzy systemu Windows. Aplikacja jest uruchamiana bez wyświetlania konsoli. |
| Aplikacja w tle (IoT) | Obsługują wdrażanie projektów języka Python do uruchamiania jako usługi w tle na urządzeniach. Odwiedź stronę [Centrum deweloperów systemu Windows IoT](https://dev.windows.com/en-us/iot) Aby uzyskać więcej informacji. |
| Moduł rozszerzenia języka Python | Ten szablon jest dostępny w węźle Visual C++, jeśli po zainstalowaniu **Python natywnych narzędzi** z obciążeniem Python w Visual Studio 2017 (zobacz [instalacji](installing-python-support-in-visual-studio.md)). Struktura core zapewnia rozszerzenie DLL, podobnie jak opisany w C++ [Tworzenie rozszerzenia C++ dla języka Python](working-with-c-cpp-python-in-visual-studio.md). |

> [!Note]
> Ponieważ interpretacji języka Python, projektów języka Python w programie Visual Studio nie dają autonomicznego pliku wykonywalnego, podobnie jak inne projekty języka skompilowanych (C#, na przykład). Aby uzyskać więcej informacji, zobacz [pytania i odpowiedzi](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="create-project-from-existing-files"</a>

### <a name="creating-a-project-from-existing-files"></a>Tworzenie projektu z istniejących plików

> [!Important]
> Proces opisany w tym miejscu nie Przenieś lub skopiuj oryginalnych plików źródłowych. Jeśli chcesz pracować z kopią, najpierw zduplikowane folderu.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Pliki połączone

Pliki połączone są pliki, które zostały przeniesione do projektu, ale zazwyczaj znajdują się poza folderów projektu aplikacji. Pojawią się one w Eksploratorze rozwiązań jako normalne pliki za pomocą ikony nałożone skrótów: ![Ikona pliku łącza](media/projects-linked-file-icon.png)

Połączone pliki zostały określone w `.pyproj` plik za pomocą `<Compile Include="...">` elementu. Pliki połączone są użycie ścieżki względnej poza struktury katalogów, jawnych ani niejawnych użycie ścieżki w Eksploratorze rozwiązań:

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Połączone pliki są ignorowane w dowolnej z następujących warunków:

- Połączony plik zawiera łącze metadanych i ścieżka określona w życie atrybutu Include w katalogu projektu
- Połączony plik duplikaty pliku znajdującego się w hierarchii projektu
- Połączony plik zawiera łącze metadanych i ścieżki łącza jest ścieżką względną poza hierarchii projektu
- Ścieżka łącza jest ścieżką do katalogu głównego

### <a name="working-with-linked-files"></a>Praca z plikami połączonego

Aby dodać istniejący element jako łącza, kliknij prawym przyciskiem myszy folder w projekcie, w miejsce którego chcesz dodać plik, a następnie wybierz **Dodaj > Kończenie elementu...** . W oknie dialogowym, wybierz plik i wybierz **Dodaj jako Link** z listy rozwijanej na **Dodaj** przycisku. Pod warunkiem, że nie ma żadnych plików powodujące konflikt, to polecenie tworzy łącze w wybranym folderze. Jednak łącze nie została dodana, jeśli istnieje już plik o takiej samej nazwie lub łącze do tego pliku już istnieje w projekcie.

Jeśli spróbujesz łącza do pliku, który już istnieje w folderze projektu jest dodawany jako zwykłego pliku, a nie jako łącze. Aby przekonwertować pliku łącza, wybierz polecenie **Plik > Zapisz jako** można zapisać pliku do lokalizacji poza hierarchii projektu; Visual Studio automatycznie konwertuje go na łącze. Podobnie można przekonwertować łącze przywrócić za pomocą **Plik > Zapisz jako** można zapisać pliku gdzieś w hierarchii projektu. 

Jeśli przenosisz połączony plik w Eksploratorze rozwiązań, link jest przenoszony, ale nie wpływa na rzeczywisty plik. Podobnie łącze usunięcie łącza bez wpływu na plik.

Nie można zmienić nazwy plików połączonych.

## <a name="references"></a>Odwołania

Dodawanie odwołań do projektów i rozszerzenia, które są wyświetlane w obszarze obsługi projektów programu Visual Studio **odwołania** węzła w Eksploratorze rozwiązań:

![Odwołania do rozszerzenia w projektów języka Python](media/projects-extension-references.png)

Odwołania do rozszerzenia zwykle wskazuje współzależności między projektami i służą do zapewniania IntelliSense w czasie projektowania lub łączenie w czasie kompilacji. Projekty języka Python używać odwołań w podobny sposób, ale ze względu na specyfikę dynamicznej języka Python głównie służą one w czasie projektowania, aby zapewnić lepsze IntelliSense. One mogą służyć do wdrożenia na Microsoft Azure można zainstalować dodatkowe zależności.

### <a name="extension-modules"></a>Moduły rozszerzenia

Odwołanie do `.pyd` plik umożliwia IntelliSense dla wygenerowanego modułu. Visual Studio ładuje `.pyd` plików jest ładowany do interpreter języka Python i introspects jego typy i funkcje. Ponadto próbuje analizowanie ciągów doc dla funkcji w celu zapewnienia pomocy podpisu.

Jeśli w dowolnym momencie moduł rozszerzenie zostanie zaktualizowane na dysku, Visual Studio zerwano modułu w tle. Ta akcja nie ma wpływu na zachowania w czasie wykonywania, ale niektóre zakończeń nie są dostępne do czasu ukończenia analizy.

Może być również konieczne dodanie [ścieżki wyszukiwania](search-paths.md) do folderu zawierającego modułu.

### <a name="net-projects"></a>Projekty platformy .NET

Podczas pracy z IronPython, można dodać odwołania do zestawów platformy .NET, aby włączyć IntelliSense. .NET projektów w rozwiązaniu, kliknij prawym przyciskiem myszy **odwołania** węzła w projekcie języka Python, wybierz opcję **Dodaj odwołanie**, wybierz pozycję **projektów** , a następnie przejdź do żądany projekt. Biblioteki DLL pobrane oddzielnie, można wybrać **Przeglądaj** karcie zamiast tego i przejdź do żądanego pliku DLL.

Ponieważ odwołań w IronPython nie są dostępne, dopóki wywołania `clr.AddReference('AssemblyName')` jest wprowadzone, należy również dodać `clr.AddReference` wywołania do zestawu.

### <a name="webpi-projects"></a>Projekty WebPI

Możesz dodać odwołania do pozycji produktu WebPI wdrożenia usług chmurowych firmy Microsoft Azure z których można zainstalować dodatkowe składniki za pośrednictwem WebPI źródła danych. Domyślnie źródła danych, wyświetlany jest specyficzne dla języka Python i obejmuje Django, języka CPython i inne składniki podstawowe. Można również wybrać własne źródła danych, jak pokazano poniżej. Podczas publikowania do systemu Microsoft Azure, zadania Instalator instaluje wszystkich produktów, do którego istnieje odwołanie.

![WebPI odwołań](media/projects-webPI-components.png)