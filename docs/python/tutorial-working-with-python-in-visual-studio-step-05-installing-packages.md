---
title: Praca z języka Python, krok 5, instalowanie pakietów
description: Krok 5 podstawowy samouczek do pracy z języka Python w programie Visual Studio, prezentacja programu Visual Studio funkcje zarządzania pakietami w środowisku Python.
ms.date: 03/05/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 73de2a4c58a24a603f1d5d54138d5762e3ae9971
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="step-5-installing-packages-in-your-python-environment"></a>Krok 5: Instalowanie pakietów w środowisku Python

**Poprzedni krok: [uruchamianie kodu w debugerze](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Społeczność deweloperów języka Python ma wyprodukowanych tysiące przydatne pakiety, które można zastosować do własnych projektów. Program Visual Studio udostępnia interfejs użytkownika w zakresie zarządzania pakietami w Twoim środowisku Python.

1. Wybierz **Widok > inne okna > środowiska Python** polecenia menu. **Środowiska Python** okno otwiera jako element równorzędny do Eksploratora rozwiązań i przedstawia różnych środowiskach dostępne dla Ciebie. Lista zawiera obu środowiskach, które zostały zainstalowane za pomocą Instalatora programu Visual Studio i tych, które należy zainstalować osobno. Środowisko pogrubione to domyślnego środowiska, który jest używany dla nowych projektów.

  ![Okno środowiska Python](media/environments-default-view-blue.png)

1. W środowisku **omówienie** kartę zapewnia szybki dostęp do interaktywnego okna dla tego środowiska wraz z folderu instalacji i tłumaczy w środowisku. Na przykład wybierz **Otwórz okno interaktywne** i interaktywnego okna dla tego w danym środowisku jest wyświetlana w programie Visual Studio.

1. Wybierz **pakiety** kartę i można wyświetlić listę pakietów, które są aktualnie zainstalowane w środowisku.

  ![Pakiety zainstalowane w środowisku](media/environments-installed-packages-blue.png)

1. Zainstaluj `matplotlib` wprowadzając jej nazwę w polu wyszukiwania, następnie wybierz pozycję `pip install`

  ![Instalowanie matplotlib w środowisku](media/environments-add-matplotlib1.png)

1. Jeśli zostanie wyświetlony monit, w tym celu należy wyrazić zgodę na podniesienia uprawnień.

1. Po zainstalowaniu pakietu zostanie wyświetlony w oknie środowiska Python. **X** z prawej strony pakietu odinstalowuje go.

  ![Ukończenie instalacji matplotlib w środowisku](media/environments-add-matplotlib2.png)

  Pasek postępu małych poniżej środowiska wskazuje, że program Visual Studio tworzy bazę danych IntelliSense dla nowo zainstalowany pakiet. **IntelliSense** karta zawiera także szczegółowe informacje. Należy pamiętać, że przed zakończeniem tej bazy danych, funkcje IntelliSense, takie jak automatyczne uzupełnianie i sprawdzanie składni nie będzie aktywny w edytor dla tego pakietu.

  Należy pamiętać, że **programu Visual Studio 2017 wersji 15,6** i później używa metody różnych i szybsze do pracy z IntelliSense i wyświetli komunikat w tym celu **IntelliSense** kartę.

1. Utwórz nowy projekt z **Plik > Nowy > Projekt**, wybierając szablon "Python aplikacji". W pliku kodu, który pojawia się Wklej następujący kod, który tworzy wave cosinus, takich jak poprzednich kroków samouczka tylko tym kreślone graficznie:

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

1. Uruchom program z (F5) lub bez debugera (Ctrl + F5), aby wyświetlić dane wyjściowe:

  ![Dane wyjściowe przykład matplotlib](media/environments-add-matplotlib3.png)

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Praca z usługą Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

### <a name="going-deeper"></a>Przechodząc głębiej

- [Środowiska Python](managing-python-environments-in-visual-studio.md)
