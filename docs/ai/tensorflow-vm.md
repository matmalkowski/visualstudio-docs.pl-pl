---
title: Uruchom modelu TensorFlow w chmurze
description: "Uruchom modelu tensorflow na platformie azure głębokie uczenia maszyny wirtualnej"
keywords: "AI, programu visual studio, głębokie uczenia maszyny wirtualnej"
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: tutorial
ms.technology: visual studio
ms.devlang: python
ms.service: multiple
ms.workload: multiple
ms.openlocfilehash: 39cffe5aa2c24c04a6543bbf0851e0e147c5ba6c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="train-a-tensorflow-model-in-the-cloud"></a>Uczenie modelu przy użyciu TensorFlow w chmurze

W tym samouczku, firma Microsoft będzie uczenia, model TensorFlow przy użyciu [MNIST dataset](http://yann.lecun.com/exdb/mnist/) na platformie Azure [głębokie Learning](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview) maszyny wirtualnej. 

Baza danych MNIST ma zestaw szkolenia 60 000 przykłady i zbiór 10 000 przykłady odręcznie cyfr.

## <a name="prerequisites"></a>Wymagania wstępne
Przed rozpoczęciem upewnij się, że masz następujące zainstalowane i skonfigurowane:

### <a name="setup-azure-deep-learning-virtual-machine"></a>Konfiguracja Azure bezpośrednich uczenia maszyny wirtualnej

> [!NOTE] 
> Ustaw **typ systemu operacyjnego** do systemu Linux.

Można znaleźć informacje o sposobie zapasowej głębokie maszyny wirtualnej Learning [tutaj](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/provision-deep-learning-dsvm). 

### <a name="remove-comment-in-parens"></a>Usuń komentarz w parens

```bash
echo -e ". /etc/profile\n$(cat ~/.bashrc)" > ~/.bashrc
```

### <a name="download-sample-code"></a>Pobierz przykładowy kod

Pobierz to [repozytorium GitHub](https://github.com/Microsoft/samples-for-ai) zawierający wprowadzenie do uczenia głębokie TensorFlow, CNTK, Theano i próbek. 

## <a name="open-project"></a>Otwórz projekt

- Uruchom program Visual Studio i wybierz **Plik > Otwórz > Projekt/rozwiązanie**.

- Wybierz **przykłady Tensorflow** folder z repozytorium próbki pobrane i Otwórz **TensorflowExamples.sln** pliku. 

![Otwórz projekt](media\tensorflow-local\open-project.png)

![Otwórz rozwiązanie](media\tensorflow-local\open-solution.png)

## <a name="add-azure-remote-vm"></a>Dodaj zdalnego maszyna wirtualna platformy Azure

W Eksploratorze serwera, kliknij prawym przyciskiem myszy **maszyny zdalnej** węzeł w obszarze narzędzia AI węzeł i wybierz opcję "Dodaj...". Wprowadź nazwę wyświetlaną komputer zdalny, IP hosta SSH portu, nazwę użytkownika i plik hasła/klucza. 

![Dodaj nowy komputer zdalny](media\tensorflow-vm\add-remote-vm.png)

## <a name="submit-job-to-azure-vm"></a>Przesyłanie zadań do maszyny Wirtualnej Azure
Kliknij prawym przyciskiem myszy na projekt MNIST w **Eksploratora rozwiązań** i wybierz **Prześlij zadanie**.

![Przesyłanie zadań do komputera zdalnego](media\tensorflow-vm\job-submission.png)

W oknie przesyłania:

- Na liście **klastrze**, wybierz komputer zdalny (z "rm:" prefiks) można przesłać zadania.

- Wprowadź **Nazwa zadania**. 

- Kliknij przycisk **przesłać**. 

## <a name="check-status-of-job"></a>Sprawdź stan zadania 
Aby wyświetlić stan i szczegóły zadania: rozszerzenia maszyn wirtualnych można przesłać zadania w **Eksploratora serwera**. Kliknij dwukrotnie **zadania**.

![Zadanie przeglądarki](media\tensorflow-vm\job-browser.png)

## <a name="clean-up-resources"></a>Oczyszczanie zasobów

Zatrzymaj maszynę Wirtualną, jeśli planujesz korzystanie z niej w najbliższej przyszłości. Po zakończeniu tego samouczka, uruchom następujące polecenie, aby wyczyścić zasoby:

```azurecli-interactive
az group delete --name myResourceGroup
```