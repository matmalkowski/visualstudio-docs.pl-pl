---
title: Używanie narzędzia PyLint do przeanalizowania linterem kodu w języku Python
description: Jak używać PyLint w programie Visual Studio, aby sprawdzić problemy w kodzie języka Python.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 7cf3e17ac70816afbd8ab67db8f407a2a982b279
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174704"
---
# <a name="using-pylint-to-check-python-code"></a>Sprawdzanie kodu w języku Python przy użyciu PyLint

[PyLint](https://www.pylint.org/), powszechnie używane narzędzie, które sprawdza występowanie błędów w kodzie języka Python i zachęca dobre języka Python, wzorców i jest zintegrowana w programie Visual Studio dla projektów języka Python.

Po prostu kliknij prawym przyciskiem myszy projekt języka Python, w Eksploratorze rozwiązań i wybierz **Python > Uruchom PyLint...** :

![Polecenie PyLint w menu kontekstowym dla projektów języka Python](media/code-pylint-command.png)

Za pomocą tego polecenia monit o zainstalowanie PyLint w środowisku active, jeśli nie jest już obecny.

PyLint ostrzeżenia i błędy są wyświetlane w oknie Lista błędów:

![Lista błędów PyLint](media/code-pylint-error-list.png)

Dwukrotne kliknięcie błąd przejście bezpośrednio do kodu źródłowego, która wygenerowała ten problem.

> [!Tip]
> Zobacz [PyLint funkcji odwołanie](https://pylint.readthedocs.io/en/latest/technical_reference/features.html) szczegółową listę wszystkich PyLint Wyprowadź komunikaty.

## <a name="setting-pylint-command-line-options"></a>Ustawianie opcji wiersza polecenia PyLint

[Opcje wiersza polecenia](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) sekcji dokumentacji PyLint zawiera opis sposobu kontrolowania zachowania PyLint firmy za pośrednictwem `.pylintrc` pliku konfiguracji. Takiego pliku można umieścić w folderze głównym projektu języka Python w programie Visual Studio lub w innym miejscu w zależności od tego, jak często chcesz, aby te ustawienia stosowane (zobacz [opcje wiersza polecenia](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) Aby uzyskać szczegółowe informacje).

Na przykład, aby pominąć ostrzeżenia "Brak docstring" pokazano na poprzedniej ilustracji, za pomocą `.pylintrc` pliku w projekcie, wykonaj czynności:

1. W wierszu polecenia przejdź do katalogu głównego projektu (który zawiera Twoje `.pyproj` pliku) i uruchom następujące polecenie, aby wygenerować plik konfiguracji skomentowanej:

   ```command
   pylint --generate-rcfile > .pylintrc
   ```

1. W Eksploratorze rozwiązań w usłudze Visual Studio, kliknij prawym przyciskiem myszy projekt, wybierz **Add > elementu zamykanie...** , przejdź do i wybierz nowy `.pylintrc` pliku, a następnie wybierz **Dodaj**.

1. Otwórz plik do edycji, który zawiera różne ustawienia, które można pracować. Aby wyłączyć ostrzeżenia, zlokalizuj `[MESSAGES CONTROL]` sekcji, a następnie zlokalizuj `disable` ustawienie w tej sekcji. Jest to długi ciąg określonych wiadomości, do których można dołączyć niezależnie od tego ostrzeżenia, które chcesz. W tym przykładzie w tym miejscu należy dołączyć `,missing-docstring` (w tym oddzielania przecinkami).

1. Zapisz `.pylintrc` pliku i spustit PyLint ponownie, aby zobaczyć, że ostrzeżenia teraz są pomijane.

> [!Tip]
> Aby użyć `.pylintrc` pliku z udziału sieciowego, Utwórz zmienną środowiskową o nazwie `PYLINTRC` z wartością nazwy pliku w sieci udostępnianie przy użyciu ścieżki UNC lub litera dysku zmapowanego. Na przykład `PYLINTRC=\\myshare\python\.pylintrc`.
