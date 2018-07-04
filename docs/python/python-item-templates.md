---
title: Szablony elementów dla projektów języka Python
description: Odwołanie do listy szablonów elementów dla projektów języka Python, które są dostępne za pośrednictwem Dodaj > okno dialogowe Nowy element w programie Visual Studio.
ms.date: 04/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 9811905e842eeb62399ef3b88558ee0286b05c84
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
ms.locfileid: "32032813"
---
# <a name="python-item-templates"></a>Szablony elementów języka Python

Szablony elementów są dostępne w projektów języka Python za pomocą **projektu** > **Dodaj nowy element** polecenia menu lub **Dodaj**  >  **Nowy element** polecenia w menu kontekstowym w **Eksploratora rozwiązań**.

![Dodaj nowy element — okno dialogowe](media/project-item-templates.png)

Przy użyciu nazwy Podaj dla elementu, szablon zazwyczaj tworzy jeden lub więcej plików i folderów znajdujących się w folderze aktualnie wybranego w projekcie (prawym przyciskiem myszy folder, aby wyświetlić menu kontekstowe automatycznie wybiera tego folderu). Dodawanie elementu obejmuje projektu programu Visual Studio, a element jest wyświetlany w **Eksploratora rozwiązań**.

Poniższa tabela zawiera krótkie opisy efekt każdego szablonu elementu w projekcie języka Python:

| Szablon | Szablon tworzy |
| --- | --- |
| Plik Python pusty | Pusty plik o `.py` rozszerzenia. |
| Klasa języka Python | A `.py` plik zawierający pojedynczy pusty definicji klasy języka Python. |
| Pakiet języka Python | Folder, który zawiera `__init.py__` pliku. |
| Testu jednostkowego języka Python | A `.py` na podstawie pliku z testu jednostkowego pojedynczego `unittest` framework wraz z wywołania `unittest.main()` Aby uruchomić testy w pliku. |
| Strony HTML | `.html` Pliku ze strukturą prosta strona składające się z `<head>` i `<body>` elementu. |
| JavaScript | Pusta `.js` pliku. |
| Arkusz stylów | A `.css` plik zawierający stylu pusty `body` |
| Plik tekstowy | Pusta `.txt` pliku. |
| Aplikacja Django 1.9<br/>Aplikacja Django 1.4 | Folder o nazwie aplikacji, która zawiera podstawowe pliki dla aplikacji Django, zgodnie z objaśnieniem w [Learning Django w programie Visual Studio, krok 2-2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) dla Django 1.9. Dla Django 1.4 `migrations` folderu, `admin.py` pliku i `apps.py` pliku nie są uwzględniane. |
| Okno IronPython WPF | Okno programu WPF składające się z dwóch plików side-by-side: `.xaml` pliku, który definiuje `<Window>` z pustą `<Grid>` elementu i skojarzone `.py` pliku, który ładuje plik XAML, używając `wpf` biblioteki. Zwykle używanych w ramach projektu, utworzone za pomocą jednego z szablonów projektu IronPython. Zobacz [Zarządzanie projektów języka Python — szablony projektów](managing-python-projects-in-visual-studio.md#project-templates). |
| Pliki obsługi roli sieci Web | A `bin` folder w katalogu głównym projektu (niezależnie od wybranego folderu w projekcie). Folder zawiera domyślny skrypt wdrożenia i `web.config` pliku role sieci web usługi w chmurze Azure. Ten szablon zawiera również `readme.html` pliku, który zawiera szczegółowe informacje. |
| Pliki obsługi roli procesu roboczego | A `bin` folder w katalogu głównym projektu (niezależnie od wybranego folderu w projekcie). Folder zawiera domyślne wdrożenie, a następnie uruchom skrypt, wraz z `web.config` pliku dla roli proces roboczy usługi w chmurze Azure. Ten szablon zawiera również `readme.html` pliku, który zawiera szczegółowe informacje. |
| Azure w pliku web.config (FastCGI) | A `web.config` pliku, który zawiera wpisy dla aplikacji korzystających z [WSGI](https://wsgi.readthedocs.io/en/latest/) obiektu do obsługi połączeń przychodzących. Ten plik jest zazwyczaj wdrażani do głównego serwera sieci web usług IIS, takie jak usługi Azure App Service. Aby uzyskać więcej informacji, zobacz [publikowania w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md). |
| Azure w pliku web.config (HttpPlatformHandler) | A `web.config` pliku, który zawiera wpisy dla aplikacji, które nasłuchują na gniazdo dla połączeń przychodzących. Ten plik jest zazwyczaj wdrażani do głównego serwera sieci web usług IIS, takie jak usługi Azure App Service. Aby uzyskać więcej informacji, zobacz [publikowania w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md). |
| Plik web.config Azure pliki statyczne | A `web.config` zazwyczaj są dodawane do pliku `static` folderu (lub inne folderu zawierającego elementy statyczne), można wyłączyć Python obsługi dla tego folderu. Ten plik konfiguracji działa w połączeniu z jednym z tych FastCGI lub HttpPlatformHandler konfiguracji plików. Aby uzyskać więcej informacji, zobacz [publikowania w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md). |
| Azure zdalnego debugowania pliku web.config | A `web.config.debug` plik, który umożliwia debugowanie zdalne przez protokół WebSockets, alongside `Microsoft.PythonTools.WebRole.dll` i `ptvsd` folderu zawierającego moduły, aby wdrożyć na serwerze, aby włączyć debugowanie zdalne. Zwykle utworzyć ten element w tym samym miejscu jako sieci `web.config` pliku. Aby uzyskać więcej informacji, zobacz [zdalne debugowanie kodu Python na platformie Azure](debugging-remote-python-code-on-azure.md). Zobacz też Uwaga poniżej. |

> [!Note]
> Jeśli dodasz debugowanie `web.config` szablon projektu i zamierzasz używać zdalnego debugowania języka Python, należy opublikować witrynę w konfiguracji "Debug". To ustawienie jest oddzielony od bieżącej konfiguracji aktywne rozwiązanie i zawsze domyślnie "Wersja". Aby go zmienić, otwórz **ustawienia** karcie i użyj **konfiguracji** pola kombi w Kreatorze publikowania. (Zobacz [dokumentacji platformy Azure](https://azure.microsoft.com/develop/python/) Aby uzyskać więcej informacji na temat tworzenia i wdrażania aplikacji sieci Web Azure.)
>
> ![Zmienianie konfiguracji publikowania](media/template-web-publish-config.png)

## <a name="see-also"></a>Zobacz także

- [Zarządzanie projektami Python — szablony projektu](managing-python-projects-in-visual-studio.md#project-templates)
- [Szablony projektów sieci web języka Python](python-web-application-project-templates.md)
- [Publikowanie w usłudze Azure app service](publishing-python-web-applications-to-azure-from-visual-studio.md)