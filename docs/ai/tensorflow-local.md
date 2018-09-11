---
title: Uczenie modelu tensorflow lokalnie
description: Uruchamianie modelu tensorflow lokalnie w narzędzia sztucznej Inteligencji dla programu Visual Studio
keywords: Program visual studio, tensorflow, lokalny w sztucznej inteligencji
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- multiple
ms.openlocfilehash: 7f60fa346df7d2b9e89f3d6905e273d0191bdf3b
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281744"
---
# <a name="train-a-tensorflow-model-locally"></a>Uczenie modelu TensorFlow lokalnie

W tym przewodniku Szybki Start będzie uczenie modelu TensorFlow z [mnist ręcznie ZAPISANYCH](http://yann.lecun.com/exdb/mnist/) zestawu danych lokalnie w programie Visual Studio Tools for AI.
Bazy danych mnist ręcznie ZAPISANYCH ma zestaw szkolenia 60 000 przykłady i zbiór 10 000 przykłady pisma odręcznego cyfr.

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem upewnij się, że masz zainstalowane następujące oprogramowanie:

### <a name="google-tensorflow"></a>Google TensorFlow

Uruchom następujące polecenie w terminalu.
```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>NumPy i SciPy
Zainstaluj [NumPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) i [SciPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy).

### <a name="download-sample-code"></a>Pobierz przykładowy kod
Pobierz ten [repozytorium GitHub](https://github.com/Microsoft/samples-for-ai) zawierający wprowadzenie do uczenia głębokiego TensorFlow, CNTK, Theano i przykłady.

## <a name="open-solution-and-train-model"></a>Otwórz rozwiązanie i wytrenuj model

- Uruchom program Visual Studio i wybierz **Plik > Otwórz > Projekt/rozwiązanie**.

- Wybierz **przykłady Tensorflow** folderu z repozytorium przykładów pobrany i otwarty **TensorflowExamples.sln** pliku.

![Otwórz projekt](media\tensorflow-local\open-project.png)

![Otwórz rozwiązanie](media\tensorflow-local\open-solution.png)

- Znajdź projekt mnist ręcznie ZAPISANYCH w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy i wybierz **Ustaw jako projekt startowy**.

- Kliknij przycisk **Uruchom**.

- Dane wyjściowe będą drukowane w konsoli.

![Przykładowe dane wyjściowe z konsoli](media\tensorflow-local\console-output.png)

> [!div class="nextstepaction"]
> [Uczenie modelu TensorFlow w chmurze](tensorflow-vm.md)