---
title: Debugowanie XAML w Blend | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 8406f07b6f74211b4df873c7eae054e9ab67749c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debug-xaml-in-blend"></a>Debugowanie XAML w Blend
Korzystając z narzędzi dostępnych w [!INCLUDE[blend_first](../debugger/includes/blend_first_md.md)] debugowanie XAML w aplikacji. Podczas kompilowania projektu błędy są wyświetlane w **wyniki** panelu. Kliknij dwukrotnie błędu można znaleźć znacznika związane z błędem. Jeśli potrzebujesz więcej miejsca do pracy można ukryć **wyniki** panelu, naciskając klawisz F12.  
  
## <a name="syntax-errors"></a>Błędy składniowe  
 Błędy składniowe wystąpić, jeśli pliki CodeBehind lub XAML nie wykonuj reguły formatowania języka. Opis błędu może ułatwić zrozumienie sposobu jego usunięcia. Listy określa także nazwę pliku i numer wiersza, w którym występuje błąd. Błędy XAML znajdują się na **znacznika** karcie **wyniki** panelu.  
  
> [!TIP]
>  XAML jest język znaczników opartych na języku XML i zasadami składni XML.  
  
 Niektóre typowe przyczyny są błędy składni języka XAML:  
  
-   Słowo kluczowe została błędnie wpisana lub wielkich liter jest nieprawidłowy.  
  
-   Znaki cudzysłowu brakuje wokół atrybuty lub ciągów tekstowych.  
  
-   XAML element nie ma tagu zamykającego.  
  
-   Istnieje XAML element w lokalizacji, w którym nie jest dozwolone.  
  
 Aby uzyskać więcej informacji o typowych składni języka XAML, zobacz [XAML podstawowa składnia przewodnik](http://go.microsoft.com/fwlink/?LinkId=329942).  
  
 Można również zidentyfikować i rozwiązać błędy składniowe proste kodem, błędy kompilacji i błędów czasu wykonywania w [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)]. Jednak błędy związane z kodem może być łatwiej zidentyfikować i rozwiązać w programie Visual Studio.  
  
### <a name="debugging-sample-xaml-code"></a>Debugowanie kodu XAML próbki  
 Poniższy przykład umożliwia przeprowadzenie proste XAML, sesji debugowania w [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)].  
  
##### <a name="to-create-a-project"></a>Aby utworzyć projekt  
  
1.  W [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)], otwórz **pliku** menu, a następnie kliknij przycisk **nowy projekt**.  
  
     W **nowy projekt** okno dialogowe po lewej stronie zostanie wyświetlona lista typów projektów. Po kliknięciu typu projektu szablony projektów, które są skojarzone z nim występować po prawej stronie.  
  
2.  Na liście typów projektów kliknij **uniwersalnych systemu Windows**.  
  
3.  Na liście szablonów projektu, kliknij przycisk **pusta aplikacja (uniwersalna systemu Windows)**.  
  
4.  W **nazwa** polu tekstowym `DebuggingSample`.  
  
5.  W **lokalizacji** tekstu sprawdź lokalizację projektu.  
  
6.  W **języka** kliknij **Visual C#**, a następnie kliknij przycisk **OK** Aby utworzyć projekt.  
  
7.  Kliknij prawym przyciskiem myszy na powierzchni projektu, a następnie kliknij przycisk **Wyświetl źródło** Aby przełączyć się do **podziału** widoku.  
  
8.  Skopiuj następujący kod, klikając **kopiowania** łącze w prawym górnym rogu kodu.  
  
    ```  
    <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
         <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
    </Grid>  
  
    ```  
  
9. Znajdź wartość domyślna **siatki**i Wklej kod między otwarcia i zamknięcia **siatki** tagów. Po zakończeniu kod powinien wyglądać następująco:  
  
    ```  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
         <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
              <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
         </Grid>  
    </Grid>  
  
    ```  
  
10. Naciśnij klawisze Ctrl + Shift + B, aby skompilować projekt.  
  
 Wyświetlony komunikat o błędzie informujący, że nie można utworzyć projektu, i **wyniki** panelu zawierającego listę błędów, który znajduje się w dolnej części aplikacji.  
  
 ![Debugowanie XAML w Blend for Visual Studio](../debugger/media/blend_debugxaml_xaml.png "blend_debugXAML_XAML")  
  
### <a name="resolving-xaml-errors"></a>Rozwiązywanie błędów XAML  
 W przypadku wykrycia błędów XAML, powierzchni projektowej wyświetla alert, że projekt zawiera nieprawidłowy kod znaczników. Jak rozwiązać błędy, na liście błąd **wyniki** panelu jest aktualizowany. Po rozwiązaniu wszystkich błędów powierzchni projektu jest włączona, a aplikacji jest wyświetlany na powierzchnię projektu.  
  
##### <a name="to-resolve-the-xaml-errors"></a>Aby usunąć błędy XAML  
  
1.  Kliknij dwukrotnie pierwszy błąd na liście. Opis jest "wartość" < "jest nieprawidłowa w atrybucie." Po dwukrotnym kliknięciu błąd odpowiedniej lokalizacji wskaźnik myszy znajduje się w kodzie. `<` Poprzedniego `Button` jest prawidłowy i nie jest atrybutem zgodnie z sugestią podaną w komunikacie o błędzie. Podczas przeglądania w poprzednim wierszu kodu, można zauważyć, że zamykający cudzysłów atrybutu `Top` brakuje. Wpisz znaki cudzysłowu zamykającego. Należy zauważyć, że błąd na liście **wyniki** panelu aktualizacji w celu odzwierciedlenia zmian.  
  
2.  Kliknij dwukrotnie opis "'0' jest nieprawidłowy na początku nazwy." `Margin="0,149,0,0"`wydaje się być poprawnie sformułowany. Jednak należy zauważyć, że kolor kodowanie `Margin` jest niezgodny z innymi wystąpieniami `Margin` w kodzie. Ponieważ poprzednie pary nazwa/wartość brakuje cudzysłowu zamykającego (`VerticalAlignment="Top`), `Margin="` jest do odczytu część wartości atrybutu poprzedniego i 0 jest w trybie odczytu początek pary nazwa/wartość. Wpisz znaki cudzysłowu zamykającego dla `Top`. Lista błędów w **wyniki** panelu aktualizacji w celu odzwierciedlenia zmian.  
  
3.  Kliknij dwukrotnie błąd, "zamykający tag XML"Przycisku"jest niezgodna." Wskaźnik myszy znajduje się pod adresem zamknięcia **siatki** tag (`</Grid>`), sugerujące, że błąd znajduje się wewnątrz `Grid` obiektu. Zwróć uwagę, że druga `Button` obiektu nie ma tagu zamykającego. Po dodaniu zamknięcia `/`, **wyniki** aktualizacji listy panelu. Teraz, gdy te błędy początkowej zostały rozwiązane. zidentyfikowano dwie dodatkowe błędy.  
  
4.  Kliknij dwukrotnie ikonę "elementu członkowskiego"zawartość"nie jest rozpoznawany lub jest niedostępna". `c` w `content` powinny być wielkimi literami. Zastąpić małą "c" wielkimi literami "c".  
  
5.  Kliknij dwukrotnie pozycję "Właściwości"Mame"nie istnieje w przestrzeni nazw"http://schemas.microsoft.com/winfx/2006/xaml"." "M" w "Mame" powinien być "y". Zastąp "M" z "y". Teraz, można przeanalizować pliku XAML, aplikacja pojawia się na powierzchni projektu.  
  
     ![Debugowanie XAML w Blend for Visual Studio](../debugger/media/blend_debugartboard_xaml.png "blend_debugArtboard_XAML")  
  
     Naciśnij klawisze Ctrl + Shift + B, aby skompilować projekt i upewnij się, że nie ma żadnych błędów pozostałych.  
  
## <a name="debugging-in-visual-studio"></a>Debugowanie w Visual Studio  
 Możesz otworzyć [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] projekty w programie Visual Studio aby łatwo debugowania kodu w aplikacji. Aby otworzyć [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] projekt w programie Visual Studio, kliknij prawym przyciskiem myszy projekt w **projekty** panelu, a następnie kliknij przycisk **edytować w programie Visual Studio**. Po zakończeniu sesję debugowania w programie Visual Studio, naciśnij kombinację klawiszy Ctrl + Shift + S, aby zapisać wprowadzone zmiany, a następnie przejdź do [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)]. Pojawi się monit, aby ponownie załadować projekt. Kliknij przycisk **tak, aby wszystkie** kontynuowanie pracy w [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)].  
  
 Aby uzyskać więcej informacji o debugowaniu aplikacji, zobacz [debugowania aplikacji platformy UWP w programie Visual Studio](http://go.microsoft.com/fwlink/?LinkId=329944).  
  
## <a name="getting-help"></a>Uzyskiwanie pomocy  
 Jeśli potrzebujesz więcej pomocy debugowania programu [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] aplikacji, możesz wyszukać [Fora społeczności użytkowników aplikacji platformy uniwersalnej systemu Windows](http://go.microsoft.com/fwlink/?LinkId=280308) dla wpisy dotyczące problemu lub zadać pytanie.