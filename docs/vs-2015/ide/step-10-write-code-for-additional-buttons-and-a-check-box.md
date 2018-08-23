---
title: 'Krok 10: Pisanie kodu dla dodatkowych przycisków i pola wyboru | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 254c01b6553c8abc647ab9041fdd6fdf5da63a70
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676561"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Krok 10. Zapisywanie kodu dla dodatkowych przycisków i pola wyboru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [krok 10: pisanie kodu dla dodatkowych przycisków i pola wyboru](https://docs.microsoft.com/visualstudio/ide/step-10-write-code-for-additional-buttons-and-a-check-box).  
  
Teraz możesz przystąpić do wykonania czterech pozostałych metod. Możesz skopiować i wkleić ten kod, ale jeśli chcesz dowiedzieć się maksymalnie dużo z tego samouczka, wpisz kod i korzystać z technologii IntelliSense.  
  
 Ten kod dodaje funkcje do dodanych wcześniej przycisków. Bez tego kodu przyciski nie robią niczego. Przyciski używają kodu w ich `Click` zdarzenia (a pola wyboru używają `CheckChanged` zdarzeń) do różnych akcji podczas aktywacji formantów. Na przykład `clearButton_Click` zdarzenia, które uaktywnia się po wybraniu **Wyczyść obraz** przycisk, partycje powoduje usunięcie bieżącego obrazu poprzez ustawienie jego `Image` właściwości `null` (lub `nothing`). Każde zdarzenie w kodzie zawiera komentarze objaśniające, co dany kod realizuje.  
  
 ![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo")wersja wideo tego tematu, zobacz [samouczek 1: tworzenie przeglądarki obrazów w Visual Basic – wideo 5](http://go.microsoft.com/fwlink/?LinkId=205216) lub [samouczek 1: tworzenie przeglądarki obrazów w języku C# - Film wideo 5](http://go.microsoft.com/fwlink/?LinkId=205206). W tych filmach wideo użyj wcześniejszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio.  
  
> [!NOTE]
>  Zgodnie z zaleceniami: zawsze komentarz w kodzie. Komentarze są informacjami dla osoby, które można odczytać i poświęcić czas na zrozumienie kodu. Wszystko w wierszu komentarza jest ignorowane przez program. W języku Visual C# wiersz komentarza tworzy się przez wpisanie dwóch ukośników na początku (/ /), a w języku Visual Basic wiersz komentarza tworzy się, zaczynając od pojedynczego cudzysłowu (').  
  
### <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Aby napisać kod dla dodatkowych przycisków i pola wyboru  
  
-   Dodaj następujący kod do pliku kodu formularza Form1 (Form1.cs lub Form1.vb). Wybierz **VB** kartę, aby wyświetlić kod języka Visual Basic.  
  
     [!code-csharp[VbExpressTutorial1Step9_10#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step9_10#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb#2)]  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 11: Uruchom swój Program i spróbuj innych funkcji](../ide/step-11-run-your-program-and-try-other-features.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 9: Przegląd, komentarz i kodu testu](../ide/step-9-review-comment-and-test-your-code.md).



