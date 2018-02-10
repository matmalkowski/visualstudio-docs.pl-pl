---
title: "Wskazówki: Korzystanie z MSBuild | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8d268ac5eb479a680063eabe4d986657c3ec4013
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="walkthrough-using-msbuild"></a>Wskazówki: używanie programu MSBuild
MSBuild to platforma kompilacji dla firmy Microsoft i Visual Studio. W tym przewodniku przedstawiono bloków konstrukcyjnych programu MSBuild i pokazano, jak napisać, manipulowanie nimi oraz debugowania projektów MSBuild. Poznasz:  
  
-   Tworzenie i operowanie nimi pliku projektu.  
  
-   Sposób użycia właściwości kompilacji  
  
-   Jak używać elementów kompilacji.  
  
 W programie Visual Studio lub w oknie polecenia, można uruchomić programu MSBuild. W tym przewodniku można utworzyć pliku projektu MSBuild przy użyciu programu Visual Studio. Edytuj plik projektu w programie Visual Studio, a następnie użyj okno polecenia, aby skompilować projekt i przejrzeć wyniki.  
  
## <a name="creating-an-msbuild-project"></a>Tworzenie projektu programu MSBuild  
 System projektu programu Visual Studio jest oparty na MSBuild. Ułatwia to tworzenie nowego pliku projektu za pomocą programu Visual Studio. W tej sekcji utworzysz plik projektu programu Visual C#. Można zamiast tego utwórz plik projektu programu Visual Basic. W kontekście tego przewodnika różnica między plikami dwóch projektów jest niewielki.  
  
#### <a name="to-create-a-project-file"></a>Aby utworzyć plik projektu  
  
1.  Otwórz program Visual Studio.  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
3.  W **nowy projekt** wybierz pozycję Visual C# typ projektu, a następnie wybierz **aplikacji Windows Forms** szablonu. W **nazwa** wpisz `BuildApp`. Wprowadź **lokalizacji** dla rozwiązania, na przykład `D:\`. Zaakceptuj wartości domyślne dla **Utwórz katalog rozwiązania** (zaznaczone), **Dodaj do kontroli źródła** (nie jest zaznaczone), a **Nazwa rozwiązania** (`BuildApp`).  
  
     Kliknij przycisk **OK** można utworzyć pliku projektu.  
  
## <a name="examining-the-project-file"></a>Sprawdzenie pliku projektu  
 W poprzedniej sekcji Visual Studio jest używany do tworzenia pliku projektu Visual C#. Plik projektu jest reprezentowana w **Eksploratora rozwiązań** przez węzeł projektu o nazwie BuildApp. Edytor kodu programu Visual Studio można użyć do sprawdzenia pliku projektu.  
  
#### <a name="to-examine-the-project-file"></a>Aby sprawdzić pliku projektu  
  
1.  W **Eksploratora rozwiązań**, kliknij węzeł projektu BuildApp.  
  
2.  W **właściwości** przeglądarki, zwróć uwagę, że **pliku projektu** właściwość jest BuildApp.csproj. Wszystkie pliki projektu są posiadającymi nazwy z sufiksem "proj". Jeśli została utworzona projektu Visual Basic, nazwa pliku projektu jest BuildApp.vbproj.  
  
3.  Kliknij prawym przyciskiem myszy węzeł projektu, a następnie kliknij przycisk **Zwolnij projekt**.  
  
4.  Ponownie kliknij prawym przyciskiem myszy węzeł projektu, a następnie kliknij przycisk **Edytuj BuildApp.csproj**.  
  
     Plik projektu zostanie wyświetlony w edytorze kodu.  
  
## <a name="targets-and-tasks"></a>Obiektów docelowych i zadań  
 Pliki projektu są pliki w formacie XML z węzła głównego [projektu](../msbuild/project-element-msbuild.md).  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Project ToolsVersion="12.0" DefaultTargets="Build"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Należy określić przestrzeni nazw xmlns w elemencie projektu.  
  
 Pracy tworzenia aplikacji wykonuje się za pomocą [docelowej](../msbuild/target-element-msbuild.md) i [zadań](../msbuild/task-element-msbuild.md) elementów.  
  
-   Zadanie jest najmniejsza jednostka pracy, czyli "atom" kompilacji. Zadania są niezależne wykonywalnego składników, które mogą mieć wejścia i wyjścia. Nie ma żadnych zadań lub aktualnie odwołuje się określona w pliku projektu. Dodawanie zadań do pliku projektu w poniższych sekcjach. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md) tematu.  
  
-   Element docelowy jest nazwane sekwencji zadań. Istnieją dwa cele na końcu pliku projektu, które obecnie są ujęte w komentarz HTML: BeforeBuild i AfterBuild.  
  
    ```xml  
    <Target Name="BeforeBuild">  
    </Target>  
    <Target Name="AfterBuild">  
    </Target>  
    ```  
  
     Aby uzyskać więcej informacji, zobacz [cele](../msbuild/msbuild-targets.md) tematu.  
  
 Węzeł projektu jest opcjonalny defaulttargets — atrybut, który wybiera domyślnego obiektu docelowego do kompilacji, w tym przypadku kompilacji.  
  
```xml  
<Project ToolsVersion="12.0" DefaultTargets="Build" ...  
```  
  
 Nie zdefiniowano celu kompilacji w pliku projektu. Zamiast niego, zostaną zaimportowane z pliku Microsoft.CSharp.targets przy użyciu [importu](../msbuild/import-element-msbuild.md) elementu.  
  
```xml  
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
```  
  
 Zaimportowane pliki skutecznie są wstawiane do pliku projektu, wszędzie tam, gdzie występuje do nich.  
  
 MSBuild śledzi docelowe kompilacji i gwarantuje, że każdego obiektu docelowego jest wbudowana w nie więcej niż raz.  
  
## <a name="adding-a-target-and-a-task"></a>Dodanie elementu docelowego i zadania  
 Dodanie elementu docelowego do pliku projektu. Dodaj zadanie do docelowego, który komunikat do drukowania.  
  
#### <a name="to-add-a-target-and-a-task"></a>Aby dodać obiekt docelowy i zadania  
  
1.  Dodaj następujące wiersze do pliku projektu zaraz po instrukcję Import:  
  
    ```xml  
    <Target Name="HelloWorld">  
    </Target>  
    ```  
  
     Spowoduje to utworzenie obiektu docelowego o nazwie HelloWorld. Zwróć uwagę, że masz obsługę funkcji Intellisense podczas edycji pliku projektu.  
  
2.  Dodaj wiersze do docelowego HelloWorld tak, aby wynikową sekcję wygląda następująco:  
  
    ```xml  
    <Target Name="HelloWorld">  
      <Message Text="Hello"></Message>  <Message Text="World"></Message>  
    </Target>  
    ```  
  
3.  Zapisz plik projektu.  
  
 Komunikat — zadanie jest jednym z wielu zadań, które jest dostarczany z programu MSBuild. Aby uzyskać pełną listę dostępnych zadań i informacje o użyciu zobacz [odwołanie do zadania](../msbuild/msbuild-task-reference.md).  
  
 Zadanie wiadomości przyjmuje wartość ciągu atrybutu tekstu jako dane wejściowe i wyświetla je na urządzeniu danych wyjściowych. Element docelowy HelloWorld wykonuje zadanie wiadomości dwa razy: najpierw, aby wyświetlić tekst "Hello", a następnie, aby wyświetlić "World".  
  
## <a name="building-the-target"></a>Tworzenie obiektu docelowego  
 Uruchom program MSBuild z **wiersz polecenia programu Visual Studio** do tworzenia obiektu docelowego HelloWorld zdefiniowanych powyżej. Wybierz element docelowy, należy użyć przełącznika wiersza polecenia/TARGET lub /t.  
  
> [!NOTE]
>  Odnoszą się do **wiersz polecenia programu Visual Studio** jako **okno polecenia** w poniższych sekcjach.  
  
#### <a name="to-build-the-target"></a>Aby utworzyć element docelowy  
  
1.  Kliknij przycisk **Start**, następnie kliknij przycisk **wszystkie programy**. Zlokalizuj i kliknij przycisk **wiersz polecenia programu Visual Studio** w **programu Visual Studio Tools** folderu.  
  
2.  W oknie polecenia przejdź do folderu zawierającego plik projektu, w tym przypadku D:\BuildApp\BuildApp.  
  
3.  Uruchom program msbuild z /t:HelloWorld przełącznika polecenia. Wybiera i tworzy element docelowy HelloWorld:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Sprawdź dane wyjściowe w **okno polecenia**. Powinny pojawić się dwa wiersze "Hello" i "World":  
  
    ```  
    Hello  
    World  
    ```  
  
> [!NOTE]
>  Jeśli zamiast tego zobacz `The target "HelloWorld" does not exist in the project` , a następnie prawdopodobnie nie pamiętasz można zapisać pliku projektu w edytorze kodu. Zapisz plik i spróbuj ponownie.  
  
 Przez przemian edytora kodu i okna wiersza polecenia, można zmienić pliku projektu i szybko wyświetlić wyniki.  
  
> [!NOTE]
>  Po uruchomieniu programu msbuild bez przełącznika polecenia /t msbuild tworzy element docelowy określonego przez atrybut DefaultTarget elementu projektu, w tym przypadku "Kompilacji". Powoduje to skompilowanie aplikacji formularzy systemu Windows BuildApp.exe.  
  
## <a name="build-properties"></a>Właściwości kompilacji  
 Właściwości kompilacji są pary nazwa wartość, które prowadzą kompilacji. Kilka właściwości kompilacji są już zdefiniowane w górnej części pliku projektu:  
  
```xml  
<PropertyGroup>  
...  
  <ProductVersion>10.0.11107</ProductVersion>  
  <SchemaVersion>2.0</SchemaVersion>  
  <ProjectGuid>{30E3C9D5-FD86-4691-A331-80EA5BA7E571}</ProjectGuid>  
  <OutputType>WinExe</OutputType>  
...  
</PropertyGroup>  
```  
  
 Wszystkie właściwości są elementy podrzędne elementy PropertyGroup. Nazwa właściwości jest nazwa elementu podrzędnego, a wartość właściwości jest elementem tekst elementu podrzędnego. Na przykład  
  
```xml  
<TargetFrameworkVersion>v12.0</TargetFrameworkVersion>  
```  
  
 Definiuje właściwości o nazwie TargetFrameworkVersion nadanie mu wartość ciągu "v12.0".  
  
 Tworzenie właściwości mogą być zmieniane w dowolnym momencie. IF  
  
```xml  
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
```  
  
 pojawi się później w pliku projektu lub w pliku później zaimportowane w pliku projektu, a następnie TargetFrameworkVersion ma nową wartość "v3.5".  
  
## <a name="examining-a-property-value"></a>Badanie wartość właściwości  
 Aby uzyskać wartość właściwości, użyj następującej składni, gdzie PropertyName jest nazwą właściwości:  
  
```  
$(PropertyName)  
```  
  
 Należy użyć następującej składni, aby zbadać właściwości w pliku projektu.  
  
#### <a name="to-examine-a-property-value"></a>Aby sprawdzić wartość właściwości  
  
1.  W edytorze kodu Zastąp element docelowy HelloWorld ten kod:  
  
    ```xml  
    <Target Name="HelloWorld">  
      <Message Text="Configuration is $(Configuration)" />  
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />  
    </Target>  
    ```  
  
2.  Zapisz plik projektu.  
  
3.  Z **okno polecenia**, wprowadź i wykonać ten wiersz:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Zbadaj dane wyjściowe. Powinny pojawić się następujące dwa wiersze (.NET Framework w wersji może różnić się):  
  
    ```  
    Configuration is Debug  
    MSBuildToolsPath is C:\Program Files\MSBuild\12.0\bin  
    ```  
  
> [!NOTE]
>  Jeśli nie widzisz tych wierszach następnie prawdopodobnie pamiętasz można zapisać pliku projektu w edytorze kodu. Zapisz plik i spróbuj ponownie.  
  
### <a name="conditional-properties"></a>Właściwości warunkowych  
 Zdefiniowano wiele właściwości, takie jak konfiguracja warunkowo, oznacza to, pojawi się atrybut Condition w elemencie właściwości. Właściwości warunkowych są zdefiniowane lub ponownie zdefiniować tylko wtedy, gdy warunek jest wartość "true". Należy pamiętać, że niezdefiniowane właściwości są podane domyślna wartość pustego ciągu. Na przykład  
  
```xml  
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
```  
  
 oznacza, że "Jeśli jeszcze nie zdefiniowano właściwości konfiguracji, zdefiniuj ją i nadaj mu wartość"Debugowanie"".  
  
 Prawie wszystkie elementy programu MSBuild mogą mieć atrybut warunku. Aby poznać informacje przy użyciu atrybutu warunku, zobacz [warunki](../msbuild/msbuild-conditions.md).  
  
### <a name="reserved-properties"></a>Właściwości zastrzeżone  
 MSBuild rezerwuje niektórych nazw właściwości do przechowywania informacji o pliku projektu i plików binarnych programu MSBuild. MSBuildToolsPath jest przykładem zarezerwowanej właściwości. Właściwości zastrzeżone jest przywoływana za pomocą notacji $, podobnie jak inne właściwości. Aby uzyskać więcej informacji, zobacz [porady: odwołanie do nazwy lub lokalizacji pliku projektu](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) i [MSBuild zarezerwowane i dobrze znane właściwości](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
### <a name="environment-variables"></a>Zmienne środowiskowe  
 Możesz odwoływać się zmienne środowiskowe w plikach projektu taki sam sposób, jak zbudować właściwości. Na przykład aby użyć zmiennej środowiskowej PATH w pliku projektu, należy użyć $(ścieżka). Jeśli projekt nie zawiera definicji właściwości, która ma taką samą nazwę jak zmiennej środowiskowej, właściwości projektu zastępuje wartość zmiennej środowiskowej. Aby uzyskać więcej informacji, zobacz [porady: Użycie zmiennych środowiskowych w kompilacji](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
## <a name="setting-properties-from-the-command-line"></a>Ustawianie właściwości wiersza polecenia  
 Właściwości mogą być zdefiniowane w wierszu polecenia, za pomocą przełącznika wiersza polecenia /property lub /p. Wartości właściwości odebranych z wiersza polecenia zastąpić wartości właściwości ustawione w projekcie zmiennych plików i środowiska.  
  
#### <a name="to-set-a-property-value-from-the-command-line"></a>Aby ustawić wartość właściwości z wiersza polecenia  
  
1.  Z **okno polecenia**, wprowadź i wykonać ten wiersz:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld /p:Configuration=Release  
    ```  
  
2.  Zbadaj dane wyjściowe. Powinien zostać wyświetlony ten wiersz:  
  
    ```  
    Configuration is Release.  
    ```  
  
 MSBuild tworzy właściwości konfiguracji i nadaje mu wartość "Wersja".  
  
## <a name="special-characters"></a>Znaki specjalne  
 Niektóre znaki mają specjalne znaczenie w plikach projektu programu MSBuild. Przykładami takich znaków średnikami (;) i gwiazdki (*). Aby można było używać tych znaków specjalnych jako literał w pliku projektu, muszą być one określone za pomocą składni xx %, gdzie xx reprezentuje wartość szesnastkową ASCII znaku.  
  
 Zmienianie zadania komunikat do wyświetlenia wartości właściwości konfiguracji z znaków specjalnych, aby był bardziej czytelny.  
  
#### <a name="to-use-special-characters-in-the-message-task"></a>Aby użyć znaków specjalnych w zadaniu wiadomości  
  
1.  W edytorze kodu Zastąp obu zadań komunikat ten wiersz:  
  
    ```xml  
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />  
    ```  
  
2.  Zapisz plik projektu.  
  
3.  Z **okno polecenia**, wprowadź i wykonać ten wiersz:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Zbadaj dane wyjściowe. Powinien zostać wyświetlony ten wiersz:  
  
    ```  
    $(Configuration) is "Debug"  
    ```  
  
 Aby uzyskać więcej informacji, zobacz [znaki specjalne MSBuild](../msbuild/msbuild-special-characters.md).  
  
## <a name="build-items"></a>Tworzenie elementów  
 Element jest informacji, zwykle nazwę pliku, które jest używane jako dane wejściowe do system kompilacji. Na przykład kolekcję elementów reprezentujących pliki źródłowe mogą być przekazywane do zadania o nazwie kompilacji do kompilowania ich do zestawu.  
  
 Wszystkie elementy są elementami podrzędnymi ItemGroup elementów. Nazwa elementu jest nazwa elementu podrzędnego, a wartość elementu jest wartość atrybutu Include elementu podrzędnego. Wartości elementów o takiej samej nazwie są zbierane w typów elementów o takiej nazwie.  Na przykład  
  
```xml  
<ItemGroup>  
    <Compile Include="Program.cs" />  
    <Compile Include="Properties\AssemblyInfo.cs" />  
</ItemGroup>  
```  
  
 definiuje grupę elementu zawierającego dwa elementy. Typ elementu kompilacji ma dwie wartości: "Program.cs" i "Properties\AssemblyInfo.cs".  
  
 Poniższy kod tworzy ten sam typ elementu przez zadeklarowanie oba pliki w jednym atrybucie Include, oddzielone średnikami.  
  
```xml  
<ItemGroup>  
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />  
</ItemGroup>  
```  
  
 Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).  
  
> [!NOTE]
>  Ścieżki plików są względem folder zawierający plik projektu programu MSBuild.  
  
## <a name="examining-item-type-values"></a>Badanie elementów typu wartości  
 Aby uzyskać wartości typu elementu, użyj następującej składni, gdzie ItemType jest nazwą typu elementu:  
  
```  
@(ItemType)  
```  
  
 Należy użyć następującej składni, aby sprawdzić typ elementu kompilacji w pliku projektu.  
  
#### <a name="to-examine-item-type-values"></a>Aby sprawdzić wartości typu elementu  
  
1.  W edytorze kodu Zastąp zadanie docelowe HelloWorld ten kod:  
  
    ```xml  
    <Target Name="HelloWorld">  
      <Message Text="Compile item type contains @(Compile)" />  
    </Target>  
    ```  
  
2.  Zapisz plik projektu.  
  
3.  Z **okno polecenia**, wprowadź i wykonać ten wiersz:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Zbadaj dane wyjściowe. Powinien zostać wyświetlony ten długi wiersz:  
  
    ```  
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs  
    ```  
  
 Wartości typu elementu są rozdzielone średnikami domyślnie.  
  
 Aby zmienić separator typ elementu, użyj następującej składni, gdzie ItemType jest typ elementu, a separatorem jest co najmniej jeden znak oddzielający ciąg:  
  
```  
@(ItemType, Separator)  
```  
  
 Zmień zadanie wiadomości karetki i wiersz źródła danych (% 0A %0 D) do wyświetlenia kompilacji elementów, każde w oddzielnym wierszu.  
  
#### <a name="to-display-item-type-values-one-per-line"></a>Aby wyświetlić typ elementu wartości, każde w oddzielnym wierszu  
  
1.  W edytorze kodu Zastąp zadanie wiadomości ten wiersz:  
  
    ```xml  
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />  
    ```  
  
2.  Zapisz plik projektu.  
  
3.  Z **okno polecenia**, wprowadź i wykonać ten wiersz:  
  
     `msbuild buildapp.csproj /t:HelloWorld`  
  
4.  Zbadaj dane wyjściowe. Powinny pojawić się następujące wiersze:  
  
    ```  
    Compile item type contains Form1.cs  
    Form1.Designer.cs  
    Program.cs  
    Properties\AssemblyInfo.cs  
    Properties\Resources.Designer.cs  
    Properties\Settings.Designer.cs  
    ```  
  
### <a name="include-exclude-and-wildcards"></a>Obejmują Wyklucz i symboli wieloznacznych  
 Można użyć symboli wieloznacznych "*","\*\*", oraz "?" w atrybucie Include do dodawania elementów do typu elementu. Na przykład  
  
```xml  
<Photos Include="images\*.jpeg" />  
```  
  
 dodaje wszystkie pliki z rozszerzeniem "JPEG" w folderze Obrazy do typu elementu zdjęć, podczas gdy  
  
```xml  
<Photos Include="images\**.jpeg" />  
```  
  
 dodaje wszystkie pliki z rozszerzeniem "JPEG" w folderze obrazów i wszystkie jego podfoldery do typu elementu zdjęcia. Aby uzyskać więcej przykładów, zobacz [porady: Wybieranie plików do kompilacji](../msbuild/how-to-select-the-files-to-build.md).  
  
 Zwróć uwagę, że podaną elementów dodanych do typu elementu. Na przykład  
  
```xml  
<Photos Include="images\*.jpeg" />  
<Photos Include="images\*.gif" />  
```  
  
 Tworzy typ elementu o nazwie fotografii zawierający wszystkie pliki w folderze obrazu z rozszerzeniem "JPEG" lub "GIF". Jest to równoważne następujący wiersz:  
  
```xml  
<Photos Include="images\*.jpeg;images\*.gif" />  
```  
  
 Element można wykluczyć z atrybutem Wyklucz typ elementu. Na przykład  
  
```xml  
<Compile Include="*.cs" Exclude="*Designer*">  
```  
  
 dodaje wszystkie pliki z rozszerzeniem"CS" do elementu kompilacji typ, z wyjątkiem plików, których nazwy zawierają ciąg "Designer". Aby uzyskać więcej przykładów, zobacz [porady: wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md).  
  
 Atrybut wykluczania dotyczy tylko dodać za pomocą atrybutu Include w elemencie elementu, który zawiera oba te elementy. Na przykład  
  
```xml  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 nie spowoduje wykluczenie pliku z pliku Form1.cs, która została dodana w elemencie poprzedniego elementu.  
  
##### <a name="to-include-and-exclude-items"></a>Aby uwzględniać i wykluczać elementy  
  
1.  W edytorze kodu Zastąp zadanie wiadomości ten wiersz:  
  
    ```xml  
    <Message Text="XFiles item type contains @(XFiles)" />  
    ```  
  
2.  Dodaj tę grupę elementu zaraz po elemencie importu:  
  
    ```xml  
    <ItemGroup>  
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />  
    </ItemGroup>  
    ```  
  
3.  Zapisz plik projektu.  
  
4.  Z **okno polecenia**, wprowadź i wykonać ten wiersz:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
5.  Zbadaj dane wyjściowe. Powinien zostać wyświetlony ten wiersz:  
  
    ```  
    XFiles item type contains Form1.cs;Program.cs;Properties/Resources.resx  
    ```  
  
## <a name="item-metadata"></a>Metadane elementu  
 Elementy mogą zawierać metadane oprócz informacji zebranych od atrybuty Include oraz Exclude. Te metadane mogą posłużyć zadania, które wymagają więcej informacji na temat elementów niż tylko wartości elementu.  
  
 Metadane elementu jest zadeklarowany w pliku projektu, tworząc element o nazwie metadanych jako element podrzędny elementu. Element może mieć zero lub więcej wartości metadanych. Na przykład następujący element CSFile ma metadane kultury o wartości "Fr":  
  
```xml  
<ItemGroup>  
    <CSFile Include="main.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Aby uzyskać wartość metadanych typu elementu, należy użyć następującej składni, gdzie ItemType jest nazwa typu elementu, a MetaDataName Nazwa metadanych:  
  
```  
%(ItemType.MetaDataName)  
```  
  
#### <a name="to-examine-item-metadata"></a>Aby zbadać metadanych elementu  
  
1.  W edytorze kodu Zastąp zadanie wiadomości ten wiersz:  
  
    ```xml  
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />  
    ```  
  
2.  Zapisz plik projektu.  
  
3.  Z **okno polecenia**, wprowadź i wykonać ten wiersz:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Zbadaj dane wyjściowe. Powinny pojawić się następujące wiersze:  
  
    ```  
    Compile.DependentUpon:  
    Compile.DependentUpon: Form1.cs  
    Compile.DependentUpon: Resources.resx  
    Compile.DependentUpon: Settings.settings  
    ```  
  
 Zwróć uwagę, jak frazy "Compile.DependentUpon" pojawia się wiele razy. Korzystanie z metadanych przy użyciu tej składni w elemencie docelowym powoduje, że "przetwarzanie wsadowe". Przetwarzanie wsadowe oznacza, że zadania w docelowym są wykonywane raz dla każdej wartości unikatowe metadane. To jest odpowiednikiem skryptu MSBuild typowe "dla pętli" programowania konstrukcji. Aby uzyskać więcej informacji, zobacz [wsadowe](../msbuild/msbuild-batching.md).  
  
### <a name="well-known-metadata"></a>Metadane dobrze znanego  
 Zawsze, gdy element zostanie dodany do listy elementów, ten element jest przypisany niektóre metadane dobrze znanego. Na przykład %(Filename) zwraca nazwę pliku dowolnego elementu. Aby uzyskać pełną listę znanych metadanych, zobacz [metadane dobrze znanego elementu](../msbuild/msbuild-well-known-item-metadata.md).  
  
##### <a name="to-examine-well-known-metadata"></a>Aby zbadać metadane dobrze znanego  
  
1.  W edytorze kodu Zastąp zadanie wiadomości ten wiersz:  
  
    ```xml  
    <Message Text="Compile Filename: %(Compile.Filename)" />  
    ```  
  
2.  Zapisz plik projektu.  
  
3.  Z **okno polecenia**, wprowadź i wykonać ten wiersz:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Zbadaj dane wyjściowe. Powinny pojawić się następujące wiersze:  
  
    ```  
    Compile Filename: Form1  
    Compile Filename: Form1.Designer  
    Compile Filename: Program  
    Compile Filename: AssemblyInfo  
    Compile Filename: Resources.Designer  
    Compile Filename: Settings.Designer  
    ```  
  
 Porównując dwóch przykładach widać, że podczas nie każdy element w typie elementu kompilacji ma DependentUpon metadanych, wszystkie elementy ma dobrze znanego metadanych Filename.  
  
### <a name="metadata-transformations"></a>Przekształcenia metadanych  
 Element listy może zostać zamieniony na nowy element listy. Aby przekształcić listy elementów, użyj następującej składni, gdzie ItemType jest nazwa typu elementu, a MetadataName Nazwa metadanych:  
  
```  
@(ItemType -> '%(MetadataName)')  
```  
  
 Na przykład listy elementów plików źródłowych może służyć do kolekcji przy użyciu wyrażeń, takich jak pliki obiektu `@(SourceFiles -> '%(Filename).obj')`. Aby uzyskać więcej informacji, zobacz [przekształca](../msbuild/msbuild-transforms.md).  
  
##### <a name="to-transform-items-using-metadata"></a>Aby przekształcić elementów przy użyciu metadanych  
  
1.  W edytorze kodu Zastąp zadanie wiadomości ten wiersz:  
  
    ```xml  
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />  
    ```  
  
2.  Zapisz plik projektu.  
  
3.  Z **okno polecenia**, wprowadź i wykonać ten wiersz:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Zbadaj dane wyjściowe. Powinien zostać wyświetlony ten wiersz:  
  
    ```  
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak  
    ```  
  
 Należy zauważyć, że metadane wyrażone w tej składni nie powoduje przetwarzania wsadowego.  
  
## <a name="whats-next"></a>Co to jest dalej?  
 Aby dowiedzieć się, jak utworzyć jeden krok pliku prostego projektu w czasie, wypróbowanie [wskazówki: Tworzenie pliku projektu MSBuild od początku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).  
  
## <a name="see-also"></a>Zobacz też
[Przegląd MSBuild](../msbuild/msbuild.md)  
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)
