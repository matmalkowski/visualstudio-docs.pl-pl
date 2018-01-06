---
title: "Wyświetl stos wywołań w debugerze programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 04/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.callstack
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
caps.latest.revision: "40"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e10b81ff07b77e2fd6202d2f5fb27392fe8134c2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-visual-studio-debugger"></a>Wyświetl stos wywołań i korzystanie z okna stosu wywołań w debugerze programu Visual Studio

Za pomocą **stos wywołań** okna, można wyświetlić wywołania funkcji lub procedury, które są obecnie na stosie. **Stos wywołań** okno zawiera kolejność, w którym są pobierania wywoływane metody i funkcje. Stos wywołań jest dobrze do badania i zrozumienie przepływu wykonywania aplikacji.
  
Gdy [symbole debugowania](#bkmk_symbols) nie są dostępne dla części stos wywołań, **stos wywołań** okno może nie móc wyświetlić poprawne informacje dla tej części stosu wywołań. Jeśli to miejsce, pojawi się następujący Notacja:  
  
`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

>  [!NOTE]
> **Stos wywołań** jest podobne do perspektywy debugowania w niektórych IDEs, takich jak Eclipse. 

> [!NOTE]
>  Okna dialogowe i dostępne polecenia menu mogą różnić się od opisanych tutaj, w zależności od wersji lub aktywne ustawienia. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.  Zobacz [personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md)
  
## <a name="view-the-call-stack-while-in-the-debugger"></a>Wyświetlić stosu wywołań znajduje się w debugerze 
  
-   Podczas debugowania w **debugowania** menu, wybierz opcję **Windows > stos wywołań**.

 ![Stos wywołań, okno](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Żółta strzałka identyfikuje ramki stosu, w którym aktualnie znajduje się wskaźnik wykonywania. Domyślnie jest to ramki stosu, którego informacje są wyświetlane w źródle, **zmiennych lokalnych**, **automatycznych**, **czujki**, i **dezasemblacji** systemu windows . Jeśli chcesz zmienić kontekstu debugera do innej ramki na stosie, możesz to zrobić [przełączanie do innej ramki stosu](#bkmk_switch).   
  
## <a name="display-non-user-code-in-the-call-stack-window"></a>Wyświetlanie kodu innych użytkowników w oknie stosu wywołań  
  
-   Kliknij prawym przyciskiem myszy **stos wywołań** i zaznacz **Pokaż kod zewnętrzny**.

Kod użytkownika nie jest kodu, który nie jest wyświetlany podczas [tylko mój kod](../debugger/just-my-code.md) jest włączona. W kodzie zarządzanym ramki kodu innych użytkowników są domyślnie ukryte. Następujące notacji pojawia się zamiast ramki kodu innych użytkowników:  
  
**[\<Kod zewnętrzny >]**  
  
## <a name="bkmk_switch"></a>Przełącz do innej ramki stosu (zmienianie kontekstu debugera)
  
1.  W **stos wywołań** okna, kliknij prawym przyciskiem myszy ramek stosu, którego kod i dane, które chcesz wyświetlić.

    Lub możesz kliknąć dwukrotnie ramkę w **stos wywołań** okna, aby przełączyć się do zaznaczonej ramki. 
  
2.  Wybierz **Przełącz do ramki**.  
  
     Zielona strzałka z nawiasy tail obok wybranej ramki stosu. Wskaźnik wykonywania pozostaje w oryginalnym ramki, który jest nadal oznaczony atrybutem żółta strzałka. W przypadku wybrania **krok** lub **Kontynuuj** z **debugowania** menu ramki pierwotnej będzie kontynuować wykonywania, nie ramkę wybrane.  
  
## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Wyświetlanie kodu źródłowego funkcji w stosie wywołań  
  
-   W **stos wywołań** okna, kliknij prawym przyciskiem myszy funkcja źródłem kod chcesz wyświetlić i wybrać **przejdź do kodu źródłowego**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Uruchamianie określonych funkcji w oknie stosu wywołań  
  
-  W **stos wywołań** okna, wybierz funkcję, kliknij prawym przyciskiem myszy i wybierz opcję **Uruchom do kursora**.  
  
## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Ustaw punkt przerwania w punkcie wyjścia wywołania funkcji  
  
-   Zobacz [Ustaw punkt przerwania w funkcji stosu wywołań](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).

## <a name="display-calls-to-or-from-another-thread"></a>Wyświetlanie wywołań do lub z innego wątku  
  
-   Kliknij prawym przyciskiem myszy **stos wywołań** i zaznacz **obejmują wątków inne To/From wywołania**.   
  
## <a name="visually-trace-the-call-stack"></a>Wizualne śledzenie stosu wywołań  

Jeśli używasz Visual Enterprise Studio (tylko), można wyświetlić map kodu do stosu wywołań podczas debugowania.

- W **stos wywołań** okna, otwórz menu skrótów. Wybierz **Pokaż stos wywołań w mapie kodu**. (Klawiatury: **CTRL** + **SHIFT** + **`**)  
  
    Aby uzyskać szczegółowe informacje, zobacz [metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Pokazywanie w mapie kodu stosu wywołań](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")
  
## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack"></a>Wyświetlanie kodu dezasemblacji funkcji w stosie wywołań  
  
-   W **stos wywołań** okna, kliknij prawym przyciskiem myszy funkcji, których dezasemblacji kod chcesz wyświetlić i wybrać **przejść do dezasemblacji**.    

## <a name="change-the-optional-information-displayed"></a>Zmień wyświetlane informacje opcjonalne  
  
-   Kliknij prawym przyciskiem myszy **stos wywołań** okna i zestawu lub wyczyść **Pokaż \<**  *informacji, które mają*  **>** .  
  
## <a name="bkmk_symbols"></a>Załadować symbole dla modułu
W **stos wywołań** okna, można załadować symboli dla kodu, który nie ma obecnie załadować symboli debugowania. Symbole można .NET Framework lub symbole systemu pobrane z serwerów symboli publicznych firmy Microsoft lub symbole w ścieżce symboli na komputerze, który debugowania.  
  
Zobacz [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
### <a name="to-load-symbols"></a>Aby załadować symbole  
  
1.  W **stos wywołań** okna, kliknij prawym przyciskiem myszy ramki stosu dla symboli, które nie zostały załadowane. Ramki będą nieaktywne.  
  
2.  Wskaż **załadować symbole** , a następnie kliknij przycisk **serwerów symboli firmy Microsoft** (jeśli jest dostępny) lub przejdź do ścieżki symboli.  
  
### <a name="to-set-the-symbol-path"></a>Aby ustawić ścieżkę symboli  
  
1.  W **stos wywołań** okna, wybierz **ustawienia** z menu skrótów.  
  
     **Opcje** zostanie otwarte okno dialogowe i **symbole** zostanie wyświetlona strona.  
  
2.  Kliknij przycisk **symbolu ustawienia**.  
  
3.  W **opcje** okna dialogowego kliknij ikonę folderu.  
  
     W **symboli (.pdb) lokalizacje** polu jest wyświetlany kursor.  
  
4.  Wpisz nazwa ścieżki do lokalizacji symboli na komputerze, który debugowania. Lokalne i zdalne debugowanie, jest to ścieżka na komputerze lokalnym.
  
5.  Kliknij przycisk **OK** zamknąć **opcje** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Kod mieszany i brakujące informacje w oknie stosu wywołań](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)  
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)   
 [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Używanie punktów przerwania](../debugger/using-breakpoints.md)