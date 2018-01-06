---
title: "Przejdź do definicji i definicji wglądu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code editor, go to definition
- code editor, peek definition
- go to definition
- peek definition
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: db67f01ff2a58ee856e4588df8770fc4edef8ca2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="go-to-definition-and-peek-definition"></a>Przejdź do definicji i definicji wglądu  
Przejdź do definicji i wgląd definicji funkcji umożliwiają łatwe wyświetlanie definicji typu lub elementu członkowskiego.

## <a name="go-to-definition"></a>Przejdź do definicji  
Przejdź do definicji funkcji przechodzi do źródła typu lub elementu członkowskiego i otwiera wynik na nowej karcie. Jeśli jesteś użytkownikiem klawiatury, umieść kursor tekstu gdzieś wewnątrz nazwy symbolu i naciśnij klawisz **F12**. Jeśli jesteś użytkownikiem myszy albo wybierz **przejdź do definicji** z menu kontekstowego lub użyj **klawisz Ctrl** funkcje opisane poniżej.  

### <a name="ctrl-click-go-to-definition"></a>Klawisz CTRL, przejdź do definicji  
W programie Visual Studio 2017 wersji 15.4 jest prostszy sposób dla użytkowników myszy szybki dostęp do przejdź do definicji. Symbole stają się aktywne po naciśnięciu **Ctrl** i zatrzymaj wskaźnik myszy typu lub elementu członkowskiego. Aby szybko przejść do definicji symbolu, naciśnij klawisz **Ctrl** klucza, a następnie kliknij go. To bardzo proste!

![Przejdź do definicji animacji kliknięcia myszą](../ide/media/click_gotodef.gif)

Można zmienić klucz modyfikujący na kliknięcie myszą **przejdź do definicji** , przechodząc do **narzędzia**, **opcje**, **Edytor tekstu**, **Ogólne**i wybierając jedną **Alt** lub **klawisze Ctrl + Alt** z **klawisz modyfikujący użyj** listy rozwijanej. Można również wyłączyć kliknięcia myszą **przejdź do definicji** usuwając zaznaczenie pola wyboru **Włącz myszy kliknij, aby wykonać przejdź do definicji** wyboru.  

![Włączanie kliknięcia myszą przejdź do definicji](../ide/media/editor_options_mouse_click_gotodef.png)  

## <a name="peek-definition"></a>Definicji wglądu
Funkcja definicji wglądu umożliwia podgląd definicję typu bez opuszczania bieżącej lokalizacji w edytorze. Jeśli jesteś użytkownikiem klawiatury, umieść kursor tekstu gdzieś wewnątrz nazwy typu lub elementu członkowskiego i naciśnij klawisz **Alt + F12**. Jeśli jesteś użytkownikiem mysz, możesz wybrać **definicji wglądu** z menu kontekstowego. W Visual Studio 2017 wersji 15,4 i nowszych ma w nowy sposób wglądu w widoku definicji za pomocą myszy. Po pierwsze, przejdź do **narzędzia**, **opcje**, **Edytor tekstu**, **ogólne**. Wybierz opcję **Otwórz definicję w widoku peek** i kliknij przycisk **OK** zamknąć **opcje** okno dialogowe.  

![Ustawienie opcji definicji wglądu kliknięcia myszą](../ide/media/editor_options_peek_view.png)  

Naciśnij klawisz **Ctrl** (lub innego klawisz modyfikujący został wybrany w **opcje**) i kliknij polecenie typu lub elementu członkowskiego.  

![Podgląd animacji definicji](../ide/media/peek_definition.gif)

Jeśli wgląd inną definicję w oknie podręcznym, zostanie uruchomiona ścieżką nawigacją, której można nawigować przy użyciu okręgi i strzałki, które znajdują się powyżej menu podręcznego.  

Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie i Edycja kodu za pomocą wgląd definicji (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).  

## <a name="see-also"></a>Zobacz też  
[Nawigowanie po kodzie](../ide/navigating-code.md)  
[Instrukcje: Wyświetlanie i edytowanie kodu za pomocą polecenia Zobacz definicję (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)  
