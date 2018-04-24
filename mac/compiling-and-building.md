---
title: Kompilowanie i tworzenia w programie Visual Studio dla komputerów Mac
description: ''
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: 7a7dfaeca45ae157dc9e82b9f8eff54244cbd7ca
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Kompilowanie i tworzenia w programie Visual Studio dla komputerów Mac

Visual Studio for Mac może służyć do tworzenia aplikacji i tworzenie zestawów podczas tworzenia projektu. Jest ważne skompilować i utworzyć kod wczesne i często, dzięki czemu można zidentyfikować niezgodności typów i inne błędy kompilacji.

## <a name="building-from-the-ide"></a>Kompilacja z IDE

Za pomocą programu Visual Studio dla komputerów Mac umożliwia tworzenie i uruchamianie natychmiast, tworzy podczas przekazywania nadal kontrolować funkcjonalność kompilacji. Visual Studio for Mac używa MSBuild jako źródłowy system kompilacji.

Wszystkie projekty i rozwiązania utworzone w IDE ma domyślnej konfiguracji kompilacji, która Definiowanie kontekstu dla kompilacji. Te konfiguracje można edytowane lub Utwórz swój własny. Tworzenie lub modyfikowanie tych konfiguracji zostanie automatycznie zaktualizowane do pliku projektu, który jest następnie używany przez program MSBuild do tworzenia projektu.  

Aby uzyskać więcej informacji dotyczących sposobu tworzenia projektów i rozwiązań w środowisku IDE, zobacz [kompilowanie oraz Oczyszczanie projektów i rozwiązań](~/building-and-cleaning-projects-and-solutions.md) przewodnik.

Visual Studio for Mac można również wykonać następujące czynności:

* Zmień ścieżkę wyjściową. To jest edytowany w opcje projektu:

    ![Zmienianie ścieżki danych wyjściowych](media/compiling-and-building-image4.png)

* Zmień poziom szczegółowości danych wyjściowych kompilacji:

    ![Zmień szczegółowość kompilacji](media/compiling-and-building-image5.png)

* Dodaj niestandardowe polecenia przed, w trakcie lub po kompilowania lub czyszczenia:

    ![Dodawanie poleceń niestandardowych](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>Tworzenie z wiersza polecenia

Aparat kompilacji MSBuild umożliwia tworzenie aplikacji za pomocą wiersza polecenia.

Zobacz [MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild) zawartości, aby uzyskać więcej informacji na temat używania programu MSBuild.

## <a name="building-from-visual-studio-team-services"></a>Kompilowanie z programu Visual Studio Team Services

* [Tworzenie aplikacji platformy Xamarin](https://www.visualstudio.com/docs/build/apps/mobile/xamarin)
* [Ciągła Integracja z platformą Xamarin](https://developer.xamarin.com/guides/cross-platform/ci/)