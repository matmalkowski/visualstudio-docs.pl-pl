---
title: Wprowadzenie do funkcji platformy Azure
description: Przy użyciu funkcji platformy Azure w programie Visual Studio dla komputerów Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.openlocfilehash: 5d787efbd09ad7f2d4a1f5f72b8f1493d8c6c587
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="introduction-to-azure-functions"></a>Wprowadzenie do funkcji platformy Azure

Azure functions to sposób tworzenia i uruchamiania sterowane zdarzeniami wstawki kodu — — funkcje — — w chmurze, bez konieczności jawnego udostępniania lub zarządzanie infrastrukturą. Aby uzyskać więcej informacji na temat usługi Azure Functions, zobacz [dokumentacji usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions/).

## <a name="requirements"></a>Wymagania

Narzędzia funkcji platformy Azure znajdują się w **programu Visual Studio for Mac 7.5**.

Tworzenie i wdrażanie funkcji należy również subskrypcji platformy Azure, która jest dostępna bezpłatnie [ https://azure.com/free ](https://azure.com/free).

## <a name="creating-your-first-azure-functions-project"></a>Tworzenie pierwszego projektu usługi Azure Functions

1. W programie Visual Studio dla komputerów Mac, wybierz **Plik > Nowy rozwiązania...** 
2. W oknie dialogowym Nowy projekt, wybierz szablon usługi Azure Functions w obszarze **chmury > Ogólne** i kliknij przycisk **dalej**:

    ![Okno dialogowe nowego projektu przedstawiający opcji Azure functions](media/azure-functions-image1.png)

3. Wprowadź **Nazwa projektu** i wybierz **Utwórz**.

Visual Studio for Mac tworzy projekt .NET Standard z funkcją HttpTrigger domyślne uwzględnione. Zawiera również odwołań NuGet do szerokiej gamy **AzureWebJobs** pakietów, jak również **Newtonsoft.Json** pakietu.

![Programu Visual Studio for Mac Edytor wyświetlanie całkiem nowych funkcji platformy azure z szablonu](media/azure-functions-newproj.png)

Nowy projekt zawiera następujące pliki:

* **HttpTrigger.cs** — ta klasa zawiera schematyczny kod dla funkcji wyzwalanych przez protokół HTTP. Zawiera **FunctionName** atrybutu z nazwą funkcji i atrybutem wyzwalacza **HttpTrigger**, który określa, że funkcja jest wyzwalana przez żądanie HTTP. Więcej informacji o metodzie funkcji, można znaleźć w [dokumentacja dla deweloperów Azure funkcje C#](https://docs.microsoft.com/azure/azure-functions/functions-dotnet-class-library) artykułu.
* **Host.JSON** — ten plik zawiera opis opcji konfigurację globalną funkcji hosta. Aby uzyskać przykładowy plik i informacji na temat dostępnych ustawień dla tego pliku, zobacz [host.json odwołania do usługi Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-host-json).
* **Local.Settings.JSON** — ten plik zawiera wszystkie ustawienia dla funkcji uruchomionej na komputerze lokalnym. Te ustawienia są używane przez podstawowe narzędzia funkcji platformy Azure. Aby uzyskać więcej informacji, zobacz [pliku ustawień lokalnych](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local#local-settings-file) w artykule Azure funkcje podstawowe narzędzia.

Teraz, po utworzeniu nowego projektu usługi Azure Functions w programie Visual Studio dla komputerów Mac, należy przetestować domyślnej funkcji wyzwalanej przez HTTP z komputera lokalnego.

<!--
## Create an Azure storage account

[Describe why this step is necessary and what it does]

1. Log on to your account at [https://portal.azure.com](https://portal.azure.com).
2. Under the **Favorites** section, located on the left of the screen, select **Storage Accounts**:
    ![]()
3. Select **Add** to create a new storage account:
    ![]()
4. Enter a globally unique name for the **Name** and reuse it for the **Resource group**. You can keep all the other items as their default.
    ![]()
5. Click **Create**. It might take a few minutes to create the storage account. You'll get a notification once it has been successfully created.
6. Select the **Go to resource** button from the notification:
    ![]()
-->

## <a name="testing-the-function-locally"></a>Testowanie funkcji lokalnie

Z obsługą usługi Azure Functions w programie Visual Studio for Mac można testowanie i debugowanie funkcji na komputerze deweloperskim lokalnego.

1. Aby przetestować funkcję lokalnie, naciśnij klawisz **Uruchom** przycisku w programie Visual Studio dla komputerów Mac:

    ![Rozpocznij debugowanie przycisku w programie visual studio dla komputerów mac](media/azure-functions-run.png)

1. Uruchamianie projektu uruchamia lokalnych, debugowanie, funkcji platformy Azure i otwiera nowe okno terminalu, jak pokazano na poniższej ilustracji: 

    ![dane wyjściowe funkcji przedstawiający okno terminalu](media/azure-functions-terminal.png) 

    Skopiuj adres URL z danych wyjściowych.

3. Wklej adres URL dla żądania HTTP do paska adresu przeglądarki. Dodaj ciąg zapytania `?name=<yourname>` na końcu adresu URL i wykonać żądania. Na poniższej ilustracji przedstawiono odpowiedzi w przeglądarce, aby lokalne żądania GET zwracane przez funkcję:

    ![żądania HTTP w przeglądarce](media/azure-functions-httpreq.png)

## <a name="creating-a-new-function"></a>Tworzenie nowych funkcji

Szablony funkcji umożliwiają szybkie tworzenie nowych funkcji przy użyciu najczęściej wyzwalaczy i szablonów. Podczas tworzenia nowego projektu usługi Azure Functions automatycznie zawiera funkcję HttpTrigger. Aby utworzyć inny typ funkcji, wykonaj następujące czynności:

1. Usuń **HttpTrigger.cs** pliku, klikając go i wybierając **Usuń**. Wybierz z następującego alertu **usunąć** Aby usunąć go z projektu:

    ![okno dialogowe, aby usunąć plik z projektu](media/azure-functions-remove.png)

2. Aby dodać nową funkcję, kliknij prawym przyciskiem myszy nazwę projektu i wybierz **Dodaj > dodawania funkcji...** :

    ![kontekst akcji dla Dodawanie nowych funkcji](media/azure-functions-addnew.png)

3. Z **nową funkcję Azure** okno dialogowe, wybierz funkcję, potrzebujesz:

    ![okno dialogowe nowego funkcji platformy azure](media/azure-functions-newfunction.png)

    Lista szablonów funkcji platformy Azure znajdują się w poniższej sekcji.

## <a name="available-function-templates"></a>Szablony funkcji dostępne

- **HTTP** — wyzwalanie wykonywania kodu za pomocą żądania HTTP. Brak jawnych szablonów dla następujących wyzwalaczy HTTP:
    - HTTP GET CRUD
    - CRUD POST protokołu HTTP
    - Wyzwalacz protokołu HTTP z parametrami
    - Wyzwalacz protokołu HTTP
- **Czasomierz** — wykonywanie oczyszczania lub innych zadań wsadowych na wstępnie zdefiniowanego harmonogramu. Ten szablon ma dwa pola: nazwą i harmonogram, jest to wyrażenie CRON sześciu pola. Aby uzyskać więcej informacji, zobacz [usługę Azure functions artykułu na czas](https://docs.microsoft.com/azure/azure-functions/functions-create-scheduled-function)
- **Wyzwalacz GitHub** — odpowiadanie na zdarzenia występujące w repozytoriach usługi GitHub. Aby uzyskać więcej informacji, zobacz [usługi Azure Functions artykuł w witrynie GitHub](https://docs.microsoft.com/azure/azure-functions/functions-create-github-webhook-triggered-function)
    - GitHub osoby wystawiającej komentarz — będzie można uruchomić tej funkcji, kiedy odbierze elementu webhook GitHub dla żądania problem lub ściągania i dodaje komentarz.
    - Element WebHook GitHub — ta funkcja zostanie uruchomione po odebraniu elementu webhook GitHub
- **Wyzwalacz obiektu blob** — proces usługi Azure Storage obiektów blob, po dodaniu ich do kontenera. Oprócz nazwy funkcji ten szablon ma właściwości połączenia i ścieżkę. Właściwość path jest ścieżką w ramach konta magazynu, który będzie monitorować wyzwalacza. Konto połączenia jest nazwą ustawienia aplikacji zawierający parametry połączenia konta magazynu. Aby uzyskać więcej informacji, zobacz [artykułu magazynu obiektów Blob Azure functions](https://docs.microsoft.com/azure/azure-functions/functions-create-storage-blob-triggered-function).
- **Kolejka wyzwalacza** — jest to funkcja, która będzie odpowiadać na komunikaty pojawiających się w kolejce usługi Azure Storage. Oprócz nazwy funkcji, ten szablon ma **ścieżki** (Nazwa kolejki, z którego będą odczytywane wiadomości) i konto magazynu **połączenia** (Nazwa ustawienia aplikacji zawierające magazynu Parametry połączenia konta). Aby uzyskać więcej informacji, zobacz [usługę Azure functions artykułu na magazyn kolejek](https://docs.microsoft.com/azure/azure-functions/functions-create-storage-queue-triggered-function).
- **Ogólny element WebHook** — jest to funkcja prostego, który zostanie uruchomiony, gdy odbiera żądanie z dowolnej usługi obsługującej takie elementy. Aby uzyskać więcej informacji, zobacz [usługę Azure functions artykułu na ogólnych elementów webhook](https://docs.microsoft.com/azure/azure-functions/functions-create-generic-webhook-triggered-function)
- **Zmiany rozmiaru obrazu** — ta funkcja tworzy obrazów po zmianie rozmiaru przy każdym dodaniu obiektu blob do kontenera. Szablon ma ścieżkę i parametry połączenia dla wyzwalacza, wyjściowy mały obraz i średnia obrazu wyjściowego.
- **Token sygnatury dostępu Współdzielonego** — ta funkcja generuje token sygnatury dostępu Współdzielonego dla danej nazwy kontenera i obiektów blob magazynu Azure. Oprócz nazwy funkcji ten szablon ma właściwości połączenia i ścieżkę. Właściwość path jest ścieżką w ramach konta magazynu, który będzie monitorować wyzwalacza. Konto połączenia jest nazwą ustawienia aplikacji zawierający parametry połączenia konta magazynu. **Praw dostępu** musi być ustawiona. Poziom dostępu określa, czy funkcja wymaga klucza interfejsu API i klucz, do którego mają być używane; Funkcja korzysta z klucza funkcja; Administrator używa klucza głównego. Aby uzyskać więcej informacji, zobacz [C# funkcji platformy Azure do generowania tokenów SAS](https://azure.microsoft.com/resources/samples/functions-dotnet-sas-token/) próbki.
- **Trwałe funkcji aranżacji** — trwałe funkcje umożliwiają pisanie stanowe funkcji w środowisku bez serwera. Rozszerzenie zarządza stanu, punkty kontrolne i ponownego uruchomienia dla Ciebie. Aby uzyskać więcej informacji, zobacz przewodniki usługę Azure functions na [trwałe funkcji](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)