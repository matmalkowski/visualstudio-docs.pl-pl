---
title: "Debugowanie kodu użytkownika przy użyciu tylko mój kod | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 476ff209f96aa5729d20bd9a5a5d12c9e5a5c39a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="specify-whether-to-debug-only-user-code-using-just-my-code-in-visual-studio"></a>Określ, czy w celu debugowania tylko kodu użytkownika przy użyciu tylko mój kod w programie Visual Studio
Można skonfigurować programu Visual Studio automatycznie Przekrocz nad systemu, framework i inne wywołania niezwiązanych z użytkownikiem i zwinąć tych wywołań w oknie stosu wywołań. Funkcja, która włącza lub wyłącza to zachowanie jest nazywany *tylko mój kod*. W tym temacie opisano sposób użycia tylko mój kod w językach C#, Visual Basic, C++ i JavaScript projektów.

W przypadku większości języków programowania tylko mój kod jest domyślnie włączona.
  
##  <a name="BKMK_Enable_or_disable_Just_My_Code"></a>Włącz lub wyłącz opcję tylko mój kod  
 Aby włączyć lub wyłączyć opcję tylko mój kod, wybierz polecenie **Narzędzia > Opcje** menu w programie Visual Studio. W **debugowanie** > **ogólne** węzła, wybierz lub wyczyść **Włącz opcję tylko mój kod**.
  
 ![Włącz opcję tylko mój kod w oknie dialogowym Opcje](../debugger/media/dbg_justmycode_options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
>  **Włącz opcję tylko mój kod** ustawienie jest ustawienie globalne, która jest stosowana do wszystkich projektów programu Visual Studio we wszystkich językach.  
  
###  <a name="BKMK_Override_call_stack_filtering"></a>Pokaż kodu innych użytkowników w widokach stosu wywołań  
 W widokach stos wywołań, taką jak **stos wywołań** i **zadania** systemu windows, tylko mój kod zwija kodu innych użytkowników do ramki adnotacjami etykietą `[External Code]`. Aby wyświetlić zwinięte ramki, wybierz **Pokaż kod zewnętrzny** w menu kontekstowym stosu wywołań wyświetlania.

 ![Pokaż zewnętrznego kodu w oknie stosu wywołań](../debugger/media/dbg_justmycode_showexternalcode.png "DBG_JustMyCode_ShowExternalCode")
  
> [!NOTE]
>  **Pokaż kod zewnętrzny** ustawienia są zapisywane profilera bieżącego użytkownika. Jest stosowana do wszystkich projektów we wszystkich językach, które są otwierane przez użytkownika.
  
##  <a name="BKMK__NET_Framework_Just_My_Code"></a>.NET framework tylko mój kod  
  
###  <a name="BKMK_NET_User_and_non_user_code"></a>Kod użytkownika i niezwiązanych z użytkownikiem  
 Aby odróżnić kod użytkownika z kodu innych użytkowników, tylko mój kod analizuje plików symboli (.pdb) i optymalizacji programu. Debuger uwzględnia kod za kod niezwiązany z użytkownikiem, gdy plik binarny jest zoptymalizowany lub plik PDB nie jest dostępny.
  
 Trzy atrybuty wpłynąć na debuger traktuje jako mój kod:  
  
-   <xref:System.Diagnostics.DebuggerNonUserCodeAttribute>Określa, że debuger czy kod jest stosowana do nie jest mój kod.  
  
-   <xref:System.Diagnostics.DebuggerHiddenAttribute>Ukrywa kod z debugera, nawet wtedy, gdy tylko mój kod jest wyłączona.  
  
-   <xref:System.Diagnostics.DebuggerStepThroughAttribute>Określa, że debuger do wykonania kroków opisanych kod, który zostało zastosowane, zamiast Wkrocz do kodu.  
  
 Inny kod jest uważany za kodu użytkownika.  
  
###  <a name="BKMK_NET_Stepping_behavior"></a>Wykonywanie krok po kroku zachowanie  
 Gdy możesz **Step Into** (skrót klawiaturowy: F11) kodu innych użytkowników, kroki debugera za pośrednictwem kodu do następnej instrukcji użytkownika. Gdy użytkownik **Wyjdź** (klawiatury: Shift + F11), uruchamiania debugera do następnego wiersza kodu użytkownika. Jeśli napotkano żadnego kodu użytkownika, a następnie wykonanie jest kontynuowane do aplikacji wyjścia punkt przerwania zostaje trafiony lub wystąpienia wyjątku.  
  
###  <a name="BKMK_NET_Breakpoint_behavior"></a>Zachowanie punktu przerwania  
 Jeśli włączono opcję tylko mój kod, można określić **Przerwij wszystkie** (klawiatury: Ctrl + Alt + Break) i zatrzymuje wykonywanie w lokalizacji w przypadku, gdy nie jest wykonywany kod użytkownika do wyświetlenia. W takim przypadku zostanie wyświetlone okno nr źródła. Jeśli następnie wybierz polecenie kroku, debuger przejście do następnego wiersza kodu użytkownika.  
  
###  <a name="BKMK_NET_Exception_behavior"></a>Zachowanie wyjątku  
 Jeśli wystąpi nieobsługiwany wyjątek w kodzie niezwiązanych z użytkownikiem, debuger podziałów w wierszu w kodzie użytkownika, na którym został wygenerowany wyjątek.  
  
 Jeśli pierwszej szansy wyjątki są włączone dla wyjątku, wiersz kodu użytkownika zostanie wyróżniona na zielono. Stos wywołań Wyświetla adnotacjami ramki etykietą **[kod zewnętrzny]**.  
  
##  <a name="BKMK_C___Just_My_Code"></a>Tylko mój kod w języku C++  
  
###  <a name="BKMK_CPP_User_and_non_user_code"></a>Kod użytkownika i niezwiązanych z użytkownikiem  
 Tylko mój kod w języku C++ są inne niż .NET Framework i JavaScript tylko mój kod, ponieważ wykonywania krokowego zachowanie jest niezależna od zachowania stosu wywołań.  
  
 **Stosy wywołań**  
  
 Domyślnie debuger uważa za kod niezwiązany z użytkownikiem w systemie windows stosu wywołań tych funkcji:  
  
-   Funkcje pozbawionego włókien źródła informacji w pliku symboli.  
  
-   Funkcje, których pliki symboli wskazują, że plik nie istnieje źródło odpowiadający ramki stosu.  
  
-   Określona w funkcji `*.natjmc` plików `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` folderu.  
  
 **Wykonywanie krok po kroku**  
  
 Domyślnie tylko funkcje określone w `*.natstepfilter` plików `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` folderu są uznawane za kod niezwiązany z użytkownikiem.  
  
 Utwórz swój własny `.natstepfilter` i `.natjmc` dostosować wzmocnienie i wywołać zachowanie okna stosu `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`.  
  
###  <a name="BKMK_CPP_Stepping_behavior"></a>Wykonywanie krok po kroku zachowanie  
 Gdy możesz **Step Into** (skrót klawiaturowy: F11) kod niezwiązany z użytkownikiem z kodu użytkownika, kroki debugera za pośrednictwem kodu do następnego wiersza kodu użytkownika. Gdy użytkownik **Wyjdź** (klawiatury: Shift + F11), uruchamiania debugera do następnego wiersza kodu użytkownika. Jeśli napotkano żadnego kodu użytkownika, a następnie wykonanie jest kontynuowane do aplikacji wyjścia punkt przerwania zostaje trafiony lub wystąpienia wyjątku.  
  
 Jeśli debuger przerwy w kodu innych użytkowników (na przykład, jeśli polecenie Przerwij wszystkie zatrzyma kodu innych użytkowników), kontynuuje wykonywanie krok po kroku w kodzie niezwiązanych z użytkownikiem.  
  
###  <a name="BKMK_CPP_Exception_behavior"></a>Zachowanie wyjątku  
 Debuger trafienia wyjątek, przestaje na wyjątek niezależnie od tego, czy jest w użytkownika ani kodu innych użytkowników. **Nieobsługiwanych przez użytkownika** opcje w **wyjątki** okno dialogowe, są ignorowane.  
  
###  <a name="BKMK_CPP_Customize_stepping_behavior"></a>Dostosowywanie zachowania wykonywania krokowego  
 Można określić funkcji do kroku przez wyświetlanie ich listy jako kodu innych użytkowników w `*.natstepfilter` plików.  
  
-   Aby określić kodu innych użytkowników dla wszystkich użytkowników maszyny programu Visual Studio, Dodaj plik .natstepfilter `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` folderu.  
  
-   Aby określić kodu innych użytkowników dla poszczególnych użytkowników, Dodaj plik .natstepfilter `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` folderu.  
  
 pliki .natstepfilter są plikami xml o następującej składni:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Action>StepAction</Action>  
    </Function>  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Module>ModuleSpec</Module>  
        <Action>StepAction</Action>  
    </Function>  
</StepFilter>  
  
```  
  
|Element|Opis|  
|-------------|-----------------|  
|Funkcja|Wymagany. Określa co najmniej jedną funkcję jako funkcje niezwiązanych z użytkownikiem.|  
|`Name`|Wymagany. ECMA-262 sformatowany wyrażenie regularne określające nazwę pełne działanie do dopasowania. Na przykład:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> Debuger informuje, że wszystkie metody w `MyNS::MyClass` są uważane za kod niezwiązany z użytkownikiem. Dopasowanie jest rozróżniana wielkość liter.|  
|`Module`|Opcjonalny. ECMA-262 sformatowany określić pełną ścieżkę do modułu zawierającego funkcję wyrażenia regularnego. Dopasowanie jest rozróżniana wielkość liter.|  
|`Action`|Wymagany. Jedną z następujących wartości z uwzględnieniem wielkości liter:<br /><br /> -   `NoStepInto`-informuje debugera Przekrocz nad dopasowane funkcji.<br />-   `StepInto`-informuje debugera, aby wkraczać do funkcji dopasowane inne zastępowanie `NoStepInto` dopasowane funkcji.|  
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a>Dostosowywanie zachowania stosu wywołań  
 Można określić moduły, pliki źródłowe i funkcje, które mają być traktowane jako kodu innych użytkowników w stosy wywołań, określając je w `*.natjmc` plików.  
  
-   Aby określić kodu innych użytkowników dla wszystkich użytkowników maszyny programu Visual Studio, Dodaj plik .natjmc `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` folderu.  
  
-   Aby określić kodu innych użytkowników dla poszczególnych użytkowników, Dodaj plik .natjmc `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` folderu.  
  
 pliki .natjmc są plikami xml o następującej składni:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">  
  
  <!-- Modules -->  
  <Module Name="ModuleSpec" />  
  <Module Name="ModuleSpec" Company="CompanyName" />  
  
  <!-- Files -->  
  <File Name="FileSpec"/>  
  
  <!-- Functions -->  
  <Function Name="FunctionSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />  
  
</NonUserCode>  
  
```  
  
 **Atrybuty elementu modułu**  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagany. Pełna ścieżka moduł lub moduły. Można używać symboli wieloznacznych Windows `?` (znak zero lub jeden) i `*` (zero lub więcej znaków). Na przykład<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> Określa, że debuger na traktowanie wszystkich modułów w `\3rdParty\UtilLibs` na dowolnym dysku jako kod zewnętrzny.|  
|`Company`|Opcjonalny. Nazwa firmy, która publikuje moduł, który jest osadzony w pliku wykonywalnego. Ten atrybut służy do odróżniania modułów.|  
  
 **Atrybuty elementu**  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagany. Pełna ścieżka pliku źródłowego lub plików, które mają być traktowane jako kod zewnętrzny. Można używać symboli wieloznacznych Windows `?` i `*` określając ścieżkę.|  
  
 **Atrybuty elementu — funkcja**  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagany. Pełna nazwa funkcji, które mają być traktowane jako kod zewnętrzny.|  
|`Module`|Opcjonalny. Nazwa lub pełną ścieżkę do modułu, która zawiera funkcję. Ten atrybut służy do odróżniania funkcje o takiej samej nazwie.|  
|`ExceptionImplementation`|Jeśli wartość `true`, stos wywołań Wyświetla funkcja, która zgłosiła wyjątek od tej funkcji.|  
  
##  <a name="BKMK_JavaScript_Just_My_Code"></a>Tylko mój kod JavaScript  
  
###  <a name="BKMK_JS_User_and_non_user_code"></a>Kod użytkownika i niezwiązanych z użytkownikiem  
 **Klasyfikacje kodu**  
  
 JavaScript tylko mój kod kontrolki wyświetlanie stosu wykonywanie krok po kroku i wywołanie Kategoryzacja kodu w jednym z tych klasyfikacjach:  
  
|||  
|-|-|  
|**MyCode**|Kod użytkownika, które użytkownika i kontroli.|  
|**LibraryCode**|Kod niezwiązanego z użytkownikiem z biblioteki, często używane i aplikacji polega na działał poprawnie (na przykład WinJS lub jQuery).|  
|**UnrelatedCode**|Kod niezwiązanego z użytkownikiem, które mogą być wykonywane w aplikacji, ale nie jest jej właścicielem i aplikacja bezpośrednio nie polegać na niej działać poprawnie. (Na przykład może to być reklamy zestawu SDK, która wyświetla reklam.) W projekty platformy UWP kodu, który jest ładowany do aplikacji z protokołu HTTP lub HTTPS identyfikatora URI jest traktowana jako UnrelatedCode.|  
  
 Debuger JavaScript klasyfikuje automatycznie te typy kodu:  
  
-   Skrypt, który jest wykonywany przez przekazanie ciąg do dostarczony host `eval` funkcji jest sklasyfikowany jako **MyCode**.  
  
-   Skrypt, który jest wykonywany przez przekazanie ciąg `Function` Konstruktor jest sklasyfikowany jako **LibraryCode**.  
  
-   Skrypt, który jest zawarty w odwołaniu framework, takie jak WinJS lub zestawu Azure SDK zostanie sklasyfikowany jako **LibraryCode**.  
  
-   Skrypt, który jest wykonywany przez przekazanie ciąg `setTimeout`, `setImmediate`, lub `setInterval` funkcji jest sklasyfikowany jako **UnrelatedCode**.  
  
-   `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` Określa inny kod użytkownika i innych użytkowników dla wszystkich projektów JavaScript programu Visual Studio.  
  
 Można zmodyfikować domyślne klasyfikacje i klasyfikować określonych plików i adresy URL przez dodać plik .json o nazwie `mycode.json` do folderu głównego projektu.  
  
 Inny kod zostanie sklasyfikowany jako **MyCode**.  
  
###  <a name="BKMK_JS_Stepping_behavior"></a>Wykonywanie krok po kroku zachowanie  
  
-   Jeśli funkcja nie jest użytkownikiem (**MyCode**) kodu, **Step Into** (skrót klawiaturowy: F11) zachowuje się jak **Step Over** (klawiatury: F10).  
  
-   Jeśli krok rozpoczyna się w innych użytkowników (**LibraryCode** lub **UnrelatedCode**) kodu, a następnie krokowe wykonywanie tymczasowo zachowuje się tak, jakby nie włączono opcję tylko mój kod. Jeśli krok do kodu użytkownika, tylko mój kod wykonywanie krok po kroku zostanie ponownie włączony.  
  
-   Gdy krok z kodu użytkownika spowoduje pozostawienie bieżącego kontekstu wykonywania (na przykład ten krok w ostatnim wierszu program obsługi zdarzeń), debuger zatrzymuje się na dalej wykonanego wiersza kodu użytkownika. Na przykład, jeśli wykonuje wywołanie zwrotne **LibraryCode** kod debuger będzie nadal występować, dopóki nie wykonuje w następnym wierszu kodu użytkownika.
  
-   **Step Out** (klawiatury: Shift + F11) zatrzymuje się w następnym wierszu kodu użytkownika. Jeśli napotkano żadnego kodu użytkownika, a następnie wykonanie jest kontynuowane do aplikacji wyjścia punkt przerwania zostaje trafiony lub wystąpienia wyjątku.  
  
###  <a name="BKMK_JS_Breakpoint_behavior"></a>Zachowanie punktu przerwania  
  
-   Punkty przerwania w kodzie zawsze zostanie uruchomiona niezależnie od klasyfikacji kodu  
  
-   Jeśli `debugger` napotkano — słowo kluczowe w:  
  
    -   **LibraryCode** zawsze dzieli kodu debugera.  
  
    -   **UnrelatedCode** kodu, nie zatrzymać debuger.  
  
###  <a name="BKMK_JS_Exception_behavior"></a>Zachowanie wyjątku  
 Jeśli wystąpi nieobsługiwany wyjątek w:  
  
-   **MyCode** lub **LibraryCode** zawsze dzieli kodu debugera.  
  
-   **UnrelatedCode** kodu i **MyCode** lub **LibraryCode** kod jest w stosie wywołań, podziały debugera.  
  
 Jeśli pierwszej szansy wyjątki są włączone dla wyjątku w oknie dialogowym Wyjątki i wyjątek **LibraryCode** lub **UnrelatedCode** kodu:  
  
-   Jeśli wyjątek jest obsługiwany, Podziel nie debugera.  
  
-   Jeśli wyjątek nie jest obsługiwany, dzieli debugera.  
  
###  <a name="BKMK_JS_Customize_Just_My_Code"></a>Dostosowywanie tylko mój kod  
 Kategoryzację użytkowników i kodu innych użytkowników dla jednego projektu programu Visual Studio, należy dodać plik .json o nazwie `mycode.json` do folderu głównego projektu.  
  
 Klasyfikacje są wykonywane w następującej kolejności:  
  
1.  Domyślne klasyfikacje  
  
2.  Klasyfikacje w `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` pliku  
  
3.  Klasyfikacje w `mycode. json` pliku bieżącego projektu.  
  
 Każdy krok klasyfikacji zastępuje poprzednie kroki. Plik JSON nie konieczne utworzenie listy wszystkich par wartości klucza i **MyCode**, **biblioteki**, i **Unrelated** wartości mogą być puste tablice.  
  
 Pliki kodu JSON użyć następującej składni:  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec",  
        . . .  
        "UrlOrFileSpec"  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec",  
        . .  
        "UrlOrFileSpec"  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec",  
        . . .  
        "UrlOrFileSpec"  
    ]  
}  
  
```  
  
 **Eval, funkcji i ScriptBlock**  
  
 **Eval**, **funkcja**, i **ScriptBlock** jak dynamicznie określać pary wartości klucza jest klasyfikowany wygenerowanego kodu.  
  
|||  
|-|-|  
|**Eval**|Skrypt, który jest wykonywany przez przekazanie ciąg do dostarczony host `eval` funkcji. Domyślnie Eval skryptu jest sklasyfikowany jako **MyCode**.|  
|**Funkcja**|Skrypt, który jest wykonywany przez przekazanie ciąg `Function` konstruktora. Domyślnie funkcja skryptu jest sklasyfikowany jako **LibraryCode**.|  
|**Blok skryptu**|Skrypt, który jest wykonywany przez przekazanie ciąg `setTimeout`, `setImmediate`, lub `setInterval` funkcji. Domyślnie ScriptBlock skryptu jest sklasyfikowany jako **UnrelatedCode**.|  
  
 Wartość można zmienić na jedną z następujących słów kluczowych:  
  
-   `MyCode`klasyfikuje skryptu jako **MyCode**.  
  
-   `Library`klasyfikuje skryptu jako **LibraryCode**.  
  
-   `Unrelated`klasyfikuje skryptu jako **UnrelatedCode**.  
  
 **MyCode, biblioteki, a niepowiązanych**  
  
 **MyCode**, **biblioteki**, i **Unrelated** par wartości klucza Określ adresy URL lub pliki, które chcesz uwzględnić w klasyfikacji:  
  
|||  
|-|-|  
|**MyCode**|Tablica adresy URL lub pliki, które są sklasyfikowane jako **MyCode**.|  
|**Biblioteki**|Tablica adresy URL lub pliki, które są sklasyfikowane jako **LibraryCode**.|  
|**Niepowiązane**|Tablica adresy URL lub pliki, które są sklasyfikowane jako **UnrelatedCode**.|  
  
 Ciąg adresu url lub pliku może zawierać jeden lub więcej `*` znaków, które odpowiadają zero lub więcej znaków. `*`odpowiada wyrażeniu regularnemu `.*`.