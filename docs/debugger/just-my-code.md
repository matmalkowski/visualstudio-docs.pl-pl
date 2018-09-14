---
title: Debugowanie kodu użytkownika przy użyciu tylko mój kod | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a2873f691fdaa1251a5562e21e2bbd0467eb2e2
ms.sourcegitcommit: 7bb0225e1fd45999ce09e0b49c2cfae515c27e11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45612756"
---
# <a name="specify-whether-to-debug-only-user-code-using-just-my-code-in-visual-studio"></a>Określ, czy w celu debugowania tylko kodu użytkownika przy użyciu tylko mój kod w programie Visual Studio
Można skonfigurować w programie Visual Studio automatycznie Przekrocz nad systemu, framework i innymi wywołaniami niespowodowanymi przez użytkownika i zwinąć te wywołania w oknie stosu wywołań. Funkcja, która włącza lub wyłącza to zachowanie jest nazywane *tylko mój kod*. W tym temacie opisano sposób używania tylko mój kod w projektach w językach C#, Visual Basic, C++ i JavaScript.

Dla większości języków programowania tylko mój kod jest włączona domyślnie.
  
##  <a name="BKMK_Enable_or_disable_Just_My_Code"></a> Włącz lub wyłącz opcję tylko mój kod  
 Aby włączyć lub wyłączyć opcję tylko mój kod, wybierz opcję **Narzędzia > Opcje** menu w programie Visual Studio. W **debugowanie** > **ogólne** węzła, wybierz lub wyczyść **Włącz tylko mój kod**.
  
 ![Włącz opcję tylko mój kod w oknie dialogowym Opcje](../debugger/media/dbg_justmycode_options.png "DBG_JustMyCode_Options")  
  
> [!NOTE]
>  **Włącz tylko mój kod** ustawienie jest ustawieniem globalnym, która jest stosowana do wszystkich projektów programu Visual Studio, we wszystkich językach.  
  
###  <a name="BKMK_Override_call_stack_filtering"></a> Pokaż kod niezwiązany z użytkownikiem w widokach stosu wywołań  
 W widokach zawierających Pokaż stos wywołań, takie jak **stos wywołań** i **zadania** systemu windows, tylko mój kod zwinięte niebędący kodem użytkownika do ramka z adnotacją etykietą `[External Code]`. Aby wyświetlić zwinięte ramek, wybierz **Pokaż kod zewnętrzny** na menu kontekstowe stosu wywołań wyświetlane.

 ![Pokaż kod zewnętrzny, w oknie stosu wywołań](../debugger/media/dbg_justmycode_showexternalcode.png "DBG_JustMyCode_ShowExternalCode")
  
> [!NOTE]
>  **Pokaż kod zewnętrzny** ustawienia są zapisywane do profilera bieżącego użytkownika. Jest stosowana do wszystkich projektów we wszystkich językach, które są otwierane przez użytkownika.

##  <a name="identify-user-code-while-debugging"></a>Identyfikator użytkownika kodu podczas debugowania 

**Modułów** okna można stwierdzić, które moduły kodu debuger jest traktowanie jako kod użytkownika lub Mój kod, wraz z informacjami, takich jak symboli podczas ładowania stanu modułu. Aby uzyskać więcej informacji, zobacz [zapoznać się z jak dołącza debuger do swojej aplikacji](../debugger/debugger-tips-and-tricks.md#modules_window).
  
##  <a name="BKMK__NET_Framework_Just_My_Code"></a> .NET framework tylko mój kod  
  
###  <a name="BKMK_NET_User_and_non_user_code"></a> Kod użytkownika i niezwiązanych z użytkownikiem  
 Aby rozróżnić kod użytkownika z poziomu kodu niepochodzącego od użytkownika, tylko mój kod patrzy na pliki symboli (.pdb) i optymalizacje program. Debuger uważa kod za niebędący kodem użytkownika, gdy plik binarny jest zoptymalizowane pod kątem lub plik PDB nie jest dostępny.
  
 Trzy atrybuty wpływa również na debuger uważa się mój kod:  
  
-   <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> Nakazuje debugerowi, że kod, który jest stosowany do nie jest mój kod.  
  
-   <xref:System.Diagnostics.DebuggerHiddenAttribute> Ukrywa kodu z debugerem, nawet wtedy, gdy tylko mój kod jest wyłączona.  
  
-   <xref:System.Diagnostics.DebuggerStepThroughAttribute> Nakazuje debugerowi, aby przejść przez kod, który zostanie zastosowany do, a nie kod krok po kroku.  
  
 Inny kod jest uważane za kod użytkownika.  
  
###  <a name="BKMK_NET_Stepping_behavior"></a> Zachowanie przechodzenia krok po kroku  
 Po użytkownik **Step Into** (skrót klawiaturowy: F11) kod niezwiązany z użytkownikiem, debuger nie wchodzi WE kod do następnej instrukcji użytkownika. Gdy możesz **Step Out** (klawiatura: Shift + F11), debuger działa do następnego wiersza kodu użytkownika. Jeśli żaden kod użytkownika zostanie osiągnięty, a następnie wykonywanie jest kontynuowane do czasu jej wyjścia, punkt przerwania zostaje trafiony lub wystąpienia wyjątku.  
  
###  <a name="BKMK_NET_Breakpoint_behavior"></a> Zachowanie punktu przerwania  
 Jeśli włączono opcję tylko mój kod, można określić **Przerwij wszystko** (klawiatura: Ctrl + Alt + Break) i zatrzymać wykonywanie w miejscu, w przypadku, gdy nie jest wykonywany kod użytkownika do wyświetlenia. W takiej sytuacji zostanie wyświetlone okno Brak źródła. Jeśli następnie wybierzesz polecenie kroku, debuger spowoduje przejście do następnego wiersza kodu użytkownika.  
  
###  <a name="BKMK_NET_Exception_behavior"></a> Zachowanie wyjątku  
 Jeśli wystąpi nieobsługiwany wyjątek w kodzie niezwiązanych z użytkownikiem, debuger przerywa w wierszu w kodzie użytkownika, w którym został wygenerowany wyjątek.  
  
 Włączenie wyjątku pierwszej szansy wyjątki wiersz kodu użytkownika jest wyróżniony w kolorze zielonym. Stos wywołań Wyświetla ramka z adnotacją etykietą **[kod zewnętrzny]**.  
  
##  <a name="BKMK_C___Just_My_Code"></a> Tylko mój kod w języku C++  
  
###  <a name="BKMK_CPP_User_and_non_user_code"></a> Kod użytkownika i niezwiązanych z użytkownikiem  
C++ tylko mój kod jest inny niż .NET Framework i JavaScript tylko mój kod, ponieważ przechodzenia krok po kroku zachowanie jest niezależna od zachowania stosu wywołań.  

Począwszy od programu Visual Studio 2017 15.8, można określić, czy włączyć opcję tylko mój kod dla języka C++ przy użyciu **narzędzia** > **opcje** > **debugowanie**  >  **Ogólne** > **Włącz tylko mój kod** (jest włączony domyślnie). Jest to równoważne użyciu [/JMC (tylko mój kod debugowanie)](/cpp/build/reference/jmc) przełącznika kompilatora.
  
 **Stosy wywołań**  
  
 Domyślnie debuger uważa za kod niezwiązany z użytkownikiem w oknach stos wywołań tych funkcji:  
  
-   Funkcje za pomocą informacji o źródle pozbawionego włókien w pliku symboli.  
  
-   Funkcje, w której pliki symboli oznacza, że brak pliku źródłowego, odpowiadający ramki stosu.  
  
-   Określona w funkcji `*.natjmc` pliki `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` folderu.  
  
 **Przechodzenie krok po kroku**  
  
 Domyślnie tylko funkcje określone w `*.natstepfilter` pliki `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` folderu są uważane za kod niezwiązany z użytkownikiem.  
  
 Możesz utworzyć swój własny `.natstepfilter` i `.natjmc` dostosować przechodzenie krok po kroku i wywoływać zachowanie okna stosu `%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers`.  
  
###  <a name="BKMK_CPP_Stepping_behavior"></a> Zachowanie przechodzenia krok po kroku  
 Gdy użytkownik **Step Into** (skrót klawiaturowy: F11) kod niezwiązany z użytkownikiem z kodu użytkownika, debuger nie wchodzi WE kod do następnego wiersza kodu użytkownika. Gdy możesz **Step Out** (klawiatura: Shift + F11), debuger działa do następnego wiersza kodu użytkownika. Jeśli żaden kod użytkownika zostanie osiągnięty, a następnie wykonywanie jest kontynuowane do czasu jej wyjścia, punkt przerwania zostaje trafiony lub wystąpienia wyjątku.  
  
 Jeśli debuger przerwie działanie na kodzie niezwiązanych z użytkownikiem (na przykład, jeśli polecenie Przerwij wszystko zatrzyma niebędący kodem użytkownika), nadal przechodzenie krok po kroku w kodzie niezwiązanych z użytkownikiem.
  
###  <a name="BKMK_CPP_Exception_behavior"></a> Zachowanie wyjątku  
 Kiedy debuger uderza w wyjątku, zatrzymuje się na wyjątek, niezależnie od tego, czy znajduje się w użytkownika lub kod niezwiązany z użytkownikiem. **User-unhandled** opcji na liście **wyjątki** okno dialogowe, są ignorowane.  
  
###  <a name="BKMK_CPP_Customize_stepping_behavior"></a> Dostosowywanie zachowania przechodzenia krok po kroku  
 Można określić funkcji, aby przejść przez wymienienie ich jako kod niezwiązany z użytkownikiem w `*.natstepfilter` plików.  
  
-   Aby określić kod niezwiązany z użytkownikiem dla wszystkich użytkowników komputera programu Visual Studio, należy dodać plik .natstepfilter `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` folderu.  
  
-   Aby określić kod niezwiązany z użytkownikiem dla poszczególnych użytkowników, należy dodać plik .natstepfilter `%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers` folderu.  
  
 .natstepfilter pliki są plikami xml o następującej składni:  
  
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
|Funkcja|Wymagane. Określa jedną lub więcej funkcji jako funkcje niezwiązanych z użytkownikiem.|  
|`Name`|Wymagane. ECMA 262 sformatowane wyrażeń regularnych, określając nazwę pełne działanie do dopasowania. Na przykład:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> Nakazuje debugerowi, że wszystkie metody w `MyNS::MyClass` należy uznać za kod niezwiązany z użytkownikiem. W dopasowaniu jest uwzględniana wielkość liter.|  
|`Module`|Opcjonalna. ECMA 262 sformatowane wyrażeń regularnych, określić pełną ścieżkę do modułu zawierający funkcję. Dopasowanie jest rozróżniana wielkość liter.|  
|`Action`|Wymagane. Jedną z następujących wartości rozróżniana wielkość liter:<br /><br /> -   `NoStepInto`  -Nakazuje debugerowi na wkroczenie za pośrednictwem funkcji dopasowany.<br />-   `StepInto`  — informuje debuger, aby wejść do funkcji dopasowane zastąpienie wszelkich innych `NoStepInto` dopasowane funkcji.|  
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a> Dostosowywanie zachowania dotyczącego stosu wywołań  
 Można określić moduły, pliki źródłowe i funkcji, które mają być traktowane jako kod niezwiązany z użytkownikiem w stosy wywołań, określając je w `*.natjmc` plików.  
  
-   Aby określić kod niezwiązany z użytkownikiem dla wszystkich użytkowników komputera programu Visual Studio, należy dodać plik .natjmc `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` folderu.  
  
-   Aby określić kod niezwiązany z użytkownikiem dla poszczególnych użytkowników, należy dodać plik .natjmc `%USERPROFILE%\My Documents\Visual Studio 2017\Visualizers` folderu.  
  
 .natjmc pliki są plikami xml o następującej składni:  
  
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
  
 **Atrybuty elementu modułów**  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagane. Pełna ścieżka moduł lub moduły. Można używać symboli wieloznacznych Windows `?` (zero lub jeden znak) i `*` (zero lub więcej znaków). Na przykład<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> Nakazuje debugerowi Traktuj wszystkie moduły w `\3rdParty\UtilLibs` na dowolnym dysku jako kodu zewnętrznego.|  
|`Company`|Opcjonalna. Nazwa firmy, która publikuje moduł, który jest osadzony w pliku wykonywalnym. Ten atrybut służy do odróżniania modułów.|  
  
 **Atrybuty elementu pliku**  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagane. Pełna ścieżka pliku źródłowego lub pliki, które mają być traktowane jako kodu zewnętrznego. Można używać symboli wieloznacznych Windows `?` i `*` określając ścieżkę.|  
  
 **Atrybuty elementów — funkcja**  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Wymagane. W pełni kwalifikowaną nazwę funkcji, które mają być traktowane jako kodu zewnętrznego.|  
|`Module`|Opcjonalna. Nazwa lub pełną ścieżkę do modułu, która zawiera funkcję. Ten atrybut służy do odróżniania funkcji o tej samej nazwie.|  
|`ExceptionImplementation`|Po ustawieniu `true`, stos wywołań Wyświetla funkcja, która zgłosiła wyjątek, a nie z tej funkcji.|  
  
##  <a name="BKMK_JavaScript_Just_My_Code"></a> Tylko mój kod języka JavaScript  
  
###  <a name="BKMK_JS_User_and_non_user_code"></a> Kod użytkownika i niezwiązanych z użytkownikiem  
 **Klasyfikacje kodu**  
  
 JavaScript tylko mój kod kontrolki przechodzenie krok po kroku, a następnie wywołać wyświetlanie stosu przez skategoryzowanie kodu w jednym z tych klasyfikacji:  
  
|||  
|-|-|  
|**MyCode**|Kod użytkownika, który umożliwia zbieranie i kontrolowanie.|  
|**LibraryCode**|Kod niezwiązany z użytkownikiem z bibliotek, które regularnie używane i aplikacji zależy od działał poprawnie (na przykład WinJS lub jQuery).|  
|**UnrelatedCode**|Kod niezwiązany z użytkownikiem, które mogą być wykonywane w aplikacji, ale nie jest on własnością i aplikacja nie bezpośrednio na niej się opierać działał poprawnie. (Na przykład może to obejmować advertising SDK, który wyświetla reklamy.) W projektach platformy uniwersalnej systemu Windows każdy kod, który jest ładowany do aplikacji za pomocą protokołu HTTP lub HTTPS identyfikatora URI jest również uważana za UnrelatedCode.|  
  
 Debuger JavaScript klasyfikuje automatycznie tych typów kodu:  
  
-   Skrypt, który jest wykonywany, przekazując ciąg do hosta — pod warunkiem `eval` funkcji zostanie sklasyfikowany jako **MyCode**.  
  
-   Skrypt, który jest wykonywany, przekazując ciąg do `Function` Konstruktor jest klasyfikowana jako **LibraryCode**.  
  
-   Skrypt, który znajduje się w dokumentacji framework, na przykład WinJS lub zestawu Azure SDK zostanie sklasyfikowany jako **LibraryCode**.  
  
-   Skrypt, który jest wykonywany, przekazując ciąg do `setTimeout`, `setImmediate`, lub `setInterval` funkcji zostanie sklasyfikowany jako **UnrelatedCode**.  
  
-   `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` Określa innego użytkownika i niezwiązanych z użytkownikiem kodu dla wszystkich projektów języka JavaScript w programie Visual Studio.  
  
 Możesz zmodyfikować domyślne klasyfikacje i klasyfikowania plików i adresy URL Dodaj przez plik JSON o nazwie `mycode.json` do folderu głównego projektu.  
  
 Inny kod jest klasyfikowana jako **MyCode**.  
  
###  <a name="BKMK_JS_Stepping_behavior"></a> Zachowanie przechodzenia krok po kroku  
  
-   Jeśli funkcja nie jest użytkownikiem (**MyCode**) kod, **Step Into** (skrót klawiaturowy: F11) zachowuje się jak **Step Over** (klawiatura: F10).  
  
-   Jeśli krok rozpoczyna się w niezwiązanych z użytkownikiem (**LibraryCode** lub **UnrelatedCode**) kodu, a następnie tymczasowo przechodzenie krok po kroku zachowuje się tak, jakby nie włączono opcję tylko mój kod. Gdy krok do kodu użytkownika, tylko mój kod przechodzenie krok po kroku zostanie ponownie włączony.  
  
-   Gdy krok w kodzie użytkownika skutkuje opuszczania bieżącego kontekstu wykonywania (takich jak krok w ostatnim wierszu programu obsługi zdarzeń), debuger zatrzymuje się w następnym wierszu wykonywany kod użytkownika. Na przykład, jeśli wykonuje wywołanie zwrotne **LibraryCode** Debuger kontynuuje do czasu następnego wiersza kodu użytkownika wykonuje kod.
  
-   **Step Out** (klawiatura: Shift + F11) zatrzymuje się w następnym wierszu kodu użytkownika. Jeśli żaden kod użytkownika zostanie osiągnięty, a następnie wykonywanie jest kontynuowane do czasu jej wyjścia, punkt przerwania zostaje trafiony lub wystąpienia wyjątku.  
  
###  <a name="BKMK_JS_Breakpoint_behavior"></a> Zachowanie punktu przerwania  
  
-   Punkty przerwania ustawione w kodzie będą zawsze zostanie osiągnięty, niezależnie od klasyfikacji kod  
  
-   Jeśli `debugger` — słowo kluczowe zostanie napotkany w:  
  
    -   **LibraryCode** kod, debuger zawsze przerywa pracę.  
  
    -   **UnrelatedCode** kod, debuger nie zatrzymuje.  
  
###  <a name="BKMK_JS_Exception_behavior"></a> Zachowanie wyjątku  
 Jeśli wystąpi nieobsługiwany wyjątek w:  
  
-   **MyCode** lub **LibraryCode** kod, debuger zawsze przerywa pracę.  
  
-   **UnrelatedCode** kodu, i **MyCode** lub **LibraryCode** kod znajduje się na stos wywołań, podziały debugera.  
  
 Jeśli pierwszej szansy wyjątki są włączone dla wyjątku w oknie dialogowym Wyjątki, a wyjątek jest zgłaszany w **LibraryCode** lub **UnrelatedCode** kodu:  
  
-   Jeśli wyjątek jest obsługiwany, debuger nie zostanie przerwane.  
  
-   Jeśli wyjątek nie jest obsługiwany, debuger przerywa.  
  
###  <a name="BKMK_JS_Customize_Just_My_Code"></a> Dostosowywanie tylko mój kod  
 Kategoryzowanie, użytkownika i kod niezwiązany z użytkownikiem dla pojedynczego projektu programu Visual Studio, należy dodać plik JSON o nazwie `mycode.json` do folderu głównego projektu.  
  
 Klasyfikacje są wykonywane w następującej kolejności:  
  
1.  Domyślne klasyfikacje  
  
2.  Klasyfikacje w `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` pliku  
  
3.  Klasyfikacje w `mycode. json` pliku bieżącego projektu.  
  
 Każdy krok klasyfikacji zastąpienia poprzednich kroków. Plik JSON nie konieczne utworzenie listy wszystkich pary klucz-wartość, a **MyCode**, **bibliotek**, i **Unrelated** wartości mogą być puste tablic.  
  
 Pliki kodu JSON, użyj następującej składni:  
  
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
  
 **Eval, funkcja i ScriptBlock**  
  
 **Eval**, **funkcja**, i **ScriptBlock** pary klucz-wartość jak dynamicznie określać jest klasyfikowany wygenerowanego kodu.  
  
|||  
|-|-|  
|**Eval**|Skrypt, który jest wykonywany, przekazując ciąg do hosta — pod warunkiem `eval` funkcji. Domyślnie skrypt — wersja próbna zostanie sklasyfikowany jako **MyCode**.|  
|**Function**|Skrypt, który jest wykonywany, przekazując ciąg do `Function` konstruktora. Domyślnie funkcja skryptu zostanie sklasyfikowany jako **LibraryCode**.|  
|**Blok skryptu**|Skrypt, który jest wykonywany, przekazując ciąg do `setTimeout`, `setImmediate`, lub `setInterval` funkcji. Domyślnie skryptów w blok skryptu zostanie sklasyfikowany jako **UnrelatedCode**.|  
  
 Możesz zmienić wartość, do jednego z tych słów kluczowych:  
  
-   `MyCode`  klasyfikuje skryptu jako **MyCode**.  
  
-   `Library`  klasyfikuje skryptu jako **LibraryCode**.  
  
-   `Unrelated`  klasyfikuje skryptu jako **UnrelatedCode**.  
  
 **MyCode, biblioteki i niepowiązanych**  
  
 **MyCode**, **bibliotek**, i **Unrelated** pary klucz-wartość Określ adresy URL lub pliki, które mają zostać uwzględnione w klasyfikacji:  
  
|||  
|-|-|  
|**MyCode**|Tablicę adresów URL lub pliki, które są klasyfikowane jako **MyCode**.|  
|**Biblioteki**|Tablicę adresów URL lub pliki, które są klasyfikowane jako **LibraryCode**.|  
|**Niepowiązane**|Tablicę adresów URL lub pliki, które są klasyfikowane jako **UnrelatedCode**.|  
  
 Adres url lub plik ciąg może zawierać jeden lub więcej `*` znaków, które dopasowuje zero lub więcej znaków. `*` jest to równoważne wyrażenie regularne `.*`.
