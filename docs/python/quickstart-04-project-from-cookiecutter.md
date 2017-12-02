---
title: "Szybki Start: Tworzenie projektów języka Python z szablonu Cookiecutter w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 876fdbd4507fd7ed55e7b29834d4a3bc5e68dfad
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Szybki Start: Tworzenie projektu z szablonu Cookiecutter

Po wprowadzeniu [zainstalowane obsługę języka Python w Visual Studio 2017](installation.md), łatwo utworzyć nowy projekt z szablonu Cookiecutter, w tym wiele, które są publikowane w witrynie GitHub. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) zawiera graficzny interfejs użytkownika do odnalezienia szablony, wprowadź opcje szablonu oraz tworzenie projektów i pliki. Wchodzi w skład programu Visual Studio 2017 r, a można zainstalować oddzielnie we wcześniejszych wersjach programu Visual Studio.

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
> [Samouczek: Praca z języka Python w programie Visual Studio](vs-tutorial-01-01.md)

## <a name="see-also"></a>Zobacz też

- [Użycie rozszerzenia Cookiecutter](cookiecutter.md)
- [Tworzenie środowiska dla istniejących interpreter języka Python](python-environments.md#creating-an-environment-for-an-existing-interpreter).
- [Zainstaluj obsługę języka Python w programie Visual Studio 2015 i starszych wersji](installation.md).
- [Lokalizacje instalacji](installation.md#install-locations).
