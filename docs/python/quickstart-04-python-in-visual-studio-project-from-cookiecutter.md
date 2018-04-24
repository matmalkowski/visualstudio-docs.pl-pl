---
title: Szybki Start — Tworzenie projektu języka Python za pomocą Cookiecutter
description: W tego przewodnika Szybki Start dla języka Python za pomocą szablonu Cookiecutter tworzenia projektu Visual Studio.
ms.date: 09/22/2017
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: c8e4ec1691dc1826fa6772d6d69723659245cece
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Szybki Start: Tworzenie projektu z szablonu Cookiecutter

Po wprowadzeniu [zainstalowane obsługę języka Python w Visual Studio 2017](installing-python-support-in-visual-studio.md), łatwo utworzyć nowy projekt z szablonu Cookiecutter, w tym wiele, które są publikowane w witrynie GitHub. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) zawiera graficzny interfejs użytkownika do odnalezienia szablony, wprowadź opcje szablonu oraz tworzenie projektów i pliki. Wchodzi w skład programu Visual Studio 2017 r, a można zainstalować oddzielnie we wcześniejszych wersjach programu Visual Studio.

1. Dla tego przewodnika Szybki Start należy najpierw zainstalować dystrybucji Anaconda3 Python, która obejmuje niezbędne pakiety języka Python dla szablonu Cookiecutter pokazane. Uruchom Instalatora programu Visual Studio, wybierz **Modyfikuj**, rozwiń opcje **programowania Python** po prawej stronie i wybierz opcję "Anaconda3" (32-bitowy lub 64-bitowe). Należy pamiętać, że instalacja może zająć pewien czas w zależności od szybkości internetowych, ale jest najprostszym sposobem zainstalowania wymaganych pakietów.

1. Uruchom program Visual Studio.

1. Wybierz **Plik > Nowy > z Cookiecutter...** . To polecenie powoduje otwarcie okna w programie Visual Studio, gdzie można przeglądać szablonów. 

    ![Nowy projekt z szablonu Cookiecutter](media/projects-from-cookiecutter1.png)

1. Wybrany szablon "Microsoft/python-sklearn klasyfikatora cookiecutter", a następnie wybierz **dalej**. (Proces może potrwać kilka minut po raz pierwszy używasz Cookiecutter).

1. W następnym kroku należy ustawić dla nowego projektu w lokalizacji **tworzenie do** pola, a następnie wybierz opcję **Utwórz**.

    ![Drugim krokiem przy użyciu Cookiecutter, ustawianie właściwości projektu](media/projects-from-cookiecutter2.png)

1. Po zakończeniu procesu zostanie wyświetlony komunikat "Pliki utworzone pomyślnie." Wybierz polecenie **Otwórz w Eksploratorze rozwiązań** otworzyć projektu.

1. Naciśnij klawisze Ctrl + F5 lub wybierz **Debuguj > Uruchom bez debugowania** do uruchomienia programu. 

    ![Dane wyjściowe projektu szablonu python-sklearn klasyfikatora cookiecutter](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Samouczek: Praca z języka Python w programie Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Zobacz także

- [Użycie rozszerzenia Cookiecutter](using-python-cookiecutter-templates.md)
- [Ręczne identyfikowanie istniejących interpreter języka Python](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment).
- [Zainstaluj obsługę języka Python w programie Visual Studio 2015 i starszych wersji](installing-python-support-in-visual-studio.md).
- [Lokalizacje instalacji](installing-python-support-in-visual-studio.md#install-locations).
