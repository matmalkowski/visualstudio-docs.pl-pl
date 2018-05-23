---
title: Instalator programu Visual Studio for Mac Tools for Unity
description: Konfigurowanie i instalowanie narzędzi Unity do użycia w programie Visual Studio dla komputerów Mac
author: dantogno
ms.author: v-davian
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: f9a6da6c30132d6303705019919dfcad9f8cd484
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="setup-visual-studio-for-mac-tools-for-unity"></a>Instalator programu Visual Studio for Mac Tools for Unity

W tej sekcji wyjaśniono, jak rozpocząć korzystanie z programu Visual Studio dla komputerów Mac Tools for Unity.

## <a name="install-visual-studio-for-mac"></a>Zainstaluj program Visual Studio dla komputerów Mac

Pobierz i zainstaluj program Visual Studio dla komputerów Mac. Wszystkie wersje programu Visual Studio for Mac obsługę Mac Tools for Unity, w tym bezpłatna wersja Community Visual Studio:

* Pobierz program Visual Studio for Mac z [visualstudio.com](https://www.visualstudio.com/).
* Programu Visual Studio for Mac Tools for Unity są instalowane automatycznie podczas procesu instalacji.
* Postępuj zgodnie z instrukcjami [Przewodnik instalacji](installation.md) instalacji dodatkowego pomocy.

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Potwierdź, że jest włączona programu Visual Studio for Mac Tools for Unity rozszerzenia

Podczas programu Visual Studio for Mac Tools for Unity rozszerzenie powinno być włączone domyślnie, można to potwierdzić i sprawdź numer zainstalowana wersja:

1.  Wybierz z menu programu Visual Studio **rozszerzeń...** .

  ![Wybierz rozszerzenia](media/setup-vsmac-tools-unity-image1.png)

2.  Rozwiń sekcję programowanie gry i Potwierdź programu Visual Studio dla komputerów Mac narzędzi dla platformy Unity wpisu.

  ![Wpis Unity widoku](media/setup-vsmac-tools-unity-image2.png)

## <a name="install-unity"></a>Zainstaluj Unity

Unity wersji 5.6.1 wymaga programu Visual Studio for Mac Tools for Unity lub nowszej. Wszystkie plany Unity współpracować z Visual Studio Tools for Unity, łącznie z planu free osobistych. Pobierz Unity z [store.unity.com](https://store.unity.com/).

> [!NOTE]
> Aby sprawdzić, czy Visual Studio Tools for Unity są włączone w wersji jedności, wybierz **o Unity** z Unity menu i wyszukaj tekst "Microsoft Visual Studio Tools for Unity włączone" w lewym dolnym rogu okna dialogowego.
>
>   ![O Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Konfigurowanie środowiska Unity do użycia z programem Visual Studio dla komputerów Mac

Visual Studio musi być ustawiona jako edytor skryptu zewnętrznego w Unity:

1.  Wybierz **Preferencje...**  z Unity menu.

  ![Wybierz preferencje](media/setup-vsmac-tools-unity-image4.png)

2.  W oknie dialogowym Preferencje wybierz **zewnętrznych narzędzi** kartę.

3.  Z listy rozwijanej zewnętrznego edytora skryptów, wybierz **programu Visual Studio** Jeśli ta opcja jest wyświetlana, w przeciwnym razie wybierz **Przeglądaj...** .

  ![Wybierz program Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4.  Jeśli **Przeglądaj...**  została wybrana, przejdź do katalogu aplikacji i wybierz program Visual Studio, a następnie kliknij przycisk **Otwórz**.

  ![Wybierz opcję Otwórz](media/setup-vsmac-tools-unity-image6.png)

5.  Po wybraniu programu Visual Studio w **Edytor skryptów zewnętrzne** listy, zamknij okno dialogowe Preferencje, aby ukończyć proces konfiguracji.
