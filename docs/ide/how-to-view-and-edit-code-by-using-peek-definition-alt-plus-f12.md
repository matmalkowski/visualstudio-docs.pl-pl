---
title: "Porady: Podgląd i Edycja kodu za pomocą definicji wglądu (Alt + F12) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45f3dd20-902a-4047-8cca-9f18216123f4
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bf0dd4ab4a60dc7cfdfd351aee59c4942f75ef69
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Porady: Podgląd i edycja kodu za pomocą definicji wglądu (Alt+F12)
Można użyć **definicji wglądu** polecenie, aby wyświetlić i edytować kod bez przełączania od pisania kodu. **Podgląd definicji** i **przejdź do definicji** wyświetlane te same informacje, ale **definicji wglądu** zawiera go w oknie podręcznym i **przejdź do definicji** zawiera kod w oknie oddzielne kodu. **Przejdź do definicji** powoduje, że kontekst (oznacza to, że kod active okna, bieżącego wiersza, a pozycja kursora) przejść do definicji okna kodu. Za pomocą **definicji wglądu**, można wyświetlać i edytować definicję i poruszanie się w pliku definicji przy zachowaniu Twoje miejsce w oryginalnym pliku kodu.  
  
 Można użyć **definicji wglądu** z kodem C#, Visual Basic i C++. W języku Visual Basic **definicji wglądu** zawiera łącze do **przeglądarki obiektów** symboli, które nie mają definicji metadanych (na przykład, .NET Framework typy, które są wbudowane w).  
  
## <a name="working-with-peek-definition"></a>Praca z funkcją Zobacz definicję  
  
#### <a name="to-open-a-peek-definition-window"></a>Aby otworzyć okno Zobacz definicję    
1.  Możesz uzyskać wgląd definicji, wybierając **definicji wglądu** z menu kontekstowego dla elementu członkowskiego, który chcesz zapoznać. W Visual Studio 2017 wersji 15,4 i nowszych, jeśli opcja jest włączona, możesz również uzyskać wgląd definicji za pomocą myszy naciskając **Ctrl** (lub innego modyfikatora) i kliknij nazwę elementu członkowskiego. Lub z klawiatury, naciśnij klawisz **Alt + F12**.  
  
     Na ilustracji przedstawiono **definicji wglądu** Windows metody o nazwie `Print()`:  
  
     ![Podgląd okna](../ide/media/peekwindow.png "PeekWindow")  
  
     Okno definicji pojawia się poniżej `printer.Print("Hello World!")` wiersza w oryginalnym pliku. Okno nie ukrywa żadnego kodu w pliku oryginalnym. Wiersze, które należy wykonać `printer.Print("Hello World!")` są wyświetlane w oknie definicji.  
  
2.  Możesz przenieść kursor w inne miejsce w oknie definicji kodu. Możesz nadal można poruszanie się w oryginalnej okna kodu.  
  
3.  Można skopiować ciąg z okna definicji i wkleić go w kodzie oryginalnym. Możesz również przeciągać i upuszczać ciąg z okna definicji do oryginalnego kodu bez usuwania go z okna definicji.  
  
4.  Możesz zamknąć okno definicji, wybierając **Esc** klucza lub **zamknąć** przycisk na karcie okna definicji.  
  
#### <a name="to-open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Aby otworzyć okno Zobacz definicję z poziomu okna Zobacz definicję    
-   Jeśli masz już **definicji wglądu** okna otwarte, należy wywołać **definicji wglądu** ponownie na kodzie w danym przedziale. Otwiera się inne okno definicji. Zestaw łączy do stron nadrzędnych obok karty w oknie definicji, służący do nawigacji między oknami definicji. Etykietka narzędzia na każdej kropce ukazuje nazwę pliku i ścieżkę pliku definicji, którą ta kropka reprezentuje.  
  
     ![Okno podglądu okna podglądu](../ide/media/peekwithinpeek.png "PeekWithinPeek")  
  
#### <a name="to-use-peek-definition-with-multiple-results"></a>Aby użyć funkcji Zobacz definicję z wieloma wynikami    
-   Jeśli używasz **definicji wglądu** na kod, który ma więcej niż jednej definicji (na przykład klasy częściowe), zostanie wyświetlona lista wyników, z prawej strony widoku definicji kodu. Możesz wybrać dowolny wynik na liście, aby wyświetlić jego definicję.  
  
     ![W oknie Peek wiele wyników](../ide/media/peekmultiple.png "PeekMultiple")  
  
#### <a name="to-edit-inside-the-peek-definition-window"></a>Aby edytować wewnątrz okna Zobacz definicję    
-   Po rozpoczęciu edycji wewnątrz **definicji wglądu** okna, pliku, który modyfikacji automatycznie otwiera się jako osobnej karcie w edytorze kodu i odzwierciedla zmiany, które zostały wprowadzone. Możesz dokonać, Cofnij i Zapisz zmiany w **definicji wglądu** okna i na karcie nadal odzwierciedlenia tych zmian. Nawet jeśli zamkniesz **definicji wglądu** okna bez zapisywania zmian, można wprowadzić, Cofnij i zapisać zmiany na karcie Pobieranie dokładnie którym została pozostawiona w **definicji wglądu** okna.  
  
     ![Edytowanie okna podglądu](../ide/media/peekedit.png "PeekEdit")  
  
#### <a name="to-change-options-for-peek-definition"></a>Aby zmienić opcje dla definicji wglądu  
1. Przejdź do **narzędzia**, **opcje**, **Edytor tekstu**, **ogólne**.  

2. Wybierz opcję **Otwórz definicję w widoku peek**.  

3. Kliknij przycisk **OK** zamknąć **opcje** okno dialogowe.  

     ![Ustawienie opcji definicji wglądu kliknięcia myszą](../ide/media/editor_options_peek_view.png)  

#### <a name="to-use-keyboard-shortcuts-for-peek-definition"></a>Aby używać skrótów klawiaturowych dla funkcji Zobacz definicję    
-   Można użyć tych skrótów klawiaturowych z **definicji wglądu** okno:  
  
    |Funkcja|Skrót klawiaturowy|  
    |-------------------|:-----------------------:|  
    |Otwórz okno definicji|Alt+F12|  
    |Zamknij okno definicji|Esc|  
    |Promuj okno definicji do karty zwykłego dokumentu|Shift+Alt+Home|  
    |Przechodzenie między oknami definicji|Ctrl+Alt+- i Ctrl+Alt+=|  
    |Przechodzenie między wieloma wynikami|F8 i Shift + F8|  
    |Przełączanie się między oknem edytora kodu i oknem definicji|Shift + Esc|  
  
    > [!NOTE]
    >  Umożliwia także te same skróty klawiaturowe do edycji kodu w **definicji wglądu** okno używany w innym miejscu w programie Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
[Nawigowanie po kodzie](../ide/navigating-code.md)  
[Przejdź do definicji i definicji wglądu](../ide/go-to-and-peek-definition.md)  
[Wskazówki dotyczące produktywności](../ide/productivity-tips-for-visual-studio.md)