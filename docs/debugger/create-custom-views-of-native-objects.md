---
title: Tworzenie niestandardowych widoków obiektów macierzystych w debugerze | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/27/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 38656b9c5ce4165f2a04b5e6d76411ce7f005855
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="create-custom-views-of-native-objects-in-the-visual-studio-debugger"></a>Tworzenie niestandardowych widoków obiektów macierzystych w debugerze programu Visual Studio
Framework programu Visual Studio Natvis pozwala dostosować Visual Studio Wyświetla typy natywne w oknach zmiennych debugera (na przykład **czujki** okna, **zmiennych lokalnych** okna, a następnie w  **Etykietki danych**.
  
 Zastępuje Natvis **autoexp.dat —** pliku, który był używany w starszych wersjach programu Visual Studio i składnia XML oferty, lepszą diagnostykę, przechowywanie wersji i obsługa wielu plików.  
  
> [!NOTE]
>  Nie można użyć w ramach Natvis wizualizacje po:  
>   
>  -  Debugowania projektu pulpitu Windows w języku C++ z ustawioną typ debugera **mieszane**.  
> -   Robią w aplikacji pulpitu systemu Windows w trybie zgodności zarządzanego debugowanie w trybie mieszanym (**Narzędzia > Opcje > debugowanie > Ogólne > Użyj trybu zgodności zarządzanej**).  
> -   Debugowania w aplikacji pulpitu systemu Windows w trybie macierzystym zgodności (**Narzędzia > Opcje > debugowanie > Ogólne > Użyj natywnego trybu zgodności**).  
  
##  <a name="BKMK_Why_create_visualizations_"></a> Dlaczego tworzenie wizualizacji Natvis?  
 W ramach Natvis służy do tworzenia reguł wizualizacji dla typów tworzonego, deweloperzy mogą zobaczyć je łatwo podczas debugowania.  
  
 Na przykład na poniższej ilustracji przedstawiono zmiennej typu [Windows::UI::Xaml::Controls::TextBox](http://go.microsoft.com/fwlink/?LinkId=258422) która jest wyświetlana w debugerze bez żadnych niestandardowych wizualizacje zastosowane.  
  
 ![Pole tekstowe domyślne wizualizacji](../debugger/media/dbg_natvis_textbox_default.png "DBG_NATVIS_TextBox_Default")  
  
 Pokazuje wyróżniony wiersz `Text` właściwość `TextBox` klasy. Hierarchia klas złożonych utrudnia znaleźć tę wartość; Ponadto debuger nie może ustalić sposób interpretowania wpisz niestandardowy ciąg używane przez obiekt, więc nie zawiera ciągu przechowywany w polu tekstowym.  
  
 Taki sam `TextBox` wygląda znacznie prostsza w oknie zmiennej wizualizacji niestandardowe reguły są stosowane. Ważne elementy członkowskie klasy, które mogą być wyświetlane ze sobą i debuger zawiera wartość ciągu podstawowy typ niestandardowy ciąg.  
  
 ![Pole tekstowe danych przy użyciu wizualizatora](../debugger/media/dbg_natvis_textbox_visualizer.png "DBG_NATVIS_TextBox_Visualizer")  
  
##  <a name="BKMK_Using_Natvis_files"></a> Używających plików Natvis  
 .natvis są pliki XML z rozszerzeniem .natvis. Schemat jest zdefiniowany w **%VSINSTALLDIR%\Xml\Schemas\natvis.xsd**.  
  
 Podstawowa struktura pliku .natvis jest co najmniej jeden `Type` elementów, gdzie każdy `Type` element reprezentuje wpisem wizualizacji dla typu, w której w pełni kwalifikowana nazwa jest określona w `Name` atrybutu.  
  
```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
  <Type Name="MyNamespace::CFoo">  
    .  
    .  
  </Type>  
  
  <Type Name="...">  
    .  
    .  
  </Type>  
</AutoVisualizer>  
```  
  
 Program Visual Studio udostępnia niektóre pliki .natvis **%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers** folderu. Te pliki zawierają zasady wizualizacji wiele typów wspólnych i może służyć jako przykłady, pisząc wizualizacji dla nowych typów.  
  
## <a name="adding-natvis-files-to-your-projects"></a>Dodawanie plików .natvis do projektów  
 Możesz dodać pliki .natvis do każdego projektu C++.  
  
 Aby dodać nowego pliku .natvis w otwartych projektów C++, wybierz węzeł projektu w **Eksploratora rozwiązań**i kliknij przycisk **Dodaj > Nowy element > Visual C++ > Narzędzia > pliku wizualizacji debugera (.natvis)**. Debuger załaduje pliki Natvis z projektów C++ automatycznie. Domyślnie pliki Natvis w projekcie również są wstawiane do pliku .pdb skompilowanego przez projekt. Oznacza to, że przypadku debugowania pliku binarnego stworzonej przez ten projekt debuger ładuje pliku Natvis z .pdb nawet, jeśli nie masz projekt jest otwarty. Jeśli nie chcesz, aby pliku .natvis do uwzględnienia w .pdb, kliknij prawym przyciskiem myszy plik .natvis **Eksploratora rozwiązań**i w **właściwości konfiguracji** zestaw okna **wyłączone z kompilacji**  do **tak**.  
  
 Zalecane jest, aby edytować pliki Natvis przy użyciu programu Visual Studio Any zmiany podczas debugowania zaczęły obowiązywać automatycznie podczas zapisywania pliku. Udoskonalone środowisko edytowania jest również uzyskać z funkcji IntelliSense.  
  
 Pliki Natvis, które są ładowane z .pdb mają zastosowanie tylko do typów modułu, do którego odwołuje się pliku pdb. Na przykład, jeśli wpis dla typu o nazwie definiuje Module1.pdb `Test`, ten wpis stosowane tylko do **testu** klasy w Module1.dll. Jeśli inny moduł również definiuje klasę o nazwie **testu**, jego Module1.pdb natvis wpis nie ma zastosowania do niego.  
  
##  <a name="BKMK_natvis_location"></a> Wdrażanie plików .natvis  
 Jeśli pliku .natvis ma zastosowanie tylko do typów, które tworzysz projekt programu Visual Studio, nie trzeba wykonywać żadnych czynności; .natvis znajduje się w .pdb. Jednak można dodać .natvis pliki do katalogu użytkownika lub w katalogu systemu, jeśli chcesz, aby zastosować do wielu projektów.  
  
 Kolejność, w których .natvis pliki są oceniane następująco:  
  
1.  pliki .natvis osadzony w .pdb, który debugowania (chyba, że plik o tej samej nazwie istnieje w załadowanym projekcie).  
  
2.  .natvis pliki, które są częścią załadowanego projektu C++ lub element najwyższego poziomu rozwiązania. Ta grupa zawiera wszystkie załadowanych projektów C++, w tym biblioteki klas, ale nie zawiera projekty innych języków (na przykład nie można załadować pliku .natvis z projektu C#). Dla pliku wykonywalnego projektów należy używać elementów rozwiązania do obsługi .natvis pliki, które nie są już obecne w .pdb, ponieważ nie istnieje żaden projekt C++.  
  
3.  Katalog natvis specyficzne dla użytkownika (na przykład **%USERPROFILE%\Documents\Visual 2017\Visualizers w Studio** lub **%USERPROFILE%\My 2015\Visualizers Documents\Visual Studio**).  
  
4.  Katalog Natvis systemowe (**%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers**). Jest to katalog, gdy są kopiowane pliki .natvis, które są zainstalowane z programem Visual Studio. Jeśli użytkownik ma uprawnienia administratora, możesz dodać inne pliki do tego katalogu, a także.  
  
## <a name="modifying-natvis-files-while-debugging"></a>Modyfikowanie plików .natvis podczas debugowania  
 Podczas debugowania projektu, w którym jest dostępna, można zmodyfikować pliku .natvis w IDE. Otwórz plik w IDE (przy użyciu tego samego wystąpienia programu Visual Studio debugowania z), zmodyfikuj go i zapisać go. Po zapisaniu pliku **czujki** i **zmiennych lokalnych** system windows powinien zostać zaktualizowany w celu odzwierciedlenia zmian. Jeśli zmodyfikujesz pliku .natvis poza IDE, zmiany nie będą obowiązywać automatycznie. Do aktualizacji systemu windows, można oszacować **.natvisreload** w **czujki** okna. Ta akcja powoduje, że zmiany zaczęły obowiązywać bez ponownego uruchomienia sesji debugowania.  
  
 Można również dodawać lub usuwać .natvis plików do rozwiązania, które debugowania i Visual Studio dodaje lub usuwa odpowiednich wizualizacji.  
  
 Jeśli pliku .natvis jest osadzony w .pdb, nie można modyfikować podczas debugowania.  
  
 Użyj **.natvisreload** poleceń podczas uaktualniania pliku natvis do nowszej wersji (na przykład, jeśli jest on wyewidencjonowany do kontroli źródła i chcesz wykrycie ostatnich zmian, że osoba else wprowadzone w pliku). Zalecane jest, aby edytować pliki natvis za pomocą edytora xml programu Visual Studio.  
  
##  <a name="BKMK_Expressions_and_formatting"></a> Wyrażenia i formatowanie  
 Wizualizacje Natvis Użyj wyrażenia języka C++, aby określić elementy danych do wyświetlenia. Oprócz rozszerzenia i ograniczenia dotyczące wyrażeń języka C++ w debugerze, które są opisane w [kontekstu — Operator (C++)](../debugger/context-operator-cpp.md), należy zwrócić uwagę następujące różnice:  
  
-   Wyrażenia Natvis są obliczane w kontekście obiektu wizualizowanego, nie bieżącej ramki stosu. Na przykład, jeśli używasz `x` w wyrażeniu Natvis identyfikator odwołuje się do pola o nazwie `x` w obiekcie wizualizowanego nie do zmiennej lokalnej o nazwie `x` w funkcji aktualnie wykonywane. Nie masz dostępu do zmiennych lokalnych w wyrażeniach Natvis, mimo że można uzyskać dostępu do zmiennych globalnych.  
  
-   Wyrażenia Natvis nie zezwalaj na obliczanie funkcji lub efekty uboczne. Oznacza to, że wywołania funkcji i operatory przypisania są ignorowane. Ponieważ [debugera funkcje wewnętrzne](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) są efekt uboczny wolnej one może być za darmo wywoływana z dowolne wyrażenie Natvis, nawet jeśli są niedozwolone wywołania innych funkcji.  
  
 Aby kontrolować sposób wyświetlania wyrażenia w oknie zmiennej, można użyć dowolnego z specyfikatory formatu, które zostały opisane w [specyfikatory formatu](../debugger/format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) sekcji [specyfikatory formatu w C++](../debugger/format-specifiers-in-cpp.md) tematu. Należy pamiętać, że specyfikatory formatu są ignorowane, gdy wpis wirtualizacji jest używana wewnętrznie przez Natvis, takich jak `Size` wyrażenie w [ArrayItems rozszerzenia](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).  
  
## <a name="natvis-views"></a>Widoki Natvis  
 Widoki Natvis umożliwiają wyświetlanie dowolnego typu w więcej niż jeden sposób. Na przykład można zdefiniować widok o nazwie **proste** który zapewnia uproszczony widok typu. Na przykład poniżej przedstawiono wizualizację `std::vector`:
  
```xml
<Type Name="std::vector&lt;*&gt;">  
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>  
    <Expand>  
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>  
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>  
        <ArrayItems>  
            <Size>_Mylast - _Myfirst</Size>  
            <ValuePointer>_Myfirst</ValuePointer>  
        </ArrayItems>  
    </Expand>  
</Type>  
```  
  
 `DisplayString` i `ArrayItems` elementy są używane w widoku domyślne i w widoku uproszczonym, podczas gdy `[size]` i `[capacity]` elementy są wykluczone z widoku uproszczonym. Można użyć **, widok** specyfikatorze, aby określić alternatywne widoku formatu. W **czujki** okna, określ prosty widoku w postaci **vec,view(simple)**:  
  
 ![Okno czujki z widokiem proste](../debugger/media/watch-simpleview.png "SimpleView czujki")  
  
##  <a name="BKMK_Diagnosing_Natvis_errors"></a> Diagnozowanie błędów Natvis  
 Diagnostyka Natvis służy do rozwiązywania składni oraz błędy analizy. Debuger wystąpią błędy we wpisie wizualizacji, ignoruje błędy i wyświetla albo typu w postaci raw lub pobrania inną wizualizację odpowiedni. Aby zrozumieć, dlaczego jest ignorowana wpis wizualizacji i podstawowe błędy są można włączyć diagnostyki Natvis **Narzędzia > Opcje > debugowanie > okno danych wyjściowych > Natvis komunikaty diagnostyczne (tylko C++)** Opcja. Błędy są wyświetlane w **dane wyjściowe** okna.  
  
##  <a name="BKMK_Syntax_reference"></a> Odwołania do składni Natvis  
  
###  <a name="BKMK_AutoVisualizer"></a> AutoVisualizer element  
 `AutoVisualizer` Element węzła głównego pliku .natvis i zawiera przestrzeń nazw `xmlns:` atrybutu.  
  
```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  
  
###  <a name="BKMK_Type"></a> Typ elementu  
 Typ podstawowy wygląda następująco:  
  
```xml
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  
```  
  
 Określa:  
  
1.  Typ tej wizualizacji powinna być używana do ( `Type Name` atrybutu).  
  
2.  Jak powinna wyglądać wartości obiektu tego typu ( `DisplayString` elementu).  
  
3.  Elementy członkowskie tego typu należy wygląd gdy użytkownik rozwija go w oknie zmiennej ( `Expand` węzła).  
  
 **Szablonu klasy** `Name` atrybutu `Type` element akceptuje gwiazdkę `*` jako symbolu wieloznacznego, używanej do nazwy klas opartego na szablonie:  
  
```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
  
```  
  
 W tym przykładzie jest używany wizualizacji tej samej, czy obiekt jest `CAtlArray<int>` lub `CAtlArray<float>`. Jeśli istnieje wpis wizualizacji określonych dla `CAtlArray<float>`, następnie pierwszeństwo ogólnego jeden.  
  
 Należy pamiętać, że parametry szablonu może być przywoływany w zapisie wizualizacji przy użyciu makra $T1, $T2 i tak dalej. Aby uzyskać przykłady makr, zobacz pliki .natvis dostarczanego z programem Visual Studio.  
  
####  <a name="BKMK_Visualizer_type_matching"></a> Dopasowywanie typu wizualizatora  
 W przypadku niepowodzenia wpis wizualizacji do sprawdzania poprawności dalej wizualizacji dostępne jest używany.  
  
#### <a name="inheritable-attribute"></a>Atrybut dziedziczonych  
 Można określić, czy wizualizacji dotyczy tylko typu podstawowego lub typu podstawowego i wszystkie typy pochodne z opcjonalnym `Inheritable` atrybutu. Poniższa wizualizację dotyczą tylko `BaseClass` typu:  
  
```xml
<Type Name="Namespace::BaseClass" Inheritable="true">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  
  
 Wartość domyślna `Inheritable` jest `true`.  
  
#### <a name="priority-attribute"></a>Pierwszeństwo atrybutów  
 `Priority` Atrybut określa kolejność, w którym alternatywne definicje są używane, jeśli definicja nie powiedzie się, można przeanalizować. Możliwe wartości `Priority` są: `Low`, `MediumLow`,`Medium`, `MediumHigh`, i `High`, a wartość domyślna to `Medium`.  
  
 Atrybut priorytet powinien być używany tylko odróżnienie priorytetów w ramach tego samego pliku .natvis nie między różne pliki.  
  
 W poniższym przykładzie mamy najpierw przeanalizować wpis odpowiadający 2015 STL, a w przypadku niepowodzenia można przeanalizować używamy alternatywny wpisu dla wersji 2013 STL:  
  
```xml
<!-- VC 2013 -->  
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">  
     <DisplayString>{_Callee}</DisplayString>  
    <Expand>  
        <ExpandedItem>_Callee</ExpandedItem>  
    </Expand>  
</Type>  
  
<!-- VC 2015 -->  
<Type Name="std::reference_wrapper&lt;*&gt;">  
    <DisplayString>{*_Ptr}</DisplayString>  
    <Expand>  
        <Item Name="[ptr]">_Ptr</Item>  
    </Expand>  
</Type>  
```  
  
####  <a name="BKMK_Versioning"></a> Wersja elementu  
 Użyj `Version` elementu do wizualizacji zakresu określone moduły i ich wersji, która nazwa kolizji można zminimalizować i różne wizualizacje mogą być używane dla różnych wersji typów. Na przykład:  
  
```xml
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  
  
 W tym przykładzie ma zastosowanie tylko do wizualizacji `DirectUI::Border` odnaleźć typu w `Windows.UI.Xaml.dll` z wersji 1.0 do wersji 1.5. Dodawanie elementów wersji zakresów wpis wizualizacji danego modułu i wersję i zmniejsza przypadkowej niezgodności. Jednak jeśli typ jest zdefiniowany w typowych pliku nagłówka, który jest używany przez inną modułów, wizualizacji kontrolą wersji nie została zastosowana, gdy typ nie jest określony moduł.  
  
#### <a name="optional-attribute"></a>Opcjonalny atrybut  
 `Optional` Atrybut może występować w każdym węźle. W przypadku niepowodzenia żadnych podwyrażenia wewnątrz węzła Opcjonalnie można przeanalizować tego węzła jest ignorowana, ale pozostałe elementu Type jest nadal ważny. W następującego typu `[State]` jest Nieopcjonalne, ale `[Exception]` jest opcjonalna.  Oznacza to, że jeśli `MyNamespace::MyClass` zawiera pole o nazwie _`M_exceptionHolder`, możesz nadal wyświetlany jest zarówno `[State]` węzła i `[Exception]` węzła, ale jeśli `_M_exceptionHolder` brakuje zostanie wyświetlony tylko `[State]` węzła.
  
```xml
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  
  
###  <a name="BKMK_Condition_attribute"></a> Atrybut warunku  
 Opcjonalny `Condition` atrybut jest dostępna dla wielu elementów wizualizacji i określa, kiedy należy użyć reguły wizualizacji. Jeśli wyrażenie w elemencie atrybut condition jest rozpoznawana jako `false`, a następnie reguła wizualizacji określone przez element nie zostanie zastosowana. Czy jest spełniony, czy istnieje nie `Condition` atrybutu, a następnie reguła wizualizacji zostanie zastosowana do typu. Można użyć tego atrybutu dla `if-else` logiki wpisów wizualizacji. Na przykład ma dwa następujące wizualizacji `DisplayString` elementy na typ wskaźnika inteligentnego:  
  
```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
  
```  
  
 Gdy `_Myptr` element członkowski jest `null`, warunek pierwszy `DisplayString` rozpoznawany jako element `true`, dzięki czemu zostanie wyświetlony formularz. Gdy `_Myptr` element członkowski nie jest `null`, warunek jest `false`, a drugi `DisplayString` element jest wyświetlany.  
  
### <a name="includeview-and-excludeview-attributes"></a>Atrybuty IncludeView i ExcludeView  
 Te atrybuty Określ elementy, które mają być wyświetlane lub nie są wyświetlane w różnych widoków. Na przykład podana Specyfikacja Natvis `std::vector`:  
  
```xml
<Type Name="std::vector&lt;*&gt;">  
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>  
    <Expand>  
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>  
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>  
        <ArrayItems>  
            <Size>_Mylast - _Myfirst</Size>  
            <ValuePointer>_Myfirst</ValuePointer>  
        </ArrayItems>  
    </Expand>  
</Type>  
```  
  
 Prosty widok nie zawiera [rozmiar] i [pojemności] elementy w widoku uproszczonym. Jeśli ma użyliśmy `IncludeView="simple"` zamiast `ExcludeView`, `[size]` i `[capacity]` elementy zostaną pokazane w widoku uproszczonym, a nie w widok domyślny.  
  
 Można użyć `IncludeView` i `ExcludeView` atrybuty dla typów, a także na poszczególne elementy.  
  
###  <a name="BKMK_DisplayString"></a> Klasa DisplayString  
 A `DisplayString` element określa ciąg, który będzie wyświetlany jako wartość zmiennej. Akceptowane są dowolne ciągi mieszanym za pomocą wyrażeń. Wszystkie elementy wewnątrz nawiasów klamrowych jest interpretowany jako wyrażenie. Na przykład `DisplayString` wpis podobnie do następującej:  
  
```xml
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  
  
```  
  
 Oznacza że zmienne typu `CPoint` są wyświetlane tak jak na ilustracji:  
  
 ![Za pomocą elementu DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "DBG_NATVIS_CPoint_DisplayString")  
  
 W `DisplayString` wyrażenie `x` i `y`, które są członkami `CPoint`, znajdują się wewnątrz nawiasów klamrowych i ich wartości. Wyrażenie, które pokazuje, jak można wprowadzić nawias klamrowy przy użyciu podwójne nawiasy klamrowe ( `{{` lub `}}` ).  
  
> [!NOTE]
>  `DisplayString` Element jest jedynym elementem, który akceptuje dowolne ciągi i składni nawias klamrowy. Wszystkie inne elementy wizualizacji akceptuje tylko wyrażeń, które są oceniane przez debuger.  
  
###  <a name="BKMK_StringView"></a> StringView  
 `StringView` Element definiuje wyrażenie, którego wartość ma do wysłania do wizualizatora tekst. Na przykład, załóżmy, że mamy następujące wizualizację dla `ATL::CStringT` typu:  
  
```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>
```  
  
 Wyświetla wizualizację `CStringT` obiekt w zmiennej oknie następująco:   
  
 ![Element CStringT DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "DBG_NATVIS_DisplayString_CStringT")  
  
 Dodawanie `StringView` elementu wskazuje debugera, że tę wartość można wyświetlić, wizualizacji tekst:  
  
```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  
  
 Zwróć uwagę, ikonę lupy wyświetlany obok wartość, poniżej. Wybieranie ikony uruchamia wizualizatora tekst, który będzie wyświetlany ciąg który `m_pszData` wskazuje.  
  
 ![CStringT danych za pomocą wizualizatora StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "DBG_NATVIS_StringView_CStringT")  
  
> [!NOTE]
>  Należy pamiętać, że wyrażenie `{m_pszData,su}` obejmuje specyfikatora formatu w C++ `su` do wyświetlania wartości w postaci ciągu Unicode. Zobacz [specyfikatory formatu w C++](../debugger/format-specifiers-in-cpp.md) Aby uzyskać więcej informacji.  
  
###  <a name="BKMK_Expand"></a> Rozwiń węzeł  
 `Expand` Węzeł służy do dostosowywania elementów podrzędnych zwizualizowanego typu, kiedy użytkownik rozwija go w zmiennych systemu windows. Przyjmuje listę węzły podrzędne, które definiują elementy podrzędne.  
  
 `Expand` Węzeł jest opcjonalne.  
  
-   Jeśli `Expand` węzła nie została określona w pozycji wizualizacji programu Visual Studio domyślnych reguł rozszerzenia są używane.  
  
-   Jeśli `Expand` węzeł został określony bez węzłów podrzędnych w nim, typ nie będzie można rozwijać w oknach debugera.  
  
####  <a name="BKMK_Item_expansion"></a> Element rozszerzenia  
 `Item` Element jest najprostsza i najbardziej typowych elementu do użycia w `Expand` węzła. `Item` Definiuje pojedynczym elemencie podrzędnym. Na przykład, załóżmy, że masz `CRect` klasy z `top`, `left`, `right`, i `bottom` jako jego pól i następujący wpis wizualizacji:  
  
```xml
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  
  
```  
  
 `CRect` Typu będą wyglądać następująco:  
  
 ![CRect o rozszerzeniu element elementu](../debugger/media/dbg_natvis_expand_item_crect1.png "DBG_NATVIS_Expand_Item_CRect1")  
  
 Wyrażenia określone w `Width` i `Height` elementy są oceniane i wyświetlane w kolumnie wartość. `[Raw View]` Węzeł jest tworzone automatycznie przez debuger zawsze, gdy jest używany niestandardowy rozszerzenia. Rozwiniętą na zrzucie ekranu powyżej, aby pokazać, jak raw widok obiektu różni się od jego wizualizacji. Rozszerzenia domyślnej programu Visual Studio tworzy poddrzewo dla klasy podstawowej i listy wszystkich danych elementów członkowskich klasy podstawowej jako elementy podrzędne.  
  
> [!NOTE]
>  Jeśli wyrażenie element elementu wskazuje typ złożony, `Item` sam węzeł jest rozwijania.  
  
####  <a name="BKMK_ArrayItems_expansion"></a> Rozszerzenia ArrayItems  
 Użyj `ArrayItems` węzeł, aby zinterpretować typu jako tablica i wyświetl jego poszczególne elementy debuger programu Visual Studio. Wizualizacja dla `std::vector` jest dobrym przykładem:  
  
```xml
<Type Name="std::vector&lt;*&gt;">  
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_Mylast - _Myfirst</Item>  
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>  
    <ArrayItems>  
      <Size>_Mylast - _Myfirst</Size>  
      <ValuePointer>_Myfirst</ValuePointer>  
    </ArrayItems>  
  </Expand>  
</Type>  
```  
  
 A `std::vector` pokazuje jego poszczególne elementy po rozwinięciu w oknie zmiennej:  
  
 ![przy użyciu rozszerzenia ArrayItems STD::Vector](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "DBG_NATVIS_Expand_ArrayItems_StdVector")  
  
 Co najmniej `ArrayItems` węzeł musi mieć:  
  
1.  A `Size` wyrażenia (który musi być liczbą całkowitą) dla debugera zrozumieć długości tablicy  
  
2.  A `ValuePointer` wyrażenie, które powinny wskazywać na pierwszym elementem (który musi być wskaźnikiem typu elementu, który nie jest `void*`).  
  
 Domyślna wartość dolna granica tablicy wynosi 0. Wartość można zastąpić, używając `LowerBound` elementu (przykłady można znaleźć w plikach .natvis dostarczanego z programem Visual Studio).  
  
 Można teraz używać `[]` operatora z `ArrayItems` rozszerzenia, na przykład `vector[i]`. [] — Operator może być używany z dowolnego wizualizacji jednowymiarowej tablicy, która używa `ArrayItems` lub `IndexListItems`, nawet jeśli sam typ nie zezwala na tego operatora (na przykład `CATLArray`).  
  
 Można również określić tablic wielowymiarowych. Debuger wymaga nieco więcej informacji do prawidłowego wyświetlenia elementów podrzędnych w takiej sytuacji:  
  
```xml
<Type Name="Concurrency::array&lt;*,*&gt;">  
  <DisplayString>extent = {_M_extent}</DisplayString>  
  <Expand>  
    <Item Name="extent">_M_extent</Item>  
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">  
      <Direction>Forward</Direction>  
      <Rank>$T2</Rank>  
      <Size>_M_extent._M_base[$i]</Size>  
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>  
    </ArrayItems>  
  </Expand>  
</Type>  
```  
  
 `Direction` Określa, czy tablica jest kolejności wierszy lub kolumn. `Rank` Określa rangę tablicy. `Size` Element akceptuje niejawne `$i` parametr, który zastępuje go przez indeks wymiaru, aby znaleźć długości tablicy w tym wymiarze. Na przykład w poprzednim przykładzie powyżej wyrażenie `_M_extent.M_base[0]` nadać długość wymiar 0th `_M_extent._M_base[1]` 1 i tak dalej.  
  
 Oto jak dwuwymiarowa `Concurrency::array` obiektu wygląda w debugerze:  
  
 ![Tablicą dwuwymiarową o rozszerzeniu ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "DBG_NATVIS_Expand_ArrayItems_2D")  
  
####  <a name="BKMK_IndexListItems_expansion"></a> Rozszerzenia IndexListItems  
 Można użyć `ArrayItems` rozszerzenia, tylko wtedy, gdy elementy tablicy są określone połączone ze sobą w pamięci. Debuger pobiera do następnego elementu po prostu zwiększając jego wskaźnik do bieżącego elementu. Do obsługi przypadkach konieczne do manipulowania indeks węzeł wartość `IndexListItems` węzły można użyć. Oto wizualizacji przy użyciu `IndexListItems` węzła:  
  
```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">  
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_M_vector._M_index</Item>  
    <IndexListItems>  
      <Size>_M_vector._M_index</Size>  
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>  
    </IndexListItems>  
  </Expand>  
</Type>  
```  
  
 Można teraz używać `[]` operatora z `IndexListItems` rozszerzenia, na przykład `vector[i]`. `[]` Operator może być używany z dowolnego wizualizacji jednowymiarowej tablicy, która używa `ArrayItems` lub `IndexListItems`, nawet jeśli sam typ nie zezwala na tego operatora (na przykład `CATLArray`).  
  
 Jedyną różnicą między `ArrayItems` i `IndexListItems` jest to, że `ValueNode` oczekuje pełne wyrażenie i<sup>th</sup> element z niejawnych `$i` parametru.  
  
####  <a name="BKMK_LinkedListItems_expansion"></a> Rozszerzenia LinkedListItems  
 Jeśli zwizualizowanego typu reprezentuje listy połączonej, Debuger można wyświetlić jego elementy podrzędne za pomocą `LinkedListItems` węzła. Poniżej przedstawiono wizualizację dla `CAtlList` typu za pomocą tej funkcji:  
  
```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">  
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>  
  <Expand>  
    <Item Name="Count">m_nElements</Item>  
    <LinkedListItems>  
      <Size>m_nElements</Size>  
      <HeadPointer>m_pHead</HeadPointer>  
      <NextPointer>m_pNext</NextPointer>  
      <ValueNode>m_element</ValueNode>  
    </LinkedListItems>  
  </Expand>  
</Type>  
```  
  
 `Size` Element odwołuje się do długość listy. `HeadPointer` wskazuje pierwszy element `NextPointer` odwołuje się do następnego elementu i `ValueNode` odnosi się do wartości elementu.  
  
-   `NextPointer` i `ValueNode` wyrażenia są obliczane w kontekście elementu węzła listy połączonej, a nie nadrzędnego typu listy. W powyższym przykładzie `CAtlList` ma `CNode` klasy (znalezione w `atlcoll.h`) reprezentujący węzeł listy połączonej. `m_pNext` i `m_element` pól tego `CNode` klasy, a nie `CAtlList` klasy.  
  
-   `ValueNode` Może być puste lub mieć `this` do odwoływania się do węzeł listy połączonej.  
  
#### <a name="customlistitems-expansion"></a>Rozszerzenia CustomListItems  
 `CustomListItems` Rozszerzenia umożliwia pisanie niestandardowej logiki do przechodzenia przez to struktura danych, takich jak tablica skrótów. Należy używać `CustomListItems` do wizualizacji danych można wyrazić za pomocą wyrażeń C++ jest struktury, w których wszystkie elementy potrzebne do oceny, ale jeszcze nie spełniają pleśnią dla `ArrayItems`, `TreeItems`, lub `LinkedListItems.`  
  
 Wizualizator dla CAtlMap jest doskonałym przykładem where `CustomListItems` jest odpowiedni.  
  
```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">  
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>  
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>  
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>  
    <Expand>  
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">  
        <Variable Name="iBucket" InitialValue="-1" />  
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />  
        <Variable Name="iBucketIncrement" InitialValue="-1" />  
  
        <Size>m_nElements</Size>  
        <Exec>pBucket = nullptr</Exec>  
        <Loop>  
          <If Condition="pBucket == nullptr">  
            <Exec>iBucket++</Exec>  
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>  
            <Break Condition="iBucketIncrement == -1" />  
            <Exec>iBucket += iBucketIncrement</Exec>  
            <Exec>pBucket = m_ppBins[iBucket]</Exec>  
          </If>  
          <Item>pBucket,na</Item>  
          <Exec>pBucket = pBucket->m_pNext</Exec>  
        </Loop>  
      </CustomListItems>  
    </Expand>  
</Type>  
```  

Można użyć `Exec` na wykonanie kodu wewnątrz `CustomListItems` rozszerzenia przy użyciu zmiennych i obiektów zdefiniowanych w `CustomListItems` rozszerzenia. Nie można użyć `Exec` można obliczyć wartości funkcji.

Można używać operatorów logicznych, operatorów arytmetycznych i operatory przypisania z `Exec`.

Obsługiwane są następujące funkcje wewnętrzne:

- `strlen, wcslen, strnlen, wcsnlen, strcmp, wcscmp, _stricmp, _strcmpi, _wcsicmp, strncmp, wcsncmp, _strnicmp, _wcsnicmp, memcmp, memicmp, wmemcmp, strchr, wcschr, memchr, wmemchr, strstr, wcsstr, __log2, __findNonNull`
- `GetLastError, TlsGetValue, DecodeHString, WindowsGetStringLen, WindowsGetStringRawBuffer, WindowsCompareStringOrdinal, RoInspectCapturedStackBackTrace, CoDecodeProxy, GetEnvBlockLength, DecodeWinRTRestrictedException, DynamicMemberLookup, DecodePointer, DynamicCast`
- `ConcurrencyArray_OperatorBracket_idx // Concurrency::array<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)`
- `ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `ConcurrencyArrayView_OperatorBracket_idx // Concurrency::array_view<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operator(int, int, ...)`
- `ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `Stdext_HashMap_Int_OperatorBracket_idx`
- `Std_UnorderedMap_Int_OperatorBracket_idx`
- `TreeTraverse_Init // Initializes a new tree traversal`
- `TreeTraverse_Next // Returns nodes in a tree`
- `TreeTraverse_Skip // Skips nodes in a pending tree traversal`
  
####  <a name="BKMK_TreeItems_expansion"></a> Rozszerzenia TreeItems  
 Jeśli zwizualizowanego typu reprezentuje drzewa, Debuger można zaprezentuje drzewa i wyświetlić jego elementy podrzędne za pomocą `TreeItems` węzła. Poniżej przedstawiono wizualizację dla `std::map` typu za pomocą tej funkcji:  
  
```xml
<Type Name="std::map&lt;*&gt;">  
  <DisplayString>{{size = {_Mysize}}}</DisplayString>  
  <Expand>  
    <Item Name="[size]">_Mysize</Item>  
    <Item Name="[comp]">comp</Item>  
    <TreeItems>  
      <Size>_Mysize</Size>  
      <HeadPointer>_Myhead->_Parent</HeadPointer>  
      <LeftPointer>_Left</LeftPointer>  
      <RightPointer>_Right</RightPointer>  
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>  
    </TreeItems>  
  </Expand>  
</Type>  
```  
  
 Składnia jest podobny do `LinkedListItems` węzła. `LeftPointer`, `RightPointer`, i `ValueNode` są obliczane w kontekście klasy węzła drzewa, i `ValueNode` może być puste lub mieć `this` do odwoływania się do samego węzła drzewa.  
  
####  <a name="BKMK_ExpandedItem_expansion"></a> Rozszerzenia ExpandedItem  
 `ExpandedItem` Element może być użyty do generowania widok podrzędny zagregowane przez wyświetlanie właściwości podstawowe elementy członkowskie klasy lub dane, tak jakby były dzieci zwizualizowanego typu. Określone wyrażenie jest obliczane i węzłów podrzędnych wyniku są dołączane do listy podrzędnych zwizualizowanego typu. Załóżmy na przykład, będziemy mieć typ wskaźnika inteligentnego `auto_ptr<vector<int>>`, które są zwykle wyświetlane jako:  
  
 ![automatycznie&#95;ptr&#60;wektor&#60;int&#62; &#62; domyślne rozszerzenie](../debugger/media/dbg_natvis_expand_expandeditem_default.png "DBG_NATVIS_Expand_ExpandedItem_Default")  
  
 Zobaczyć wartości wektora, należy przejść do szczegółów dwa poziomy w oknie zmiennej przechodzącej przez _Myptr elementu członkowskiego. Dodając `ExpandedItem` elementu, można wyeliminować `_Myptr` zmienną z hierarchii i bezpośrednio wyświetlanie elementów wektora::  
  
```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
```  
  
 ![automatycznie&#95;ptr&#60;wektor&#60;int&#62; &#62; rozszerzenia ExpandedItem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "DBG_NATVIS_Expand_ExpandedItem_Visualized")  
  
 Poniższy przykład przedstawia sposób agregacji właściwości z klasy podstawowej w klasie pochodnej. Załóżmy, że `CPanel` pochodną klasy `CFrameworkElement`. Zamiast powtarzające się właściwości, które pochodzą od podstawy `CFrameworkElement` klasy, `ExpandedItem` węzeł pozwala te właściwości, które mają być dołączane do listy podrzędnych `CPanel` klasy. **Nd** specyfikatora formatu, który wyłącza wizualizacji dopasowania dla klasy pochodnej, niezbędne jest w tym miejscu. W przeciwnym razie wyrażenie `*(CFrameworkElement*)this` powoduje, że `CPanel` wizualizacji ma zostać zastosowany ponownie, ponieważ wizualizacji domyślny typ reguły dopasowywania uważają, że najbardziej odpowiednie. Przy użyciu **nd** specyfikator formatu powoduje, że debuger do użycia wizualizacji klasy podstawowej lub rozszerzenia domyślną klasę podstawową klasę podstawową powodował wizualizacji.  
  
```xml
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  
```  
  
####  <a name="BKMK_Synthetic_Item_expansion"></a> Syntetyczne rozszerzenia elementu  
 Gdzie `ExpandedItem` element zapewnia bardziej płaski widok danych przez wyeliminowanie hierarchiami `Synthetic` węzeł będzie odwrotnie. Umożliwia tworzenie elementu podrzędnego sztuczne (to znaczy elementu podrzędnego nie będący wynikiem wyrażenia). Ten element podrzędny mogą zawierać elementy podrzędne własnych. W poniższym przykładzie wizualizację dla `Concurrency::array` wpisz używa `Synthetic` węzła w celu wyświetlania komunikatów diagnostycznych dla użytkownika:  
  
```xml
<Type Name="Concurrency::array&lt;*,*&gt;">  
  <DisplayString>extent = {_M_extent}</DisplayString>  
  <Expand>  
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>  
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">  
      <Rank>$T2</Rank>  
      <Size>_M_extent._M_base[$i]</Size>  
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>  
    </ArrayItems>  
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">  
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>  
    </Synthetic>  
  </Expand>  
</Type>  
  
```  
  
 ![CONCURRENCY::Array o rozszerzeniu syntetycznych element](../debugger/media/dbg_natvis_expand_synthetic.png "DBG_NATVIS_Expand_Synthetic")  
  
###  <a name="BKMK_HResult"></a> HResult  
 `HResult` Element umożliwia dostosowanie informacji, która jest wyświetlana dla wyniku HRESULT w oknach debugera. `HRValue` Element musi zawierać wartość HRESULT, która ma być dostosowane 32-bitowych. `HRDescription` Element zawiera informacje, które jest wyświetlane w debugerze.  
  
```  
  
<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  
  
###  <a name="BKMK_UIVisualizer"></a> UIVisualizer  
 A `UIVisualizer` element rejestruje graficznego wizualizatora wtyczki z debugera. Dodatek wizualizatora graficznego tworzy okno dialogowe lub inny interfejs do wyświetlenia w taki sposób, który jest jego typu danych zmiennej lub obiektu. Dodatek wizualizatora musi być utworzone jako [pakiet VSPackage](../extensibility/internals/vspackages.md) i musi zostać udostępniona usługa, która może być zużyte przez debuger. Pliku .natvis zawiera informacje rejestracyjne dotyczące dodatek plug-in, takie jak jego nazwa, identyfikator GUID usługi udostępniane i typy, które można wyświetlać wizualizację.  
  
 Oto przykład elementu UIVisualizer:  
  
```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"   
        Id="1" MenuName="Vector Visualizer"/>  
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"   
        Id="2" MenuName="List Visualizer"/>  
.  
.  
</AutoVisualizer>  
```  
  
 A `UIVisualizer` jest identyfikowany przez `ServiceId`  -  `Id` atrybutu pary. `ServiceId` Identyfikator GUID usługi udostępniane przez pakiet wizualizatora `Id` to unikatowy identyfikator, który może służyć do odróżnienia wizualizatorów, jeśli usługa zawiera więcej niż jeden wizualizatora. W powyższym przykładzie tę samą usługę wizualizatora zawiera dwa wizualizatorów.  
  
 `MenuName` Atrybut jest, co użytkownicy widzą jako nazwa wizualizatora po otwarciu listy rozwijanej obok ikonę lupy w oknach zmiennych debugera, na przykład:  
  
 ![Menu skrótów menu UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "DBG_NATVIS_VectorVisualizer")  
  
 Każdy typ zdefiniowany w pliku .natvis jawnie musi zawierać wizualizatorów interfejsu użytkownika, które można je wyświetlić. Debuger odpowiada odwołania wizualizatora we wpisach typ do dopasowania typy z zarejestrowanych wizualizatorów. Na przykład następujące wpisz hasło dla `std::vector` odwołuje się do UIVisualizer w naszym przykładzie.  
  
```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  
  
 Można zobaczyć przykład UIVisualizer w rozszerzeniu czujki obraz używany do wyświetlania map bitowych w pamięci: [ImageWatch](https://visualstudiogallery.msdn.microsoft.com/e682d542-7ef3-402c-b857-bbfba714f78d)  
  
### <a name="customvisualizer-element"></a>CustomVisualizer element  
 `CustomVisualizer` jest punktem rozszerzalności, który określa rozszerzenie VSIX, który może zapisać do kontrolowania wizualizację w kodu uruchamianego w programie Visual Studio. Aby uzyskać więcej informacji na temat pisania rozszerzenia VSIX, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md). Pisanie wizualizatora niestandardowego jest znacznie większą niż zapisywania definicji XML natvis, ale jest wolny od ograniczeń, o jaką natvis obsługuje lub nie obsługuje. Niestandardowe wizualizatory mają dostęp do pełnego zestawu debugera rozszerzalności interfejsów API, która może służyć do zapytania i zmodyfikować obiekt debugowany proces lub komunikowania się z innymi składnikami programu Visual Studio.  
  
 Można użyć `Condition`, `IncludeView`, i `ExcludeView` atrybutów w elementach CustomVisualizer.