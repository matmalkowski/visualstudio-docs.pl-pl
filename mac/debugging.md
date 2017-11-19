---
title: "Debugowanie za pomocą platformy Xamarin | Dokumentacja firmy Microsoft"
description: "Debugowanie jest typowe i konieczne, część programowania. Jako dojrzałe środowiska IDE programu Visual Studio for Mac zawiera całego zestawu funkcji Łatwe debugowanie. Z bezpiecznego debugowania, do wizualizacji danych, w tym artykule będzie opisano sposób użycia potencjał debugowania w programie Visual Studio dla komputerów Mac."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-debug
ms.assetid: BB7A084D-9AC2-48B5-8076-6C8518796BBA
ms.openlocfilehash: 6d85c318b60e065be86d242bf3199b3716c59ada
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-with-xamarin"></a>Debugowanie za pomocą platformy Xamarin


Visual Studio for Mac ma debuger natywny umożliwiająca obsługę debugowania dla aplikacji platformy Xamarin.iOS Xamarin.Mac i platformy Xamarin.Android.
Programu Visual Studio for Mac używa [ *debugera nietrwałego Mono*](http://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger/), która jest zaimplementowana w czasie wykonywania Mono, dzięki czemu Visual Studio dla komputerów Mac do debugowania kodu zarządzanego na wszystkich platformach.

## <a name="the-debugger"></a>Debuger

Visual Studio for Mac używa debugera nietrwałego Mono do debugowania kodu zarządzanego (C# lub języka F #) we wszystkich aplikacjach Xamarin. Debuger Mono nietrwałego różni się od regular debuger w tym jest współpracy debugera, korzysta z wbudowanej w czasie wykonywania Mono; wygenerowany kod i Mono środowiska uruchomieniowego współpracować z IDE w celu zapewnienia obsługi debugowania. Środowisko uruchomieniowe Mono dostęp do debugowania funkcji przy użyciu protokołu danych przesyłanych w sieci, który można uzyskać więcej informacji [w dokumentacji Mono](http://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger-wire-format/).


Twarde debugery, takich jak [LLDB]( http://lldb.llvm.org/index.html) lub [GDB]( https://www.gnu.org/software/gdb/), sterowania programem bez wiedzy lub współpracy z debugowanego programu, ale może być użyteczny podczas debugowania aplikacji platformy Xamarin w zdarzeniu które Musisz debugować natywnego systemu iOS lub Android kodu.

## <a name="using-the-debugger"></a>Korzystanie z debugera

Aby rozpocząć debugowanie dowolnej aplikacji, upewnij się, że konfiguracja jest ustawiona na **debugowania**. Konfiguracja debugowania udostępnia przydatne zestaw narzędzi do obsługi debugowania, takich jak punkty przerwania, przy użyciu danych wizualizatorów i wyświetlając stosu wywołań:

![Konfiguracja debugowania](media/debugging-image_0.png)

## <a name="setting-a-breakpoint"></a>Ustawienia punktu przerwania

Aby ustawić punkt przerwania w środowiskiem IDE, kliknij obszar marginesu edytora obok numer wiersza kodu, w którym chcesz przerwać:

![Ustawianie punktów przerwania w margines](media/debugging-image0.png)


Można wyświetlić wszystkie punkty przerwania, które zostały ustawione w kodzie, przechodząc do **konsoli punktów przerwania**:

![Lista punktów przerwania](media/debugging-image0a.png)


## <a name="start-debugging"></a>Rozpocznij debugowanie

Aby rozpocząć debugowanie, wybierz urządzenie docelowe lub podobne/emulatora w środowiskiem IDE:

![Wybierz urządzenie docelowe](media/debugging-image1.png)

Następnie Wdróż aplikację, naciskając klawisz **odtwarzanie** przycisku lub **Cmd + return**. Po trafieniu punktu przerwania kod będzie wyróżniony żółty:

![Został trafiony punkt przerwania przedstawiający wyróżnienia](media/debugging-image2.png)

Debugowanie narzędzi, takich jak używany do sprawdzenia wartości obiektów, można w tym momencie uzyskać więcej informacji o tym, co się dzieje w kodzie:

![Debugowanie wizualizacji](media/debugging-image3.png)

## <a name="conditional-breakpoints"></a>Warunkowe punkty przerwania

Można również ustawić reguły, dyktowania okoliczności, w których punkt przerwania powinna się odbyć, jest to nazywane Dodawanie *warunkowych punktów przerwania*. Aby ustawić warunkowe punktu przerwania, Uzyskaj dostęp do **okna Właściwości punktu przerwania**, które można wykonać na dwa sposoby:


* Aby dodać nowego punktu przerwania warunkowego, kliknij prawym przyciskiem myszy na marginesie edytor z lewej strony numer wiersza dla kodu, który chcesz ustawić punkt przerwania i wybierz nowego punktu przerwania:


 ![Menu kontekstowe punktu przerwania](media/debugging-image4.png)

* Aby dodać warunek do istniejącego punktu przerwania, kliknij prawym przyciskiem myszy punkt przerwania i wybierz **właściwości punktu przerwania**, lub w **konsoli punktów przerwania**, kliknij przycisk Edytuj punktu przerwania zostały pokazane poniżej:


 ![Edytuj istniejący punkt przerwania w konsoli punkty przerwania](media/debugging-image5.png)


Następnie możesz wprowadzić warunku, pod którym ma nastąpić punktu przerwania:

 ![Edytowanie warunków punktu przerwania](media/debugging-image6.png)

## <a name="stepping-through-code"></a>Krokowe wykonywanie kodu

Po osiągnięciu punktu przerwania, narzędzi debugowania umożliwiają uzyskanie kontrolę nad wykonywania programu. Visual Studio for Mac wyświetli czterech przycisków, umożliwiając uruchamianie i wykonywać krokowo kodu. W programie Visual Studio dla komputerów Mac będzie mieć następującą postać:

 ![Przyciski do wykonania kroków opisanych kodu](media/debugging-image7.png)

Poniżej przedstawiono cztery przyciski:

*   **Odtwórz** — to rozpocznie się wykonywanie kodu, aż do następnego punktu przerwania.
*   **Step Over** — powoduje uruchomienie następnego wiersza kodu. Następnego wiersza po wywołaniu funkcji Step Over wykona funkcji i zatrzyma się w następnym wierszu kodu *po* funkcji.
*   **Step Into** — powoduje również uruchomienie następnego wiersza kodu. Następnego wiersza po wywołaniu funkcji Step Into przestanie w pierwszym wierszu funkcji, co pozwala na kontynuowanie wiersz po wierszu debugowanie funkcji. Jeśli następnego wiersza nie jest funkcją, działają taka sama jak Step Over.
*   **Step Out** — to nastąpi powrót do wiersza której wywołano bieżącej funkcji.


## <a name="debugging-monos-class-libraries"></a>Debugowanie bibliotek klas w jedno
Xamarin produkty są dostarczane z kodu źródłowego dla bibliotek klas w jedno i służy do pojedynczego kroku z debugera Aby sprawdzić, jak działają pod maską rzeczy.

Ponieważ ta funkcja wymaga większej ilości pamięci podczas debugowania, domyślnie jest ona wyłączona.

Aby włączyć tę funkcję, należy przejść do **programu Visual Studio for Mac > Preferencje > debugera** i upewnij się, że "**debugować kod projektu. nie wykonywanie kodu framework.** " opcja jest **niezaznaczone**, jak pokazano poniżej:

 ![Nie Wkrocz framework kod — opcja](media/debugging-image8.png)
