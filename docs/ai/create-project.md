---
ms.technology: vs-ai-tools
ms.openlocfilehash: 999e57f9b9b873f44f5a1ef0edac94c7e2b53ac4
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
ms.locfileid: "29709365"
---
# <a name="create-an-ai-project-from-a-template-in-visual-studio"></a>Tworzenie projektu AI z szablonu w programie Visual Studio

Po wprowadzeniu [zainstalowany program Visual Studio Tools dla AI](installation.md), ułatwia tworzenie nowego projektu AI przy użyciu różnych szablonów.

1. Uruchom program Visual Studio.

1. Wybierz **Plik > Nowy > Projekt** (Ctrl + Shift + N). W **nowy projekt** okno dialogowe, wyszukaj "**narzędzia AI**" i wybierz szablon ma. Należy pamiętać, że wybranie szablonu wyświetla krótki opis zawiera jakie szablonu.

    ![Okno dialogowe Nowy projekt VS2017 z szablonu Python](media\create-project\new-ai-project.png)

1. Dla tego przewodnika Szybki Start, wybierz "**aplikacji TensorFlow**" szablonu, nadaj projektu nazwę (na przykład "MNIST") i lokalizację, a następnie wybierz **OK**.

1. Program Visual Studio tworzy plik projektu ( `.pyproj` pliku na dysku) oraz inne pliki zgodnie z opisem w szablonie. Przy użyciu szablonu "TensorFlow aplikacji" Projekt zawiera jeden plik o nazwie takiej jak projektu. Plik jest otwarty w edytorze programu Visual Studio domyślnie.

    ![Projekt wynikowy przy użyciu szablonu aplikacji Python](media\create-project\new-tensorflowapp.png)

1. Należy zauważyć, że kod importuje już kilka bibliotek, w tym TensorFlow numpy sys i systemu operacyjnego. Ponadto możesz już aplikacji rozpoczyna się od niektóre argumenty wejściowe umożliwia łatwe przełączenie lokalizacji danych wejściowych szkolenia, modeli danych wyjściowych i pliki dziennika. Te parametry są przydatne podczas przesyłania zadań do wielu kontekstów obliczeń (ie inny katalog z pola lokalnego deweloperów niż w udziale plików Azure).

1. Projekt zawiera także niektóre właściwości utworzony ułatwia debugowanie aplikacji przez automatyczne przekazywanie argumentów wiersza polecenia dla tych parametrów wejściowych. **Kliknij prawym przyciskiem myszy** następnie wybierz projekt **właściwości**

    ![Właściwości](media\create-project\project-properties.png)

1. Kliknij przycisk **debugowania** kartę, aby wyświetlić argumenty skryptu automatycznie dodane. Możesz je zmienić zgodnie z potrzebami, na którym znajduje się dane wejściowe i gdzie chcesz przechowywane dane wyjściowe.

    ![Właściwości](media\create-project\/project-properties_1.png)

1. Uruchom program, naciskając klawisze Ctrl + F5 lub wybranie **Debuguj > Uruchom bez debugowania** w menu. Wyniki są wyświetlane w oknie konsoli.
