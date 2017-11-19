---
title: Uczenie modelu tensorflow lokalnie
description: "Uruchamianie modelu tensorflow lokalnie w narzędziach AI programu Visual Studio"
keywords: AI, visual studio, tensorflow, lokalnego
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: quickstart
ms.technology: visual studio
ms.devlang: python
ms.service: multiple
ms.openlocfilehash: 2b48acc8cfea97a89c32ce7180d693246ca6ab26
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="train-a-tensorflow-model-locally"></a>Uczenie modelu TensorFlow lokalnie 

W tym Szybki Start, firma Microsoft train model TensorFlow z [MNIST](http://yann.lecun.com/exdb/mnist/) zestawu danych lokalnie w Visual Studio Tools for AI. Baza danych MNIST ma zestaw szkolenia 60 000 przykłady i zbiór 10 000 przykłady odręcznie cyfr. 

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem należy upewnić się, że zainstalowane następujące elementy:

### <a name="google-tensorflow"></a>Google TensorFlow 

Uruchom następujące polecenie w terminalu. 
```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>NumPy i SciPy 
Zainstaluj [NumPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) i [SciPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy). 

### <a name="download-sample-code"></a>Pobierz przykładowy kod
Pobierz to [repozytorium GitHub](https://github.com/Microsoft/samples-for-ai) zawierający wprowadzenie do uczenia głębokie TensorFlow, CNTK, Theano i próbek. 

## <a name="open-solution-and-train-model"></a>Otwórz rozwiązanie i uczenia modelu

- Uruchom program Visual Studio i wybierz **Plik > Otwórz > Projekt/rozwiązanie**.

- Wybierz **przykłady Tensorflow** folder z repozytorium próbki pobrane i Otwórz **TensorflowExamples.sln** pliku. 

![Otwórz projekt](media\tensorflow-local\open-project.png)

![Otwórz rozwiązanie](media\tensorflow-local\open-solution.png)

- Znajdź projekt MNIST w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy i wybierz **Ustaw jako projekt startowy**.

- Kliknij przycisk **Uruchom**. 

- Dane wyjściowe jest drukowany w konsoli.

![Przykładowe dane wyjściowe z konsoli](media\tensorflow-local\console-output.png)

> [!div class="nextstepaction"]
> [Uczenie modelu przy użyciu TensorFlow w chmurze](tensorflow-vm.md)