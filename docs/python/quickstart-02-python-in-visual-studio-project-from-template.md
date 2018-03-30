---
title: Szybki Start — tworzenie za pomocą szablonu projektu języka Python | Dokumentacja firmy Microsoft
description: W tym Szybki Start tworzenia projektu programu Visual Studio dla języka Python za pomocą wbudowanych szablonów dla Podstawowa aplikacja platformy Flask.
ms.custom: mvc
ms.date: 03/22/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 2d4d81676d9f63751455f4f51ae5993c46dd0f04
ms.sourcegitcommit: 064f8678f4a918e1dce60285090a9803d37dc34b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2018
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Szybki Start: Tworzenie projektu języka Python z szablonu w programie Visual Studio

Po wprowadzeniu [zainstalowane obsługę języka Python w Visual Studio 2017](installing-python-support-in-visual-studio.md), ułatwia tworzenie nowego projektu Python przy użyciu różnych szablonów. Ta opcja szybkiego startu służy do tworzenia prostej aplikacji platformy Flask przy użyciu szablonu. Projekt wynikowy jest podobny do projektu, należy utworzyć ręcznie za pomocą [Szybki Start — tworzenie aplikacji sieci web w usłudze platformy Flask](../ide/quickstart-python.md).

1. Uruchom program Visual Studio 2017 r.

1. Na pasku menu u góry wybierz **Plik > Nowy > Projekt...** , a następnie w **nowy projekt** okno dialogowe Wyszukiwanie "flask puste", wybierz szablon "Pusty projekt sieci Web platformy Flask" na liście środkowej, nadaj nazwę projektu i wybierz **OK**:

    ![Tworzenie nowego projektu za pomocą szablonu projektu sieci Web platformy Flask puste](media/quickstart-python-06-blank-flask-template.png)

1. Visual Studio wyświetli okno dialogowe z informacją, "ten projekt wymaga pakiety zewnętrzne". To okno dialogowe pojawia się, ponieważ szablon zawiera `requirements.txt` pliku określania zależności na platformy Flask. Visual Studio może automatycznie zainstalować te pakiety i daje możliwość zainstalowania ich *środowiska wirtualnego*. Przy użyciu środowiska wirtualnego zamiast zaleca się instalowanie w środowisku globalnych, dlatego wybierz **zainstalować w środowisku wirtualnym** aby kontynuować.

    ![Instalowanie platformy Flask w środowisku wirtualnym](media/quickstart-python-07-install-into-virtual-environment.png)

1. Wyświetla programu Visual Studio **Dodawanie środowiska wirtualnego** okna dialogowego. Zaakceptuj wartość domyślną, a następnie wybierz **Utwórz**, następnie wyrazić zgodę na wszystkie żądania podniesienia uprawnień.

    > [!Tip]
    > Po rozpoczęciu projektu jest zdecydowanie zalecane od razu utworzyć środowisko wirtualne jak większość szablonów programu Visual Studio zaprosić podczas wykonywania. Środowiska wirtualne Obsługa dokładne wymagania dotyczące projektu w czasie, jak dodać i usunąć biblioteki. Następnie można łatwo wygenerować `requirements.txt` pliku, który umożliwia ponowne zainstalowanie tych zależności na innych komputerach Programowanie (jako gdy za pomocą kontroli źródła) i w przypadku wdrażania projektu na serwerze produkcyjnym. Aby uzyskać więcej informacji w środowiskach wirtualnych i ich korzyści, zobacz [za pomocą środowisk wirtualnych](../python/selecting-a-python-environment-for-a-project.md#using-virtual-environments) i [zarządzania wymagane pakiety z pliku requirements.txt](../python/managing-required-packages-with-requirements-txt.md).

1. Gdy program Visual Studio utworzy tego środowiska, Szukaj w **Eksploratora rozwiązań** aby zobaczyć, czy masz `app.py` plików wraz z programem `requirements.txt`. Otwórz `app.py` aby zobaczyć, że szablon dostarczył kodu tak jak w [Szybki Start — tworzenie aplikacji sieci web w usłudze platformy Flask](../ide/quickstart-python.md), przy użyciu dwóch dodane sekcje.

    Najpierw jest to wiersz `wsgi_app = app.wsgi_app` które mogą być przydatne podczas wdrażania aplikacji na serwerze sieci web.

    Drugi jest uruchamianie kodu, który można ustawić hosta i portu za pomocą zmiennych środowiskowych, zamiast kodować je. Taki kod, można łatwo zarządzać konfiguracji na komputerach zarówno rozwoju i produkcji, bez konieczności zmieniania kodu:

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. Wybierz **Debuguj > Uruchom bez debugowania** do uruchomienia aplikacji, a następnie otwórz w przeglądarce `localhost:5555`.

**Pytanie: Jakie Python szablony programu Visual Studio oferuje?**

**Odpowiedzi**: Z obciążeniem Python zainstalowany, program Visual Studio oferuje różne szablony projektów, między innymi [Flask i Django oraz Bottle platformy sieci web](../python/python-web-application-project-templates.md), usług w chmurze Azure, różnych uczenia maszynowego scenariusze, a nawet szablonu do utworzenia projektu z istniejącej struktury folderu zawierającego aplikację języka Python. Możesz przejść do nich za pośrednictwem **Plik > Nowy > Projekt...**  okno dialogowe, wybierając **Python** węzeł języka i jego węzły podrzędne.

Program Visual Studio oferuje również różnych plików lub *elementu szablony* do szybkiego tworzenia klasy języka Python, pakiet języka Python, testu jednostkowego języka Python i plikach web.config. Jeśli masz projektów języka Python, otwórz dostęp szablonów elementów za pomocą **projektu > Dodaj nowy element...**  polecenia menu.

Za pomocą szablonów można zaoszczędzić znaczących godzinę uruchamiania projektu lub tworzenia pliku i są również to dobry sposób na Dowiedz się więcej o różnych typach aplikacji i kodu struktury. Warto dopiero po kilku minutach można utworzyć za pomocą różnych szablonów projektów i elementów do zapoznania się z ich oferty.

**Pytanie: Czy można również używać Cookiecutter szablonów?**

**Odpowiedzi**: tak! W rzeczywistości program Visual Studio udostępnia bezpośrednia Integracja z Cookiecutter, w którym można zapoznać się za pośrednictwem [Szybki Start: Tworzenie projektu z szablonu Cookiecutter](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md).

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczek: Praca z języka Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Zobacz także

- [Ręczne identyfikowanie istniejących interpreter języka Python](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment).
- [Zainstaluj obsługę języka Python w programie Visual Studio 2015 i starszych wersji](installing-python-support-in-visual-studio.md).
- [Lokalizacje instalacji](installing-python-support-in-visual-studio.md#install-locations).
