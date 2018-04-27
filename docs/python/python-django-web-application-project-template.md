---
title: Szablon projektu sieci web Django dla języka Python
description: Przegląd szablonów programu Visual Studio dla aplikacji sieci web napisanych w języku Python za pomocą środowiska Django.
ms.date: 04/17/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 077619b7d47441bb4a02dbe87e7cf714b634beff
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="django-web-project-template"></a>Szablon projektów internetowych Django

[Django](https://www.djangoproject.com/) to struktura Python wysokiego poziomu przeznaczone do rozwoju szybkie, bezpieczne i skalowalne sieci web. Obsługa języka Python w programie Visual Studio udostępnia kilka szablonów projektu konfigurowania struktury aplikacji sieci web na podstawie Django. Aby użyć szablonu w programie Visual Studio, wybierz **pliku** > **nowy** > **projektu**, wyszukaj "Django" i wybierz z "puste Django sieci Web "Projekt,"Projekt sieci Web Django"i"Projektu sieci Web Django sond"Szablony. Zobacz [Learning Django samouczek](learn-django-in-visual-studio-step-01-project-and-solution.md) przewodnik wszystkich szablonów.

Program Visual Studio udostępnia pełną IntelliSense dla projektów Django:

- Zmienne kontekstu przekazywany do szablonu:

    ![IntelliSense dla kontekstu zmiennych](media/template-django-intellisense.png)

- Znakowanie i filtrowania dla obu built-ins i zdefiniowanych przez użytkownika:

    ![IntelliSense dla tagów i filtry](media/template-django-intellisense-filter.png)

- Składnia kolorowaniu osadzonych CSS i JavaScript:

    ![CSS, IntelliSense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)

Visual Studio udostępnia pełnej [obsługa debugowania](debugging-python-in-visual-studio.md) dla projektów Django: 

![Punkty przerwania](media/template-django-debugging.png)

Jest typowa dla projektów Django mają być zarządzane za pośrednictwem ich `manage.py` pliku, który jest założenie, że program Visual Studio jest zgodny. Zatrzymanie przy użyciu tego pliku jako punkt wejścia, Podziel są zasadniczo pliku projektu. W takim przypadku należy [ponownie utworzyć projekt z istniejących plików](managing-python-projects-in-visual-studio.md#creating-a-project-from-existing-files) bez oznaczenie go jako projekt Django.

## <a name="django-management-console"></a>Konsoli zarządzania Django

W konsoli zarządzania Django jest dostępny za pośrednictwem różnych poleceń na **projektu** menu lub klikając prawym przyciskiem myszy projekt w Eksploratorze rozwiązań.

- **Otwórz powłokę Django...** : otwiera powłokę w kontekście użytkownika aplikacji, który umożliwia manipulowanie modeli "

    ![Konsola](media/template-django-console-shell.png)

- **Baza danych synchronizacji Django**: wykonuje `manage.py syncdb` w oknie interaktywnym:

    ![Konsola](media/template-django-console-sync-db.png)

- **Zbieraj Static**: wykonuje `manage.py collectstatic --noinput` można skopiować pliki statyczne do ścieżka określona przez `STATIC_ROOT` w Twojej `settings.py`. Gdy [publikowania w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md), pliki statyczne są zbierane automatycznie w ramach operacji publikowania.

    ![Konsola](media/template-django-console-collect-static.png)

- **Sprawdź poprawność**: wykonuje `manage.py validate`, które raporty wszelkie błędy sprawdzania poprawności zainstalowane modele określony przez `INSTALLED_APPS` w Twojej `settings.py`:

    ![Konsola](media/template-django-console-validate.png)

## <a name="see-also"></a>Zobacz także

- [Samouczek dotyczący uczenia Django](learn-django-in-visual-studio-step-01-project-and-solution.md)