---
title: "Tworzenie projektu na AI narzędzi dla programu Visual studio"
description: "Tworzenie projektu z usługi azure machine learning galerii przy użyciu — przykład"
keywords: AI, visual studio uczenia maszynowego azure
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: how to article
ms.technology: visual studio
ms.devlang: multiple
ms.service: multiple
ms.openlocfilehash: 2d8b5f1d06d31eaba9c75e0f0515b2526fc7efdf
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
## <a name="create-an-ai-project-from-the-azure-machine-learning-gallery-in-visual-studio"></a>Utwórz projekt AI z galerii Azure Machine Learning w programie Visual Studio

Usługa Azure Machine Learning jest zintegrowany z programu Visual Studio Tools dla AI. Służy on do przesyłania zadań learning maszyny do zdalnego obliczeń obiektów docelowych jak maszyn wirtualnych platformy Azure, klastry Spark i inne. Dowiedz się więcej o [Azure Machine Learning eksperymenty](https://docs.microsoft.com/azure/machine-learning/preview/experimentation-service-configuration) 

Po wprowadzeniu [zainstalowany program Visual Studio Tools dla AI](installation.md), ułatwia tworzenie nowego projektu języka Python za pomocą wstępnie przygotowanych przepisami w galerii Azure Machine Learning próbki.

> ! Azure Machine Learning Workbench musi być zainstalowany. Aby go zainstalować można znaleźć [szybkiego startu instalacji usługi Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/preview/quickstart-installation) 

1. Uruchom program Visual Studio. Otwórz **Eksploratora serwera** otwierając **narzędzia AI** menu i wybierając polecenie **wybierz klastra**  

    ![Wybór klastra](media\create-project\select-cluster.png)

1. Zaloguj się do subskrypcji usługi Azure Machine Learning, klikając prawym przyciskiem myszy **usługi Azure Machine Learning** następnie wybierz węzeł w Eksploratorze serwera **logowania** i postępuj zgodnie z instrukcjami.

    ![Logowanie](media\create-project\azureml-login.png)
 
2. Wybierz **narzędzia AI > Azure Machine Learning próbki galerii**. 
    
    ![Przykładowe galerii](media\create-project\gallery.png)

1. Dla tego przewodnika Szybki Start, wybierz "**MNIST przy użyciu TensorFlow**" sample i kliknij przycisk **zainstalować**. Podaj 
2.
 - **Grupa zasobów**: grupy zasobów platformy Azure, w którym będą przechowywane metadane
 - **Konto**: usługi Azure Machine Learning eksperymenty konta
 - **Obszar roboczy**: obszaru roboczego uczenia maszynowego Azure
 - **Typ projektu**: framework learning maszyny. W takim przypadku wybierz **TensorFlow**
 - **Dodaj do rozwiązania**: Określa, czy do dodania do bieżącego rozwiązania Visual Studio lub Utwórz i Otwórz nowe rozwiązanie
 - **Ścieżka projektu**: lokalizację, aby zapisać kod
 - **Nazwa projektu**: typ **TensorFlowMNIST**
   

    ![Projekt wynikowy przy użyciu szablonu aplikacji Python](media\create-project\new-AzureSampleProject.png)

1. Program Visual Studio tworzy plik projektu ( `.pyproj` pliku na dysku) oraz inne pliki zdefiniowane w próbce. Przy użyciu szablonu "MNIST" Projekt zawiera kilka plików.

    ![mnist](media\create-project\azml-mnist.png)

1. Przesłać zadania usługi Azure Machine Learning. 

    ![mnist](media\create-project\submit-azml.png)

1. Uruchomione w kontenerze Docker lub na komputerze lokalnym

    ![mnist](media\create-project\azml-local.png)