---
title: "W programie Visual Studio przy użyciu PyLint | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 07/12/2017
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
ms.workload: python
ms.openlocfilehash: cf97be0c7a7b5bb9d6a9d43ceeb5cd9e9334025d
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="using-pylint-to-check-python-code"></a>Przy użyciu PyLint w celu sprawdzenia kodu języka Python

[PyLint](https://www.pylint.org/), powszechnie używane narzędzie, które sprawdza błędów w kodzie języka Python i zachęca dobrej Python kodowania wzorców, jest zintegrowany z programu Visual Studio dla projektów języka Python.

Po prostu kliknij prawym przyciskiem myszy projekt języka Python w Eksploratorze rozwiązań i wybierz **Python > Uruchom PyLint...** :

![Polecenie PyLint w menu kontekstowym dla projektów języka Python](media/code-pylint-command.png)

Za pomocą tego polecenia monit o zainstalowanie PyLint do środowiska active, jeśli nie jest już istnieje.

PyLint ostrzeżenia i błędy są wyświetlane w oknie Lista błędów:

![Lista błędów PyLint](media/code-pylint-error-list.png)

Dwukrotne kliknięcie błąd przejście bezpośrednio do kodu źródłowego, który wygenerował problem.

> [!Tip]
> Zobacz [PyLint funkcji odwołanie](https://pylint.readthedocs.io/en/latest/technical_reference/features.html) szczegółową listę wszystkich PyLint komunikaty wyjściowe.

## <a name="setting-pylint-command-line-options"></a>Ustawianie opcji wiersza polecenia PyLint

[Opcje wiersza polecenia](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) części dokumentacji PyLint zawiera opis sposobu kontrolowania zachowania PyLint firmy za pośrednictwem `.pylintrc` pliku konfiguracji. Tego pliku można umieścić w folderze głównym projektu języka Python w programie Visual Studio lub w innym miejscu w zależności od tego, jak bardzo ma tych ustawień (zobacz [opcje wiersza polecenia](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) szczegółowe informacje).

Na przykład w celu pominięcia ostrzeżenia "Brak docstring" pokazano na poprzedniej ilustracji z `.pylintrc` pliku w projekcie, wykonaj kroki:

1. W wierszu polecenia przejdź do katalogu głównym projektu (która zawiera Twoje `.pyproj` plików) i uruchom następujące polecenie, aby wygenerować plik konfiguracji komentarze:

   ```command
   pylint --generate-rcfile > .pylintrc
   ```

1. W Eksploratorze rozwiązań programu Visual Studio, kliknij prawym przyciskiem myszy projekt, wybierz **Dodaj > Kończenie elementu...** , przejdź do i wybierz nową `.pylintrc` pliku, a następnie wybierz **Dodaj**.

1. Otwórz plik do edycji, który zawiera różne ustawienia, którymi można pracować z. Aby wyłączyć ostrzeżenia, zlokalizuj `[MESSAGES CONTROL]` sekcji, a następnie zlokalizuj `disable` ustawienie w tej sekcji. Brak ciąg z określonymi komunikatami, do których można dołączyć niezależnie od tego ostrzeżenia, które chcesz. W tym przykładzie należy dołączyć `,missing-docstring` (w tym oddzielania przecinkami).

1. Zapisz `.pylintrc` pliku i uruchom PyLint ponownie, aby zobaczyć, że ostrzeżenia teraz są pomijane.

> [!Tip]
> Aby użyć `.pylintrc` pliku z udziału sieciowego, Utwórz zmienną środowiskową o nazwie `PYLINTRC` wartość nazwy pliku w sieci udostępnianie przy użyciu ścieżki UNC ani litery dysku zmapowanego. Na przykład `PYLINTRC=\\myshare\python\.pylintrc`.
