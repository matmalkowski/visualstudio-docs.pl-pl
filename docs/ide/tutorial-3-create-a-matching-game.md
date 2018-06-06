---
title: 'Samouczek 3: Tworzenie pasujący gier'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3358d23c7c4f3fd2ad7f6beffb6a035b6c810d38
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747981"
---
# <a name="tutorial-3-create-a-matching-game"></a>Samouczek 3: Tworzenie pasujący gier
W tym samouczku stworzysz grę w dopasowywanie, gdzie gracz musi dopasować pary ukrytych ikon. Dowiesz się, jak:

-   Przechowywanie obiekty, takie jak ikony, w <xref:System.Collections.Generic.List%601> obiektu.

-   Użyj `foreach` pętli języka Visual C# lub `For Each` pętli w języku Visual Basic do iteracji elementów na liście.

-   Śledzić stan formularza za pomocą zmiennych odwołania.

-   Stworzyć program obsługi zdarzeń w celu reagowania na zdarzenia, którego możesz używać z wieloma obiektami.

-   Stworzyć czasomierz, który odlicza czas do zera, a następnie uruchamia zdarzenie dokładnie jeden raz po uruchomieniu.

 Po zakończeniu samouczka program będzie wyglądać tak, jak na poniższej ilustracji.

 ![Gry utworzone w tym samouczku](../ide/media/express_finishedgame.png) gry utworzonego w ramach tego samouczka

## <a name="tutorial-links"></a>Samouczek łącza

 Aby pobrać ukończoną wersję przykładu, zobacz [całą pasującego gier samouczek próbkę](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

> [!NOTE]
>  W tym samouczku omówiono zarówno Visual C#, jak i Visual Basic, więc skoncentruj się na informacjach specyficznych dla języka programowania, którego używasz.

 Jeśli masz problem lub pytania dotyczące programowania, spróbuj zadać pytanie na jednym z forów MSDN. Zobacz [forum Visual Basic](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) i [forum Visual C#](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral). Dostępne są tam również wspaniałe, bezpłatne materiały szkoleniowe wideo. Aby dowiedzieć się więcej na temat programowania w języku Visual Basic, zobacz [podstawy języka Visual Basic: Programowanie dla początkujących bezwzględną](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Aby dowiedzieć się więcej na temat programowania w języku języka Visual C#, zobacz [podstawy języka C#: Programowanie dla początkujących bezwzględną](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Krok 1: Tworzenie projektu i Dodawanie tabeli do formularza](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Rozpocznij od utworzenia projektu i dodaniu `TableLayoutPanel` formantu, aby zachować formanty prawidłowo wyrównane.|
|[Krok 2: Dodawanie obiektu losowego i listy ikon](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Dodaj `Random` obiektu i `List` obiektu umożliwia utworzenie listy ikon.|
|[Krok 3: Przypisanie losowej ikony do każdej etykiety](../ide/step-3-assign-a-random-icon-to-each-label.md)|Przypisz losowo do ikony `Label` kontrolki, aby każda gra jest inna.|
|[Krok 4: Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Dodaj `Click` obsługi zdarzeń, który zmienia kolor etykiety, dla której zostanie kliknięty.|
|[Krok 5: Dodawanie odwołań do etykiet](../ide/step-5-add-label-references.md)|Dodaj zmienne odwołania, aby śledzić, które etykiety zostały kliknięte.|
|[Krok 6: Dodawanie czasomierza](../ide/step-6-add-a-timer.md)|Dodaj czasomierz do formularza, aby śledzić czas, który upłynął w grze.|
|[Krok 7: Zachowanie widoczności par](../ide/step-7-keep-pairs-visible.md)|Zachowaj widoczne pary ikon, jeśli wybrana para pasuje.|
|[Krok 8: Dodanie metody sprawdzania, czy gracz wygrał](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Dodaj `CheckForWinner()` metody, aby sprawdzić, czy gracz wygrał.|
|[Krok 9: Próbowanie innych funkcji](../ide/step-9-try-other-features.md)|Wypróbuj inne funkcje, takie jak zmiana ikon i kolorów, dodawanie siatki i dodawanie dźwięków. Spróbuj powiększyć planszę i dostosować czasomierz.|
