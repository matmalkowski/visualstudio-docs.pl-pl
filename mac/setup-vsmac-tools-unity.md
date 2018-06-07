---
title: Instalator programu Visual Studio for Mac Tools for Unity
description: Konfigurowanie i instalowanie narzędzi Unity do użycia w programie Visual Studio dla komputerów Mac
author: dantogno
ms.author: v-davian
ms.date: 05/25/2018
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: 18839ce37feb4f2a113c4a8875ce1c25ddba31e1
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34573274"
---
# <a name="setup-visual-studio-for-mac-tools-for-unity"></a>Instalator programu Visual Studio for Mac Tools for Unity

W tej sekcji wyjaśniono, jak rozpocząć korzystanie z programu Visual Studio dla komputerów Mac Tools for Unity.

## <a name="install-visual-studio-for-mac"></a>Zainstaluj program Visual Studio dla komputerów Mac

### <a name="unity-bundled-installation"></a>Instalacja pakietu Unity

Począwszy od platformy Unity 2018.1 programu Visual Studio for Mac jest domyślną IDE języka C# dla Unity i znajduje się w Unity Pobierz Asystenta pakietu, a także narzędzie instalacji platformy Unity koncentratora. Pobierz Unity z [store.unity.com](https://store.unity.com/).

Podczas instalacji upewnij się, że na liście Składniki do zainstalowania z Unity zaznaczono Visual Studio dla komputerów Mac:

#### <a name="unity-hub"></a>Koncentrator Unity

![Instalacja Centrum Unity](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Asystent pobierania Unity

![Instalacja Asystenta pobierania Unity](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Wyszukiwanie aktualizacji dla programu Visual Studio dla komputerów Mac

Wersja programu Visual Studio for Mac dołączone do instalacji Unity nie może być r. Zalecane jest, aby wyszukać aktualizacje upewnić się, że masz dostęp do najnowszych funkcji i narzędzi.

* [Aktualizacja programu Visual Studio dla komputerów Mac](update.md)

### <a name="manual-installation"></a>Instalacja ręczna

Jeśli masz już Unity 5.6.1 lub powyżej, ale nie ma programu Visual Studio dla komputerów Mac, należy ręcznie zainstalować program Visual Studio dla komputerów Mac. Wszystkie wersje programu Visual Studio for Mac są powiązane z programem Visual Studio dla komputerów Mac Tools for Unity, w tym bezpłatna wersja Community:

* Pobierz program Visual Studio for Mac z [visualstudio.com](https://www.visualstudio.com/).
* Programu Visual Studio for Mac Tools for Unity są instalowane automatycznie podczas procesu instalacji.
* Postępuj zgodnie z instrukcjami [Przewodnik instalacji](installation.md) instalacji dodatkowego pomocy.

> [!NOTE]
> Unity wersji 5.6.1 wymaga programu Visual Studio for Mac Tools for Unity lub nowszej. Aby sprawdzić, czy Visual Studio Tools for Unity są włączone w wersji jedności, wybierz **o Unity** z Unity menu i wyszukaj tekst "Microsoft Visual Studio Tools for Unity włączone" w lewym dolnym rogu okna dialogowego.
>
> ![O Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Potwierdź, że jest włączona programu Visual Studio for Mac Tools for Unity rozszerzenia

Podczas programu Visual Studio for Mac Tools for Unity rozszerzenie powinno być włączone domyślnie, można to potwierdzić i sprawdź numer zainstalowana wersja:

1. Wybierz z menu programu Visual Studio **rozszerzeń...** .

  ![Wybierz rozszerzenia](media/setup-vsmac-tools-unity-image1.png)

1. Rozwiń sekcję programowanie gry i Potwierdź programu Visual Studio dla komputerów Mac narzędzi dla platformy Unity wpisu.

  ![Wpis Unity widoku](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Konfigurowanie środowiska Unity do użycia z programem Visual Studio dla komputerów Mac

Począwszy od platformy Unity 2018.1, Visual Studio powinien być domyślny edytor skryptu zewnętrznego w Unity. Można to potwierdzić, lub zmienić edytor skryptu zewnętrznego do programu Visual Studio:

1. Wybierz **Preferencje...**  z Unity menu.

  ![Wybierz preferencje](media/setup-vsmac-tools-unity-image4.png)

1. W oknie dialogowym Preferencje wybierz **zewnętrznych narzędzi** kartę.

1. Z listy rozwijanej zewnętrznego edytora skryptów, wybierz **programu Visual Studio** Jeśli ta opcja jest wyświetlana, w przeciwnym razie wybierz **Przeglądaj...** .

  ![Wybierz program Visual Studio](media/setup-vsmac-tools-unity-image5.png)

1. Jeśli **Przeglądaj...**  została wybrana, przejdź do katalogu aplikacji i wybierz program Visual Studio, a następnie kliknij przycisk **Otwórz**.

  ![Wybierz opcję Otwórz](media/setup-vsmac-tools-unity-image6.png)

1. Po wybraniu programu Visual Studio w **Edytor skryptów zewnętrzne** listy, zamknij okno dialogowe Preferencje, aby ukończyć proces konfiguracji.
