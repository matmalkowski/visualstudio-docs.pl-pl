---
title: "Dostosowywanie układów okien w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.windows
- vs.environment
helpviewer_keywords:
- windows [Visual Studio], managing
- custom window configurations
- layout [Visual Studio], window management
- document windows [Visual Studio]
- interface modes
- AutoHide windows
- MDI, window interface modes
- multiple monitors
- Tabbed Document mode
- debug mode
- custom layouts
ms.assetid: 7517ff13-76de-4ecf-9c1b-eb9b7ff4d718
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 596e9e6dfa5f7fb464430636f696e37748ccb8eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="customize-window-layouts-in-visual-studio"></a>Dostosowywanie układów okien w programie Visual Studio
W programie Visual Studio można dostosować położenie, rozmiar i zachowania systemu windows, aby utworzyć układów okien, które najlepiej dla różnych Projektowanie przepływów pracy. Podczas dostosowywania układ IDE pamięta. Na przykład możesz zmienić lokalizację dokowania **Eksploratora rozwiązań** , a następnie zamknij program Visual Studio, przy następnym uruchomieniu, nawet jeśli pracujesz na innym komputerze, **Eksploratora rozwiązań** będzie zadokowane w tej samej lokalizacji. Można także nazwę niestandardowego układu i zapisz go, a następnie przełączać się między układów za pomocą jednego polecenia. Na przykład można utworzyć układ do edycji i drugi dla debugowania i przełączać się między nimi przy użyciu **okno &#124; Zastosuj układ okna** polecenia menu.  

## <a name="kinds-of-windows"></a>Rodzaje okien  

### <a name="tool-and-document-windows"></a>Narzędzia i zarządzania dokumentami systemu windows  
 IDE ma dwa typy podstawowe okna, *narzędzia systemu windows* i *dokumentu windows*. Narzędzia systemu windows obejmują Eksploratorze rozwiązań, Eksploratora serwera, okno danych wyjściowych, listę błędów, projektantów, debugera systemu windows i itd. Okna dokumentów zawierają pliki kodu źródłowego, pliki tekstowe dowolnego, plików konfiguracji i tak dalej. Okna narzędzi można zmienić rozmiar i przeciągnąć przez ich pasek tytułu. Okna dokumentów można przeciągnąć przez ich kartę. Kliknij prawym przyciskiem myszy na pasku karty lub tytułu Ustaw inne opcje w oknie.  

 **Okna** menu zawiera opcje dokowaniu, zmiennoprzecinkowych i ukrywanie okien w środowisku IDE. Kliknij prawym przyciskiem myszy pasek okna tab lub tytuł, aby wyświetlić dodatkowe opcje dla tego określonego okna. Jednocześnie można wyświetlić więcej niż jedno wystąpienie niektórych okien narzędzi. Na przykład można wyświetlić więcej niż jedno okno przeglądarki sieci web i można utworzyć dodatkowe wystąpienia niektórych okien narzędzi, wybierając **nowe okno** na **okna** menu.  

### <a name="preview-tab-document-windows"></a>Karta Podgląd (dokument z systemem windows)  
 Na karcie podglądu można wyświetlić pliki w edytorze bez ich otwierania. Pliki można wyświetlić, wybierając je w **Eksploratora rozwiązań**, podczas debugowania w kroku plikami z przejdź do definicji oraz w przypadku przeglądania wyników wyszukiwania. Podgląd plików są wyświetlane na karcie po prawej stronie dobrze kartę dokumentu. Plik można otworzyć do edycji, jeśli ją zmodyfikować, lub wybierz **Otwórz**.  

### <a name="tab-groups"></a>Grupy kart  
 Karta grup rozszerzyć możliwości zarządzania ograniczone roboczym podczas pracy z co najmniej dwa otwarte dokumenty w środowisku IDE. Wiele okien dokumentów i okien narzędzi można organizować w pionowych lub poziomych grupy kart i losowa dokumentów z jednej grupy kartę do innego.  

### <a name="split-windows"></a>Podzielone okna  
 Jeżeli konieczne wyświetlenie lub Edycja dwóch lokalizacjach jednocześnie w dokumencie, można podzielić systemu windows. Aby podzielić dokument na dwie sekcje niezależnie przewijania, kliknij przycisk **podziału** na **okna** menu. Kliknij przycisk **Usuń podział** na **okna** menu, aby przywrócić jednego widoku.  

### <a name="toolbars"></a>Paski narzędzi  
 Paski narzędzi można uporządkować przeciągając lub za pomocą **Dostosuj** okno dialogowe. Aby uzyskać więcej informacji na temat pozycji i dostosowywać paski narzędzi, zobacz [porady: Dostosowywanie menu i pasków narzędzi](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).  

## <a name="arrange-and-dock-windows"></a>Aranżowanie i dokowanie okien  
 Zarówno dokumentów systemu windows i okien narzędzi mogą być *zadokowanych*, dzięki czemu ma położenie i rozmiar ramki okna IDE lub zmiennoprzecinkową jako osobne okno niezależne od IDE. Narzędzia systemu windows może być dowolnym zadokowany wewnątrz ramki IDE; Niektóre narzędzia windows może być zadokowany jako okno systemu windows w ramce edytora. Okna dokumentów może być zadokowany w ramce edytora i może zostać unieruchomiony w bieżącym położeniu w kolejności tabulacji. Dokowany wiele okien do float razem w "raft", za pośrednictwem lub na zewnątrz środowiska IDE. Narzędzia systemu windows można także ukryte lub zminimalizowane.  

 Można rozmieścić systemu windows w następujący sposób:  

-   Również przypiąć okna dokumentów do lewej strony karty.  

-   Karta doku windows ramkę do edycji.  

-   Dokowanie okien narzędzi krawędzią elementu frame w IDE.  

-   Float dokumentu lub narzędzia systemu windows za pośrednictwem lub poza IDE.  

-   Ukrywanie okien narzędzi wzdłuż krawędzi IDE.  

-   Wyświetlanie systemu windows na różnych monitorów.  

-   Położenie okna resetowania układ domyślny lub zapisanego niestandardowego układu.  

 Narzędzia i zarządzania dokumentami systemu windows można uporządkować przeciągając przy użyciu poleceń w **okna** menu i klikając prawym przyciskiem myszy pasek tytułu okna, aby być ułożone elementy.  

> [!NOTE]
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  

### <a name="dock-windows"></a>Dokowanie okien  
 Gdy kliknij i przeciągnij pasek tytułu okna narzędzia lub karcie okna dokumentu, pojawi się dokowania. Podczas operacji przeciągania gdy wskaźnik myszy zostanie umieszczony na jednym strzałki romb, zacienionym obszarze pojawi się pokazujący, gdzie zadokowane okno Jeśli teraz zwolnij przycisk myszy.  

 Aby przenieść okna dokującego bez przyciągania go w miejscu, wybierz klawisz Ctrl podczas przeciągania okna.  

 Aby przywrócić jego ostatniej pozycji okna narzędzia lub okna dokumentu, naciśnij klawisz **CTRL** podczas dwukrotnym kliknięciu pasek tytułu lub karcie okna.  

 Na poniższej ilustracji przedstawiono dokowania dla okna dokumentów, które mogą zostać zadokowane tylko w obrębie ramkę do edycji:  

 ![Dokument dokowania okna](../ide/media/documentwindowguidediamonds.png "Documentwindowguidediamonds")  

 Narzędzia systemu windows można podłączony obok ramkę w IDE lub w ramach ramkę do edycji. Dokowania pojawia się podczas przeciągania okna narzędzia do innej lokalizacji, aby ułatwić łatwo ponownie dock okna.  

 Dokowania dla narzędzi systemu windows  

 ![Narzędzie romby okna](../ide/media/vs10guidediamond.png "VS10GuideDiamond")  

 Na poniższej ilustracji przedstawiono jest zadokowany w nowej lokalizacji, która jest wyświetlana niebieski zacienionym obszarze Eksploratora rozwiązań:  

 ![Dokowanie Eksploratora rozwiązań w nowe położenie](../ide/media/vs2015_dock_diamond.png "VS2017_Dock_diamond")  

### <a name="close-and-auto-hide-tool-windows"></a>Zamknij i automatyczne ukrywanie okna narzędzi  
 Możesz zamknąć okno narzędzia, klikając przycisk X w prawym górnym rogu paska tytułu; Aby ponownie otworzyć okno, użyj polecenia jego klawiatury skrótów lub menu. Narzędzia systemu windows obsługuje funkcji o nazwie automatyczne ukrywanie, co powoduje, że okno, aby slajd przeszkadza korzystając z innego okna. Gdy okno jest ukrywane automatycznie, jego nazwa jest wyświetlana na karcie na brzegu IDE. Aby ponownie użyć okna, tak aby slajdów okno z powrotem do widoku punktu do karty.  

 ![Ukryj automatycznie](../ide/media/vs2015_auto_hide.png "vs2017_auto_hide")  

> [!NOTE]
>  Pozwala określić, czy automatyczne ukrywanie działa na narzędzia windows indywidualnie lub jako zadokowanych grupy zaznacz lub wyczyść **automatyczne ukrywanie przycisku dotyczy tylko systemu windows narzędzie active** w **opcje** okno dialogowe. Aby uzyskać więcej informacji, zobacz [ogólne, środowisko, opcje — Okno dialogowe](../ide/reference/general-environment-options-dialog-box.md).  

> [!NOTE]
>  Okna narzędzi, których automatyczne ukrywanie włączone może tymczasowo slajd w widoku, gdy okno ma fokus. W celu ukrycia okna ponownie, wybierz element poza bieżącego okna. Gdy okno utraci fokus, slajdów go ponownie z widoku.  

### <a name="specifying-a-second-monitor"></a>Określanie drugim monitorze  
 Jeśli drugi monitor i system operacyjny obsługuje tę funkcję, można wybrać, który monitor wyświetla okno. Można nawet pogrupować wiele okien w "kopie robocze" na innych monitorach.  

> [!TIP]
>  Możesz utworzyć wiele wystąpień **Eksploratora rozwiązań** i przenieść je do innego monitora. Kliknij prawym przyciskiem myszy okna i wybierz polecenie **nowy widok Eksploratora rozwiązania**. Wszystkie windows można wrócić do pierwotnego monitora, klikając dwukrotnie podczas wybierania klawisz Ctrl.  

### <a name="reset-name-and-switch-between-window-layouts"></a>Resetuj, nazwa i przełączać się między układów okien  
 Możesz powrócić IDE do oryginalnego układ okna kolekcji ustawień za pomocą **zresetować układ okna** polecenia. Po uruchomieniu tego polecenia są wykonywane następujące akcje:  

-   Wszystkie windows są przenoszone do ich domyślnych pozycji.  

-   Systemu Windows, które są zamknięte w domyślny układ okna są zamknięte.  

-   Systemu Windows, które są otwarte w domyślny układ okna są otwarte.  

### <a name="create-and-save-custom-layouts"></a>Tworzenie i zapisywanie układy niestandardowe  
 Program Visual Studio umożliwia zapisywanie maksymalnie 10 niestandardowych układów okien i szybkiego przełączania się między nimi. Poniższe kroki przedstawiają sposób tworzenia, zapisywania, wywołania i zarządzanie układy niestandardowe, które korzystają z wieloma monitorami z oba okna narzędzia zadokowane i przestawne.  

 Najpierw utwórz test rozwiązania, które zawiera dwa projekty, każde z nich inny układ optymalne.  

##### <a name="create-a-ui-project-and-customize-the-layout"></a>Utwórz projekt interfejsu użytkownika i dostosowanie układu  

1.  W **nowy projekt** okna dialogowego, Utwórz Visual C# pulpitu aplikacji WPF i Wywołaj jego dowolne. Podawać, że jest to projekt gdy firma Microsoft będzie działać w interfejsie użytkownika, chcemy, aby zmaksymalizować obszar okna projektanta i Przenieś innych okien narzędzi do końca.  

2.  Jeśli masz wiele monitorów ściągnięcia **Eksploratora rozwiązań** okna i **właściwości** okna za pośrednictwem drugiego monitora. W systemie jednego monitora należy zamknąć wszystkie okna z wyjątkiem projektanta.  

3.  Naciśnij klawisz **Ctrl + Alt + X** do wyświetlenia przybornika. Jeśli okno jest zadokowany, przeciągnij je tak, że jest ona wyświetlana innym miejscu, gdzie chcesz umieścić go na monitorować.  

4.  Naciśnij klawisz F5, aby umieścić Visual Studio w tryb debugowania. Dostosuj położenie samochodów, stos wywołań i dane wyjściowe debugowania systemu windows w żądany sposób. Układ, który zamierzasz utworzyć dotyczą zarówno w trybie edycji i tryb debugowania.  

5.  W menu głównym wybierz, kiedy są układów zarówno tryb debugowania i w trybie edycji, sposobu ich **okna > Zapisywanie układu okna**. Wywołaj ten układ "Designer".  

     Należy pamiętać, nowy układ jest przypisany dalej skrótu klawiaturowego z listy zastrzeżone Ctrl + Alt + 1... 0.  

##### <a name="create-a-database-project-and-layout"></a>Utwórz projekt bazy danych i układu  

1.  Dodaj nową **bazy danych programu SQL Server** projektu do rozwiązania.  

2.  Kliknij prawym przyciskiem myszy nowy projekt w Eksploratorze rozwiązań i wybierz polecenie **widok w Eksploratorze obiektów**. Spowoduje to wyświetlenie **Eksplorator obiektów SQL Server** okna, co umożliwia dostęp do tabel, widoków i innych obiektów w bazie danych. Można to kno lub pozostaw zadokowane. Dostosuj sposób okna narzędzia. Dla wzrostu dodany można dodać istniejącej bazy danych, ale nie jest konieczne w ramach tego przewodnika.  

3.  W przypadku układu jaki sposób, w menu głównym wybierz **okna > Zapisywanie układu okna**. Wywołaj ten układ "Projekt bazy danych". (Firma Microsoft nie będzie odblokowane z układem tryb debugowania dla tego projektu.)  

##### <a name="switch-between-the-layouts"></a>Przełączanie między układów  

1.  Aby przełączyć między układów, skróty klawiaturowe, lub z poziomu menu głównego wybierz **okna > Zastosuj układ okna**.  

     ![Zastosuj menu Układ okna](../ide/media/vs2015_applywindowlayout.png "VS2017_ApplyWindowLayout")  

     Po zastosowaniu układ interfejsu użytkownika, należy zwrócić uwagę, jak zachować układ zarówno w trybie edycji, jak i w trybie debugowania.  

     Jeśli masz w domu konfigurację monitora multi w pracy i jeden monitor komputera przenośnego, można utworzyć układów, które są zoptymalizowane pod kątem każdej maszyny.  

     Uwaga: Układ monitor wielu w przypadku zastosowania w systemie pojedynczej monitora, zmiennoprzecinkowych systemu windows, które można umieścić na drugim monitorze będzie teraz ukryty pod oknie programu Visual Studio. Te okna, można przełączyć do przodu, naciskając klawisze Alt + Tab. Po otwarciu programu Visual Studio z wieloma monitorami, można przywrócić systemu windows na ich określonych pozycji, stosując ponownie układ.  

##### <a name="manage-and-roam-your-layouts"></a>Zarządzanie i są przekazywane układów  

1.  Można usunąć, Zmień nazwę lub zmiana kolejności układu niestandardowego przez wybranie **okna > Zarządzaj układów okien**. Po przeniesieniu układ powiązania klucza jest automatycznie dostosowywany do nowej pozycji na liście. Powiązania nie może być inaczej zmodyfikowane, a więc może przechowywać maksymalnie 10 układów naraz.  

     ![Zarządzanie układów okien](../ide/media/managewindowlayouts.png "ManageWindowLayouts")  

     Mówiące, które klawiatury skrót jest przypisany do wyboru układu, wybierz **okna > Zastosuj układ okna**.  

     Tych układów są automatycznie przekazywane między wersjami programu Visual Studio, a także między wystąpieniami programu Blend na oddzielnych komputerach i z dowolnej wersji Express do innych organizacji Express. Układy nie są jednak przekazywane między Visual Studio i Blend Express.  

## <a name="related-topics"></a>Tematy pokrewne  

[Porady: poruszanie się w środowisku IDE](../ide/how-to-move-around-in-the-visual-studio-ide.md)
