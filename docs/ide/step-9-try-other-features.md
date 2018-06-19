---
title: 'Krok 9: Próbowanie innych funkcji'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc842af3723a8b056d1de684bd798f4fda37cff8
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32065081"
---
# <a name="step-9-try-other-features"></a>Krok 9: Próbowanie innych funkcji
Aby dowiedzieć się więcej, spróbuj zmienić ikony i kolory, dodać czasomierz gry i dźwięki. Aby gra była bardziej wymagająca, spróbuj zwiększyć planszę i dostosować czasomierz.  
  
 Aby pobrać ukończoną wersję przykładu, zobacz [całą pasującego gier samouczek próbkę](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).  
  
## <a name="to-try-other-features"></a>Aby wypróbować inne funkcje  

-   Zamień ikony i kolory na własne.  

    > [!TIP]
    >  Spróbuj patrzeć etykiety [Forecolor](http://msdn.microsoft.com/library/system.windows.forms.control.forecolor.aspx) właściwości.  

-   Dodaj czasomierz gry, który śledzi, jak długo graczowi zajmuje zakończenie gry.  

    > [!TIP]
    >  Aby to zrobić, można dodać etykietę do wyświetlania czas, który upłynął na powyższym formularzu <xref:System.Windows.Forms.TableLayoutPanel>, i dodać innego czasomierza do formularza w celu monitorowania czasu. Użyj kodu uruchamiającego czasomierz, gdy gracz rozpoczyna grę, i zatrzymującego czasomierz po dopasowaniu ostatnich dwóch ikon.  

-   Dodaj dźwięk, gdy gracz znajdzie dopasowanie, inny dźwięk, gdy gracz odkrywa dwie ikony, które nie pasują, a trzeci dźwięk, gdy program ukrywa ikony ponownie.  

    > [!TIP]
    >  Odtwarzanie dźwięków, można użyć <xref:System.Media> przestrzeni nazw. Zobacz [odtwarzać dźwięki w aplikacji formularzy systemu Windows (C#)](http://youtu.be/qOh4ooHg1UU) lub [odtwarzanie dźwięku w języku Visual Basic](http://youtu.be/-4oPDeQrtMs) Aby uzyskać więcej informacji.  
  
-   Utrudnij grę, zwiększając planszę.  

    > [!TIP]
    >  Należy do więcej niż tylko dodawanie wierszy i kolumn do formantu TableLayoutPanel - również należy wziąć pod uwagę liczbę ikony, którą utworzysz.  

-   Utrudnij grę, ukrywając pierwszą ikonę, jeśli gracz reaguje zbyt wolno i nie wybiera drugiej ikony w określonym czasie.  

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Jeśli masz problem lub pytania dotyczące programowania, spróbuj zadać pytanie na jednym z forów MSDN. Zobacz [forum Visual Basic](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) i [forum Visual C#](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral).  
  
-   Są tam dostępne wspaniałe, bezpłatne materiały szkoleniowe wideo. Aby dowiedzieć się więcej na temat programowania w języku Visual Basic, zobacz [podstawy języka Visual Basic: Programowanie dla początkujących bezwzględną](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Aby dowiedzieć się więcej na temat programowania w języku języka Visual C#, zobacz [podstawy języka C#: Programowanie dla początkujących bezwzględną](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 8: Dodaj metodę, aby sprawdzić, czy gracz wygrał](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
