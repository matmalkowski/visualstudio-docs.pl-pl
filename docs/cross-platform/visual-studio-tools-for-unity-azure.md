---
title: "Visual Studio Tools for Unity wskazówki Azure | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7921D4C7-5526-42F5-8E03-82D3E33A893F
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: a7e12508537a3bcda1df7997ba9e390b75b9beaf
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="using-azure-easy-tables-with-unity-walkthrough"></a>Za pomocą usługi Azure łatwe tabel z przewodnikiem Unity

![Zrzut ekranu gier próbki](media/vstu_azure-test-sample-game-image2.png)

## <a name="introduction"></a>Wprowadzenie

Platforma Azure oferuje skalowalne rozwiązanie do przechowywania danych telemetrycznych i inne dane gry w chmurze. Wraz z wydaniem Unity 2017 platformy Unity na obsługę .NET 4.6 sprawia, że integracja Azure prostsze niż kiedykolwiek zezwalając na korzystanie z zestawu SDK klienta usługi Azure Mobile.

Te kroki prowadzi przez proces konfigurowania projektu Unity, który korzysta z platformy Azure do zapisywania danych telemetrycznych i liderzy w chmurze.

> [!NOTE]
> Ten projekt wymaga "eksperymentalne".NET 4.6 Mono skryptów środowiska uruchomieniowego w Unity 2017 r. [Unity stwierdził, że wkrótce będzie to wartość domyślna](https://forum.unity3d.com/threads/future-plans-for-the-mono-runtime-upgrade.464327/), ale obecnie on nadal etykietą "eksperymentalne" i mogą wystąpić problemy.

> W tym przewodniku dokumentów przykład do połączenia z Komputerem Unity kompilacji zaplecza aplikacji mobilnej Azure. W momencie pisania tego dokumentu są znane problemy, które blokują tego projektu z działa na platformach Mac i Android. Gdy są one znane problemy, które zostanie rozwiązany, osi czasu jest wiedzą. Aby uzyskać więcej informacji, odwiedź stronę jednolitości [eksperymentalne forum skryptów](https://forum.unity3d.com/forums/experimental-scripting-previews.107/).

## <a name="download-the-completed-project"></a>Pobieranie ukończone projektu

Ukończono projektu jest dostępna w witrynie GitHub. Jednak przewodnika przyjmie, jest uruchamiany z pustą, nowego projektu i zapewni łącza do zasobów, gdy jest to konieczne.

## <a name="walkthrough-steps"></a>Kroki wskazówki

1. [Skonfigurowanie łatwego tabel na platformie Azure](visual-studio-tools-for-unity-azure-configure.md)
2. [Tworzenie tabel łatwe](visual-studio-tools-for-unity-azure-setup.md)
3. [Przygotuj Środowisko deweloperskie](visual-studio-tools-for-unity-azure-prepare.md)
4. [Tworzenie klasy modelu danych](visual-studio-tools-for-unity-azure-data.md)
5. [Implementowanie Azure MobileServiceClient](visual-studio-tools-for-unity-azure-mobile-client.md)
6. [Magazyn certyfikatów zabezpieczeń Unity Mono aktualizacji](visual-studio-tools-for-unity-azure-security.md)
7. [Testowanie połączenia klienta](visual-studio-tools-for-unity-azure-connection.md)
7. [Importuj przykładowe zasoby gier](visual-studio-tools-for-unity-azure-game-assets.md)
8. [Testowanie gry próbki](visual-studio-tools-for-unity-azure-game.md)
9. [Wyjaśnienie RaceScene](visual-studio-tools-for-unity-azure-racescene.md)
10. [Wyjaśnienie HeatmapScene](visual-studio-tools-for-unity-azure-heatmapscene.md)
11. [Wyjaśnienie LeaderboardScene](visual-studio-tools-for-unity-azure-leaderboardscene.md)


## <a name="next-step"></a>Następny krok
* [Skonfigurowanie łatwego tabel na platformie Azure](visual-studio-tools-for-unity-azure-configure.md)
