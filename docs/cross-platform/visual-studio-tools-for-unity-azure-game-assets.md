---
title: "Visual Studio Tools for Unity Azure gry wskazówki zasoby | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: C06FAB2E-F592-4EFF-B96A-58858C92DCEB
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 19b98dc472b9e01529725b95133d289edff6334d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="import-sample-game-assets"></a>Importuj przykładowe zasoby gier

Podstawowe funkcje zostały przetestowane, a przedstawiona do pracy, jest zaimportować przykładowe zasoby gier.

## <a name="import-package"></a>Importowanie pakietu

1. Pobierz [przykładowe zasoby gier pakietu](https://github.com/dantogno/UnityAzureSample/blob/master/Azure%20Easy%20tables%20sample%20game%20assets.unitypackage).

2. Upewnij się, że Twój projekt Unity jest otwarty, a następnie przejdź do lokalizacji pobierania, a następnie kliknij dwukrotnie plik. Zostanie wyświetlone okno dialogowe importowania w Unity.

3. Kliknij przycisk **wszystkie** , a następnie kliknij przycisk **importu**. Poczekaj, aż wynikowy paski postępu zakończyć.

  ![Importowanie pakietu](media/vstu_azure-import-sample-assets-image1.png)

## <a name="add-scenes-to-build-settings"></a>Dodaj sceny w ustawieniach kompilacji

Po pliki zostały ukończone importowania, należy dodać pliki wymagane sceny w ustawieniach kompilacji projektu platformy Unity.

1. W oknie projektu Unity, przejdź do **łatwe tabel Azure przykładowe zasoby gier/sceny** katalogu.

2. Wybierz z Unity menu **Plik > Ustawienia kompilacji...** . Spowoduje to wyświetlenie okna dialogowego ustawienia kompilacji.

3. Przeciągnij **HeatmapScene**, **LeaderboardScene**, **MenuScene**, i **RaceScene** pliki z okna projektu do **Sceny w kompilacji** sekcji okna dialogowego ustawienia kompilacji.

  ![Importowanie pakietu](media/vstu_azure-import-sample-assets-image2.png)

4. Wybierz z Unity menu **pliku > zapisywania projektu** do zapewnienia ustawienia kompilacji zostaną zapisane.

## <a name="next-step"></a>Następny krok

* [Testowanie przykładowej gry](visual-studio-tools-for-unity-azure-game.md)