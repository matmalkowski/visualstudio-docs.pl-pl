---
title: "Sumbit zadania do uczenia modelu w AI usługi partia zadań Azure"
description: uczenie modelu chmury
keywords: AI, visual studio, train model, chmury
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: how-to article
ms.devlang: multiple
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- azure
ms.openlocfilehash: 90d0e7db36b91c2add1bcfe80fb3325bd1ddf126
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="train-ai-models-in-azure-batch-ai"></a>Modele Train AI w AI usługi partia zadań Azure

Partia AI jest zarządzana usługa, która umożliwia AI pracowników naukowo-badawczych i analityków danych w celu przeszkolenia AI i innych modeli w klastrach maszyn wirtualnych platformy Azure, w tym o maszynach wirtualnych z obsługą procesora GPU uczenia maszynowego. Opisano wymagania dotyczące zadania, aby znaleźć dane wejściowe i przechowywania danych wyjściowych i AI partii obsługuje pozostałe. [Dowiedz się więcej o AI usługi partia zadań Azure](https://docs.microsoft.com/azure/batch-ai/overview)

Jest zintegrowany z programu Visual Studio Tools dla AI tak dynamicznie można skalować w poziomie modeli szkolenia na platformie Azure.  Po wprowadzeniu [zainstalowany program Visual Studio Tools dla AI](installation.md), ułatwia tworzenie nowego projektu języka Python za pomocą wstępnie przygotowanych przepisami w galerii Azure Machine Learning próbki.

1. Uruchom program Visual Studio. Otwórz **Eksploratora serwera** otwierając **narzędzia AI** menu i wybierając polecenie **wybierz klastra**

    ![Wybór klastra](media\train-model\select-cluster.png)


2. Rozwiń węzeł **narzędzia AI**. Wszystkie zasoby AI partii, których masz będzie być wykrywane automatycznie i są wyświetlane w Eksploratorze serwera.

    ![Przykładowe galerii](media\train-model\batchai.png)

3. Wybierz **Widok > Team Explorer...**  otworzyć **Team Explorer** okna, w którym można nawiązać połączenia z usługi GitHub lub Visual Studio Team Services lub sklonować repozytorium.

    ![Zespół przedstawiający okno Eksploratora Visual Studio Team Services, GitHub i klonowanie repozytorium](media\train-model\team-explorer.png)

4. W polu adresu URL **lokalnego repozytoria Git**, wprowadź `https://github.com/Microsoft/samples-for-ai`, wprowadź folder plików sklonowany i wybierz **klonowania**.

    > [!Tip]
    > Folder, który określisz w programie Team Explorer jest konkretnego folderu do odbierania sklonowany plików. W przeciwieństwie do `git clone` poleceń, utworzenie klona w programie Team Explorer nie tworzy automatycznie podfolder o nazwie repozytorium.

5. Po ukończeniu klonowania kliknij **Plik > Otwórz rozwiązanie > Projekt / rozwiązanie**

    ![Przykładowe galerii](media\train-model\open-solution.png)

5. Otwórz **samples-for-ai\TensorFlowExamples\TensorFlowExamples.sln** w katalogu sklonować repozytorium

    ![Przykładowe galerii](media\train-model\tensorflowexamples.png)

5. Ustaw projekt MNIST jako ** projekt startowy **

    ![Przykładowe galerii](media\train-model\mnist-startup.png)

1. ** Kliknij prawym przyciskiem myszy ** projektu MNIST **przesłać zadanie**

    ![Przykładowe galerii](media\train-model\submit-job.png)

1. Wybierz użytkownika **AI usługi partia zadań Azure** klastra, a następnie kliknij przycisk **importu**. Wybierz `AzureBatchAI_TF_MNIST.json` plik, aby szybko wypełnić niektóre wartości domyślnych, takich jak obraz Docker do użycia. Następnie kliknij przycisk **przesyłania**

    ![Przykładowe galerii](media\train-model\submit-batch.png)