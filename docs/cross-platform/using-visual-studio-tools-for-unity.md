---
title: "Za pomocą narzędzi Visual Studio Tools for Unity | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
caps.latest.revision: "5"
author: conceptdev
ms.author: crdun
manager: crdun
ms.openlocfilehash: 735c95d9eda5cba15b9d75a5abf10d26dd14b0cb
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="using-visual-studio-tools-for-unity"></a>Używanie rozszerzenia Visual Studio Tools for Unity
W tej sekcji omówiono sposób użycia programu Visual Studio Tools dla Unity w integracja i funkcje produktywności i sposobu użycia debuger programu Visual Studio do tworzenia aplikacji platformy Unity.  

## <a name="unity-integration-and-productivity"></a>Integracja platformy Unity i produktywność  
 Visual Studio Tools for Unity integruje się z Edytor platformy Unity ułatwiają zwiększenie produktywności. Te funkcje zwiększenie produktywności automatyzacji typowych zadań skryptów i Przenieś informacji z Unity w programie Visual Studio, dzięki czemu nie trzeba przełączyć go do edytora Unity.  

### <a name="unity-documentation-access"></a>Dostęp do dokumentacji Unity  
 Można uzyskać dostępu do Unity skryptów dokumentacji szybko z programu Visual Studio. Visual Studio Tools for Unity nie znajdzie się w dokumentacji interfejsu API lokalnie, spróbuje go znaleźć w trybie online.  

##### <a name="to-access-unity-documentation"></a>Aby uzyskać dostęp do dokumentacji Unity  

-   W programie Visual Studio, zaznacz lub umieść kursor nad Unity interfejsu API, aby dowiedzieć się o, a następnie naciśnij klawisz **Ctrl + Alt + M, Ctrl + H**  

### <a name="unity-monobehavior-scripting-wizard"></a>Kreator skryptów MonoBehavior Unity  
 W Unity większość skrypty są implementowane przez tworzenia klasy pochodnej z klasy MonoBehavior i zastępowanie niektóre metody. Kreator MonoBehavior szybko utworzyć pusty definicje metod MonoBehavior, który chcesz przeciążenia. Za pomocą tego kreatora, można określić jedną lub kilka metod, które mają być przeciążenia z listy dostępnych metod, wybierz, gdzie zostanie wstawiona do kodu i zdecyduj, czy uwzględnić komentarze na temat korzystania z nich.  

 ![Okno dialogowe Kreator monobehavior. ] (../cross-platform/media/vstu_monobehavior_wizard_full.png "vstu_monobehavior_wizard_full")  

##### <a name="to-create-empty-monobehavior-method-definitions-by-using-the-monobehavior-wizard"></a>Aby utworzyć pusty definicjami metod MonoBehavior za pomocą Kreatora MonoBehavior  

1.  W programie Visual Studio, umieść kursor w którym można metody służące do wstawienia, a następnie naciśnij klawisz **Ctrl + Shift + M** można uruchomić Kreatora MonoBehavior. Lub, jeśli chcesz wstawić nowych metod po klucz, który został już zaimplementowany, można określić, że później; Wystarczy nacisnąć klawisz **Ctrl + Shift + M**.  

2.  Wybierz metody, których można było przeciążyć. W **utworzyć skrypt metody** okna, w obszarze **Wybieranie metody tworzenia**, zaznacz pole wyboru obok nazwy każdego chcesz przeciążyć metodę.  

3.  Upewnij się, że jest wyświetlany w wersja platformy **Framework w wersji** listy rozwijanej jest zgodna z wersją używasz. Jeśli nie jest zgodna, zmień wartość z listy rozwijanej do wersji, która ma być używany.  

4.  Wybierz, w którym zostanie wstawiony metody. Domyślnie te metody są wstawiane na położenie kursora; Jeśli chcesz wstawić je w innej lokalizacji, można wstawić je po dowolnej metody, która jest już zaimplementowana w klasie. Można wybrać jeden z tych lokalizacji, zmień wartość **punkt wstawiania** docelowej do lokalizacji.  

5.  Jeśli Kreator ma generować komentarze dla wybranych metod, Oznacz **Generuj komentarze metody** wyboru. Te komentarze są przeznaczone do pomaga w zrozumieniu, gdy jest wywoływana metoda i jego obowiązki ogólne są.  

6.  Wybierz **OK** przycisk, aby zamknąć kreatora i wstawić metody w kodzie.  

 Kreator MonoBehavior jest szczególnie przydatne podczas nadal zapoznawania się z interfejsu API platformy Unity lub gdy chcesz przeciążyć metodę, których nie masz doświadczenia w obsłudze. Jak staną się bardziej doświadczenia w pracy z interfejsu API platformy Unity, można wybrać Kreatora szybkiego MonoBehavior do szybkiego tworzenia metod, które znasz już.  

#### <a name="quick-monobehavior-scripting-wizard"></a>Szybkie MonoBehavior kreatora skryptów  
 Jeśli już znasz interfejsu API platformy Unity, przeciążonych metod można zaimplementować nawet szybciej za pomocą Kreatora MonoBehavior szybkie. Za pomocą tego kreatora, można określić tylko jedną metodę, która dodaje się bez metody komentarzy w lokalizacji kursora.  

 ![Okno dialogowe Szybkie monobehavior kreatora. ] (../cross-platform/media/vstu_monobehavior_wizard_quick.png "vstu_monobehavior_wizard_quick")  

###### <a name="to-create-an-empty-monobehavior-method-definition-by-using-the-quick-monobehavior-wizard"></a>Aby utworzyć pusty definicję — metoda MonoBehavior za pomocą Kreatora szybkiego MonoBehavior  

1.  W programie Visual Studio, umieść kursor w miejscu metody do wstawienia, a następnie naciśnij klawisz **Ctrl + Shift + Q** można uruchomić Kreatora MonoBehavior szybkie. W odróżnieniu od innych MonoBehavior kreatora należy umieścić kursor celowo podczas korzystania z tego kreatora, ponieważ nowa metoda jest zawsze wstawiany istnieje.  

2.  Upewnij się, że jest wyświetlany w górnym prawym rogu wersja platformy **Utwórz metody skryptu** okna jest zgodna z wersją używasz. Jeśli nie jest zgodna, zmień wartość z listy rozwijanej do wersji, która ma być używany.  

3.  Znajdź można było przeciążyć metodę. W oknie Utwórz skrypt metody wpisz nazwę metody w polu tekstowym. Zostanie wyświetlona lista metod, których nazwy są zgodne zostały wprowadzone.  

4.  Wybierz metodę, którą chcesz przeciążenia. Gdy metoda ma jest wyświetlana na liście, wybierz ją przy użyciu klawiszy myszy lub strzałki, naciśnij klawisz **Enter**. Jeśli tak jest jedyną metodą na liście, możesz po prostu nacisnąć **Enter**. Metody są wstawiane do kodu.  

### <a name="unity-project-explorer"></a>Eksplorator projektów Unity  
 Eksplorator projektów Unity umożliwia Przejdź projektu środowiska Unity w programie Visual Studio.  

 ![Okno Eksploratora projektu platformy Unity. ] (../cross-platform/media/vstu_unity_project_explorer.png "vstu_unity_project_explorer")  

##### <a name="to-view-the-unity-project-explorer"></a>Aby wyświetlić Eksplorator projektów Unity  

-   W programie Visual Studio, w menu głównym wybierz **widoku**, **Eksplorator projektów Unity**. Klawiatury: **Alt + Shift + E**  

     ![Wyświetl okno Eksploratora projektu platformy Unity. ] (../cross-platform/media/vstu_view_unity_project_explorer.png "vstu_view_unity_project_explorer")  

 Eksplorator projektów Unity są wyświetlane wszystkie katalogów i plików projektów środowiska Unity w taki sam sposób, który wykonuje Edytor platformy Unity — to jest inny niż Nawigacja skrypty unity z Eksploratora rozwiązań, który zawiera tylko skrypt pliki i wyświetla je jako projekty i rozwiązania wygenerowanych przez program Visual Studio Tools for Unity organizuje je. Szczególnie w przypadku dużych projektów często jest łatwiejszy do znalezienia skryptu, który chcesz zmodyfikować za pomocą Eksploratora projektu Unity; on również można łatwo zmodyfikować innych typów plików — na przykład pliki konfiguracji na podstawie tekstu — w programie Visual studio bez dodawania ich do jednego z projektów w rozwiązaniu Visual Studio.  

### <a name="unity-error-list"></a>Lista błędów Unity  
 Komunikaty z konsoli platformy Unity w programie Visual Studio można wyświetlać, gdy jest ona dołączona do wystąpienia Unity. W tym błędy i ostrzeżenia z Unity. Komunikaty są wyświetlane w programie Visual Studio **listy błędów** okna; błąd komunikaty z Unity są wyświetlane na **błędy** karcie komunikaty ostrzegawcze w **ostrzeżenia** karcie i inne komunikaty — na przykład wiadomości wysyłane przy użyciu interfejsu API platformy Unity Debug.Log — są wyświetlane na **wiadomości** kartę.  

 Aby wyświetlić komunikaty, Unity projektu musi być [debugowania projektu przy użyciu odtwarzacza Unity](#debugging-your-project-in-a-unity-player) do obsługi debugowania skryptu i do zaimportowania programu Visual Studio Tools dla pakietu Unity, które jest odpowiednie dla używanej wersji programu Visual Studio i Visual Studio musi być [łączenie Visual Studio, aby Unity](#connecting-visual-studio-to-unity).  

 Jeśli nie chcesz wyświetlić błędy, ostrzeżenia i komunikaty z Unity w programie Visual Studio **listy błędów** okna, można je wyłączyć w menu konfiguracji.  

### <a name="keyboard-shortcuts"></a>Skróty klawiaturowe  
 Można szybki dostęp do narzędzi Unity dla funkcji programu Visual Studio przy użyciu ich skrótów klawiaturowych. Poniżej przedstawiono podsumowanie skrótów, które są dostępne.  

|Polecenie|Skrót|Nazwa polecenia skrótów|  
|-------------|--------------|---------------------------|  
|Otwórz kreatora MonoBehavior|**Ctrl + Shift + M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|  
|Otwórz Kreatora szybkich MonoBehavior|**Ctrl + Shift + Q**|**EditorContextMenus.CodeWindow.QuickMonoBehaviours**|  
|Otwórz Eksplorator projektów Unity|**Alt + Shift + E**|**View.UnityProjectExplorer**|  
|Dostęp do dokumentacji Unity|**Ctrl + Alt + M, Ctrl + H**|**Help.UnityAPIReference**|  
|Dołączanie debugera Unity (player lub edytorze)|***Brak wartości domyślnej***|**Debug.AttachUnityDebugger**|  
  
 Kombinacje klawiszy skrótu można zmienić, jeśli nie chcesz, aby domyślnie. Informacje o tym, jak je zmienić, zobacz [zidentyfikowanie i dostosowywanie skrótów klawiaturowych w Visual Studio](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="unity-debugging"></a>Debugowanie Unity  
 Visual Studio Tools for Unity umożliwia debugowanie zarówno edytora i skrypty gier dla projektu Unity za pomocą zaawansowanych debuger programu Visual Studio.  

###  <a name="connecting-visual-studio-to-unity"></a>Łączenie programu Visual Studio z Unity  
 Visual Studio Tools for Unity komunikuje się z Unity za pomocą połączenia protokołu UDP. Oznacza to, czy masz połączenie z wystąpieniem Unity uruchomionej na komputerze lokalnym lub w dowolnym miejscu w sieci w taki sam sposób. Można podłączyć do dowolnych wystąpień Unity widoczny w sieci za pomocą **wybierz wystąpienie Unity** okna dialogowego.  

##### <a name="to-open-the-select-unity-instance-dialog"></a>Aby otworzyć okno dialogowe Wybór wystąpienia Unity  

-   W programie Visual Studio, w menu głównym wybierz **debugowania**, **dołączyć debuger Unity**.  

     ![Dołącz debuger Unity. ] (../cross-platform/media/vstu_debugging_attach_unity_debugger.png "vstu_debugging_attach_unity_debugger")  

-   *Lub*, w programie Visual Studio na pasku stanu, wybierz ikonę plug w prawym dolnym rogu programu Visual Studio.  

     ![Ta ikona wskazuje, że pomocą rozszerzenia VSTU jest podłączony do Unity. ] (../cross-platform/media/vstu_connection_connected.png "vstu_connection_connected")  

> [!TIP]
>  Jeśli ikona plug zawiera znacznik wyboru, zostało już nawiązane do wystąpienia Unity.  

 **Wybierz wystąpienie Unity** okno dialogowe wyświetla niektóre informacje na temat każdego wystąpienia Unity, które możesz nawiązać połączenie.  

 ![Wybierz wystąpienie Unity, aby nawiązać połączenie. ] (../cross-platform/media/vstu_connection_to_unity.png "vstu_connection_to_unity")  

 **Projekt**  
 Nazwa projektu Unity, który działa w tym wystąpieniu Unity.  

 **Maszyny**  
 Nazwa komputera lub urządzenia, które to wystąpienie Unity.  

 **Typ**  
 **Edytor** Jeśli to wystąpienie Unity jest uruchomiony jako część programu Edytor platformy Unity; **Player** Jeśli to wystąpienie Unity jest autonomiczna player.  

 **Port**  
 Numer portu gniazda UDP, że to wystąpienie Unity komunikuje się za pośrednictwem.  

> [!IMPORTANT]
>  Ponieważ Visual Studio Tools for Unity i wystąpienia Unity komunikują się za pośrednictwem protokołu UDP gniazda sieci, Zapora może poprosić o nim. W takim przypadku musisz autoryzować połączenia, dzięki czemu pomocą rozszerzenia VSTU i Unity komunikują się.  

###  <a name="debugging-your-project-in-a-unity-player"></a>Debugowanie projektu przy użyciu odtwarzacza Unity  
 Możesz połączyć Visual Studio Tools for Unity bezpośrednio do aplikacji platformy Unity uruchomiony w autonomicznej player, gdy nie używasz Edytor platformy Unity lub do debugowania problemów, które są specyficzne dla tej platformy.  

##### <a name="to-enable-script-debugging-in-a-unity-player"></a>Aby włączyć debugowanie skryptów w Unity player  

-   Upewnij się, że tworzysz kompilacji programowanie z włączonym debugowaniem skryptu. W ustawieniach kompilacji projektu Unity oznaczyć **programowanie kompilacji** i **debugowanie skryptu** pola wyboru.  

 ![Konfigurowanie ustawień kompilacji platformy Unity do debugowania. ] (../cross-platform/media/vstu_debugging_build_settings.png "vstu_debugging_build_settings")  

 Ponadto do debugowania aplikacji platformy Unity, uruchomionych w **Unity Web Player**, należy również skonfigurować go do używania **kanału wersji programowanie**.  

##### <a name="to-configure-the-development-release-channel-in-unity-web-player"></a>Aby skonfigurować kanał wersji Programowanie w Unity Player sieci Web  

-   W sieci Web platformy Unity Player w menu kontekstowym, wybierz **kanału wersji** i upewnij się, że **programowanie** opcja jest włączona.  

    > [!IMPORTANT]
    >  W wersji Unity 4.2 i nowszych **kanału wersji** elementu menu kontekstowego jest dostępna tylko w menu kontekstowym Player sieci Web podczas **Alt** naciśnięcia klawisza jako menu kontekstowe jest otwarte. Odtwarzacz sieci Web jest uruchomiony w systemie Mac OS X, naciśnij klawisz **opcji** zamiast tego klucza.  

 Ponadto upewnij się, że nawiązano połączenie z wystąpieniem Unity, które chcesz debugować. Aby uzyskać informacje o tym, jak to zrobić, zobacz [łączenie Visual Studio, aby Unity](#connecting-visual-studio-to-unity) sekcji.  

### <a name="debugging-a-dll-in-your-unity-project"></a>Debugowanie bibliotek DLL w projekcie platformy Unity  
 Wielu deweloperów Unity pisania kodu składniki jako zewnętrznej biblioteki dll, dzięki czemu można łatwo udostępniać funkcje, które opracowują one z innymi projektami. Visual Studio Tools for Unity ułatwia debugowania kodu w te biblioteki dll z innego kodu w projekcie platformy Unity.  

> [!NOTE]
>  W tej chwili Visual Studio Tools for Unity obsługuje tylko zarządzane biblioteki dll. Nie obsługuje debugowania kodu natywnej biblioteki dll, takich jak w języku C++.  

 Należy pamiętać, że scenariusz opisany w tym miejscu założono, że kod źródłowy, oznacza to, tworzenie lub ponownie przy użyciu kodu firmy lub masz źródło kodu w bibliotece innych firm i zaplanować wdrożenie go w projekcie platformy Unity jako biblioteki DLL. W tym scenariuszu nie opisano debugowania bibliotekę DLL, dla którego nie ma kodu źródłowego.  

##### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Debugowanie zarządzanego projektu biblioteki DLL używane w projekcie platformy Unity  

1.  Dodaj istniejącego projektu biblioteki DLL do rozwiązania Visual Studio, generowane przez Visual Studio Tools for Unity. Rzadziej może być uruchamianie nowego projektu zarządzanej biblioteki DLL zawiera składniki kodu w projekcie platformy Unity; Jeśli tak jest, możesz zamiast tego dodać nowy projekt zarządzanej biblioteki DLL do rozwiązania Visual Studio. Aby uzyskać więcej informacji na temat dodawania nowego lub istniejącego projektu do rozwiązania, zobacz [porady: dodawanie projektów do rozwiązania](https://msdn.microsoft.com/en-us/library/vstudio/ff460187.aspx).  

     ![Dodaj istniejącego projektu biblioteki DLL do rozwiązania. ] (../cross-platform/media/vstu_debugging_dll_add_existing.png "vstu_debugging_dll_add_existing")  

     W obu przypadkach Visual Studio Tools for Unity przechowuje odwołanie do projektu, nawet jeśli ma można ponownie wygenerować plików projektu i rozwiązania ponownie, wystarczy tylko jeden raz wykonaj następujące kroki.  

2.  Odwołanie do poprawnego profilu framework Unity projektu biblioteki DLL. W programie Visual Studio, we właściwościach projektu biblioteki DLL, ustaw **platformy docelowej** właściwości używasz wersji platformy Unity. Jest to Unity podstawowej biblioteki klas odpowiadający zgodności interfejsu API, że elementy docelowe projektu, takie jak Pełna Unity, micro lub sieci web podstawowej biblioteki klas. Zapobiega to wywołanie metody framework, który istnieje w innych platform lub poziomy zgodności, ale które nie może istnieć w używanej wersji platformy Unity biblioteki DLL.  

     ![Ustaw DLL platformy docelowej Framework Unity. ] (../cross-platform/media/vstu_debugging_dll_target_framework.png "vstu_debugging_dll_target_framework")  

3.  Skopiuj bibliotekę DLL do folderu zasobów projektu platformy Unity. W Unity zasoby są pliki, które są umieszczone i wdrożone razem z aplikacji platformy Unity, tak aby mogły być załadowany w czasie wykonywania. Ponieważ biblioteki DLL są połączone w czasie wykonywania, biblioteki DLL muszą być wdrożone jako zasoby. Edytor platformy Unity wdrażanych jako zasób, wymaga bibliotek DLL, które należy umieścić w folderze zasobów w projekcie platformy Unity. Istnieją dwa sposoby, możesz to zrobić:  

    -   Zmodyfikuj ustawienia kompilacji projektu biblioteki DLL, które zostaną dołączone po wbudowanego zadania, które kopiuje plików wyjściowych biblioteki DLL i PDB z jego folderu wyjściowego w celu **zasoby** folderu projektu platformy Unity.  

    -   Zmodyfikuj ustawienia kompilacji projektu biblioteki DLL w celu jego folderu wyjściowego, należy ustawić **zasoby** folderu projektu platformy Unity. Pliku DLL i PDB zostaną umieszczone w **zasoby** folderu.  

     PDB, pliki są wymagane do debugowania, ponieważ zawiera symbole debugowania DLL i mapowanie kod biblioteki DLL do postaci kodu źródłowego. Visual Studio Tools for Unity użyje informacji z biblioteki DLL i PDB do tworzenia biblioteki DLL. Plik MDB, który jest używany przez aparat skryptów Unity format symboli debugowania.  

4.  Debugowanie kodu. Można teraz debugowania kodu źródłowego DLL wraz z kodu źródłowego projektu Unity i wszystkie funkcje, które służą do, takich jak punkty przerwania debugowania i krokowe wykonywanie kodu.
