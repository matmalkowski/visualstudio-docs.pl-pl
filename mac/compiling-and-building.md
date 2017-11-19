---
title: Kompilowanie i tworzenia w programie Visual Studio for Mac | Dokumentacja firmy Microsoft
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: 9005cf64f4b72f39923d6525e78de745d79c3953
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Kompilowanie i tworzenia w programie Visual Studio dla komputerów Mac

Visual Studio for Mac może służyć do tworzenia aplikacji i tworzenie zestawów podczas tworzenia projektu. Jest ważne skompilować i utworzyć kod wczesne i często, dzięki czemu można zidentyfikować niezgodności typów i inne błędy kompilacji.

## <a name="choosing-a-build-method"></a>Wybieranie metody kompilacji:

### <a name="using-the-ide"></a>Używanie IDE

Dla komputerów Mac przy użyciu programu Visual Studio umożliwia tworzenie i uruchamianie kompilacji natychmiast, podczas przekazywania nadal kontrolować funkcjonalność kompilacji. Visual Studio for Mac używa MSBuild jako źródłowy system kompilacji.

Wszystkie projekty i rozwiązania utworzone w IDE ma domyślnej konfiguracji kompilacji, która Definiowanie kontekstu dla kompilacji. Te konfiguracje można edytowane lub Utwórz swój własny. Tworzenie lub modyfikowanie tych konfiguracji zostanie automatycznie zaktualizowane do pliku projektu, który jest następnie używany przez program MSBuild do tworzenia projektu.  

Aby uzyskać więcej informacji dotyczących sposobu tworzenia projektów i rozwiązań w środowisku IDE, zobacz [kompilowanie oraz Oczyszczanie projektów i rozwiązań](~/building-and-cleaning-projects-and-solutions.md) przewodnik.

Visual Studio for Mac można również wykonać następujące czynności:

* Zmień ścieżkę wyjściową. To jest edytowany w opcje projektu:

    ![Zmienianie ścieżki danych wyjściowych](media/compiling-and-building-image4.png)

* Zmień poziom szczegółowości danych wyjściowych kompilacji:

    ![Zmień szczegółowość kompilacji](media/compiling-and-building-image5.png)

* Dodaj niestandardowe polecenia przed, w trakcie lub po kompilowania lub czyszczenia:

    ![Dodawanie poleceń niestandardowych](media/compiling-and-building-image6.png)

### <a name="building-from-command-line"></a>Tworzenie z wiersza polecenia

Aparat kompilacji MSBuild umożliwia tworzenie aplikacji za pomocą wiersza polecenia.

Zobacz [MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild) zawartości, aby uzyskać więcej informacji na temat używania programu MSBuild.

### <a name="using-visual-studio-team-services"></a>Za pomocą programu Visual Studio Team Services

* [Tworzenie aplikacji platformy Xamarin](https://www.visualstudio.com/docs/build/apps/mobile/xamarin)
* [Ciągła Integracja z platformą Xamarin](https://developer.xamarin.com/guides/cross-platform/ci/)