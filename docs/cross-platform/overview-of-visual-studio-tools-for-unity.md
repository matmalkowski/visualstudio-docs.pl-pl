---
title: "Omówienie narzędzi Visual Studio Tools for Unity | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4231bb9-45c4-4c77-ac3c-d05033b26393
caps.latest.revision: "4"
author: conceptdev
ms.author: crdun
manager: crdun
ms.openlocfilehash: 2af38cbebc1695a78a86d80240acc40c5463cbed
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/29/2017
---
# <a name="overview-of-visual-studio-tools-for-unity"></a>Omówienie narzędzi Visual Studio Tools for Unity
W tej sekcji dowiesz więcej o funkcjach programu Visual Studio Tools dla oferty Unity i jak można je staną się bardziej wydajnej pracy z Unity.  

 Program Visual Studio Tools for Unity (*pomocą rozszerzenia VSTU*), można użyć programu Visual Studio zapisu gry i Edytor skryptów w języku C#, a następnie użyć jego doskonałego debugera do znajdowania i naprawiania błędów. Najnowszą wersję pomocą rozszerzenia VSTU obejmuje kolorowania dla języka programu do cieniowania ShaderLab Unity firmy, lepsze wizualizacje debugera i generowanie kodu ulepszone MonoBehavior kreatora. Pomocą rozszerzenia VSTU oferuje również plików projektu Unity, komunikaty konsoli i możliwość uruchamiania gry w programie Visual Studio, aby móc poświęcić mniej czasu przełączanie z edytora Unity podczas pisania kodu.  

 Kontynuuj lekturę, aby dowiedzieć się więcej o tych funkcjach.  

## <a name="integration-with-unity"></a>Integracja z Unity  
 Visual Studio Tools for Unity byłoby wzmacniacz wydajność, gdyby przełączać się między Edytor platformy Unity i Visual Studio cały czas. Dlatego Visual Studio Tools for Unity ułatwia zachowanie podczas pracy bez opuszczania programu Visual Studio.  

-   **Eksplorator projektów Unity** cały projekt środowiska Unity w programie Visual Studio przy użyciu tej samej hierarchii, które są wyświetlane w edytorze Unity.  

-   Integracja z konsoli platformy Unity wyświetla dane wyjściowe z konsoli platformy Unity wewnątrz błędów w oknie programu Visual Studio.  

-   Uruchom profilowanie gry z programu Visual Studio — nie trzeba przełączyć się do platformy Unity, wystarczy nacisnąć klawisz F5.  

## <a name="superior-debugging"></a>Przełożony debugowania  
 Połącz doskonałego debugera programu Visual Studio do gry środowiska Unity do debugowania skryptów C# i bibliotek DLL, niezależnie od tego, czy jest uruchomiony autonomiczny lub Edytor platformy Unity. Można użyć wszystkich funkcji debugowania oczekiwanych z programu Visual Studio.  

-   Punkty przerwania w tym warunkowych punktów przerwania.  

-   Należy ocenić wyrażenia złożone w oknie wyrażeń kontrolnych.  

-   Sprawdzanie i modyfikowanie wartości zmiennych i argumentów.  

-   Przechodzenie do złożonych struktury obiektów i danych.  

 Gry środowiska Unity można debugować nawet po uruchomieniu na inny komputer w sieci.  

## <a name="productivity"></a>Wydajność  
 Oprócz wydajności ustanowionych Visual Studio do pisania i refaktoryzacji kodu w języku C# Visual Studio Tools for Unity udostępnia funkcje dodatkowe wydajności dla deweloperów platformy Unity.  

-   Kolorowania dla języka ShaderLab Unity pomaga dodatkowe błędy w Twojej programów do cieniowania, zanim staną się usterki. Po prostu otwórz pliki ShaderLab w programie Visual Studio.  

-   Kreator MonoBehavior pozwala przeglądać listę zachowania Unity i tworzy schematyczny kod służący do zachowania, nie może być doświadczenia w obsłudze. Naciśnij klawisze CTRL + SHIFT + M.  

-   Po zapoznaniu się z najczęściej używanych zachowania Unity się, Kreator szybkie MonoBehavior umieszcza je w zasięgu ręki. Naciśnij klawisze CTRL + ALT + Q.  

-   Dostęp do dokumentacji Unity w programie Visual Studio. Po prostu zaznacz wywołania interfejsu API, które chcesz Dowiedz się więcej o, a następnie naciśnij klawisz CTRL + ALT + M, CTRL + H.  

-   Dostęp do tych funkcji i więcej za pomocą skrótów klawiaturowych.  

## <a name="visual-studio-tools-for-unity-api"></a>Visual Studio tools dla Unity interfejsu API  
 Dostosowywanie i rozszerzanie zachowanie programu Visual Studio Tools for Unity za pomocą podanego interfejsów API.  

-   Visual Studio Tools for Unity rejestruje wywołanie zwrotne dziennika, więc można przesłać strumieniowo konsoli Unity do programu Visual Studio. Jeśli masz edytora skryptów, które rejestruje informacje, można je podłączyć do tego samego wywołania zwrotnego do wysyłania wiadomości do programu Visual Studio. Aby uzyskać więcej informacji zobacz przykład wywołanie zwrotne dziennika.  

-   Można zmienić, jak Visual Studio Tools for Unity generuje pliki projektu przy użyciu wywołania zwrotnego styl Unity ProjectFileGeneration. Aby uzyskać więcej informacji zobacz przykład Generowanie pliku projektu.  

## <a name="see-also"></a>Zobacz też  
 [Strona główna Unity](http://unity3d.com)
