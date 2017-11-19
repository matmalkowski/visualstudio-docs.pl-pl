---
title: "Krok 9: Próbowanie innych funkcji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: "11"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 35c91ef4ad9493e47aa72a4b27dc1286a18adf3a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="step-9-try-other-features"></a>Krok 9. Próbowanie innych funkcji
Aby dowiedzieć się więcej, spróbuj zmienić ikony i kolory, dodać czasomierz gry i dźwięki. Aby gra była bardziej wymagająca, spróbuj zwiększyć planszę i dostosować czasomierz.  
  
 Aby pobrać ukończoną wersję przykładu, zobacz [przykładowy samouczek pełne dopasowanie gry](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).  
  
### <a name="to-try-other-features"></a>Aby wypróbować inne funkcje  
  
-   Zamień ikony i kolory na własne.  
  
    > [!TIP]
    >  Spróbuj patrzeć etykiety [Forecolor](http://msdn.microsoft.com/library/system.windows.forms.control.forecolor.aspx) właściwości.  
  
-   Dodaj czasomierz gry, który śledzi, jak długo graczowi zajmuje zakończenie gry.  
  
    > [!TIP]
    >  Aby to zrobić, możesz dodać etykietę wyświetlającą czas, który upłynął, na formularzu powyżej TableLayoutPanel, i dodaj inny czasomierz do formularza w celu śledzenia czasu. Użyj kodu uruchamiającego czasomierz, gdy gracz rozpoczyna grę, i zatrzymującego czasomierz po dopasowaniu ostatnich dwóch ikon.  
  
-   Dodaj dźwięk, gdy gracz znajdzie dopasowanie, inny dźwięk, gdy gracz odkrywa dwie ikony, które nie pasują, a trzeci dźwięk, gdy program ukrywa ikony ponownie.  
  
    > [!TIP]
    >  Aby odtwarzać dźwięki, możesz użyć przestrzeni nazw System.media. Zobacz [odtwarzanie dźwięków w aplikacji formularzy systemu Windows (C# .NET)](http://youtu.be/qOh4ooHg1UU) lub [jak do odtwarzania Audio w języku Visual Basic](http://youtu.be/-4oPDeQrtMs) Aby uzyskać więcej informacji.  
  
-   Utrudnij grę, zwiększając planszę.  
  
    > [!TIP]
    >  Należy do więcej niż tylko dodawanie wierszy i kolumn do formantu TableLayoutPanel - również należy wziąć pod uwagę liczbę ikony, którą utworzysz.  
  
-   Utrudnij grę, ukrywając pierwszą ikonę, jeśli gracz reaguje zbyt wolno i nie wybiera drugiej ikony w określonym czasie.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Jeśli masz problem lub pytania dotyczące programowania, spróbuj zadać pytanie na jednym z forów MSDN. Zobacz [Forum Visual Basic](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) i [Forum Visual C#](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral).  
  
-   Są tam dostępne wspaniałe, bezpłatne materiały szkoleniowe wideo. Aby dowiedzieć się więcej na temat programowania w języku Visual Basic, zobacz [podstawy języka Visual Basic: Programowanie dla początkujących bezwzględną](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Aby dowiedzieć się więcej na temat programowania w języku języka Visual C#, zobacz [podstawy języka C#: Programowanie dla początkujących bezwzględną](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 8: Dodawanie metody, aby sprawdzić, czy gracz wygrał](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).