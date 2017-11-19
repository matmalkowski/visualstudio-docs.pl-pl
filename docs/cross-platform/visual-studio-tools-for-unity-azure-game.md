---
title: "Visual Studio Tools for Unity Azure wskazówki gry | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: DA86FC7F-E456-4DFC-84BF-D780421508B9
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 204389c2341c3aa9f729b92b5f3d459e7b101d24
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="test-the-sample-game"></a>Testowanie gry próbki

Gry przykładowe to proste wyścigowych gra rejestruje dane o zachowaniu odtwarzacza i zapisuje go w łatwy tabel Azure. Gry próbki także sceny, które odczytać danych z platformy Azure i wizualizację go odtwarzacza.

W tej sekcji po prostu objaśnia sposób gry próbki i upewnij się, że działa on prawidłowo. Następne sekcje zostaną umieszczone w bardziej szczegółowo wyjaśniający, jak działa gry próbki.

## <a name="starting-the-game"></a>Rozpoczynanie gry

1. W oknie projektu Unity, przejdź do **tabel łatwe zasoby/Azure przykładowe zasoby gier/sceny** folderu.

2. Kliknij dwukrotnie **MenuScene** go otworzyć.

3. Kliknij w oknie gry środowiska Unity **listy rozwijanej współczynnik proporcji** i wybierz polecenie **16:9**.

  ![Współczynnik proporcji zestawu](media/vstu_azure-test-sample-game-image1.png)

4. Kliknij przycisk **odtwarzanie** przycisku do uruchomienia gry w edytorze Unity.


## <a name="complete-a-race"></a>Zakończenie wyścigu

Przed wyświetleniem Liderzy lub heatmap, najlepiej utworzyć przykładowych danych, wykonując wyścigu co najmniej raz.

1. Gry uruchomione w edytorze Unity, kliknij polecenie **wyścigu!** przycisk, aby uruchomić nowe wyścigu.

2. Użyj **WASD** lub **klawiszy strzałek** do napędu samochód i ukończyć zegara laptop wokół ścieżki. Ze względu na przykład należy awarii w niektórych ściany wzdłuż sposób. Dane wyjściowe w Unity konsoli powinny wskazywać, gdy zarejestrowano kolizji debugowania.

  >[!NOTE]
  > Jeśli zarządzanie do przerzucenia samochodu i nie można kontynuować, kliknij przycisk **ponownego uruchomienia**. Dane są wysyłane tylko na platformie Azure, po zakończeniu laptop.

  ![Uruchom wyścigu](media/vstu_azure-test-sample-game-image2.png)

3. Po przekroczeniu szachownicą zakończenia wiersza, powinien być wyświetlany gry **Zakończono** wiadomości. W tym momencie awarii danych zostanie przekazany do platformy Azure.

4. Po zakończeniu laptop najszybszym 10 pierwszych czasu, zostanie wyświetlony monit o wprowadzenie nazwy wysokiej oceny. Wprowadź nazwę, a następnie kliknij przycisk **przesyłania**.

  ![Uruchom wyścigu](media/vstu_azure-test-sample-game-image3.png)

## <a name="view-the-heatmap"></a>Widok heatmap

1. Kliknij przycisk **Heatmap awarii widoku** przycisk z wyścigu sceny lub wybierz **awarii Heatmap** z poziomu menu głównego.

2. Sceny heatmap ładuje dane z tabeli CrashInfo na platformie Azure i wyświetla przezroczysty kuli red w lokalizacjach, w którym gracze mają kolidują z ściany Śledź wyścigu. W razie wystąpienia awarii w wielu w nakładające się obszaru, obszary powinna pojawić się jaśniejszy.

  ![Heatmap](media/vstu_azure-test-sample-game-image4.png)

## <a name="view-the-leaderboard"></a>Widok Liderzy

1. Kliknij przycisk **Liderzy** przycisk od wyścigu sceny lub menu głównego.

2. Sceny Liderzy ładuje najlepszy wynik danych z tabeli HighScoreInfo w Azure i wyświetla czas player nazwy i laptop dla każdego wysokiej wynik zapisu.

  ![Liderzy](media/vstu_azure-test-sample-game-image5.png)

## <a name="next-step"></a>Następny krok

* [Wyjaśnienie RaceScene](visual-studio-tools-for-unity-azure-racescene.md)
