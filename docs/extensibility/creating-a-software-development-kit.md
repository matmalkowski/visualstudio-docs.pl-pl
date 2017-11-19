---
title: Tworzenie zestawu Software Development Kit | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: "54"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a301085cd00e20d5c4e931ac144e454718ad152
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-software-development-kit"></a>Tworzenie zestawu Software Development Kit
Zestaw software development kit (SDK) to kolekcja interfejsów API, które można odwoływać się do pojedynczego elementu w programie Visual Studio. **Menedżera odwołań** okno dialogowe wyświetla wszystkie zestawy SDK, które mają zastosowanie do projektu. Po dodaniu zestawu SDK do projektu, interfejsy API są dostępne w programie Visual Studio.  
  
 Istnieją dwa typy zestawów SDK:  
  
-   Zestaw SDK platformy są wymagane składniki do tworzenia aplikacji dla platformy. Na przykład [!INCLUDE[win81](../debugger/includes/win81_md.md)] zestawu SDK jest wymagany do opracowywania [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji.  
  
-   Zestawy SDK rozszerzeń są składniki opcjonalne rozszerzenie platformy, które nie są wymagane do tworzenia aplikacji dla tej platformy.  
  
 W poniższych sekcjach opisano ogólne infrastruktury zestawów SDK oraz sposobu tworzenia zestawu SDK platformy i rozszerzenie SDK.  
  
-   [Zestaw SDK platformy](#PlatformSDKs)  
  
-   [Rozszerzenia SDK](#ExtensionSDKs)  
  
##  <a name="PlatformSDKs"></a>Zestaw SDK platformy  
 Zestaw SDK platformy są wymagane do opracowywania aplikacji dla platformy. Na przykład [!INCLUDE[win81](../debugger/includes/win81_md.md)] zestawu SDK jest wymagany do opracowywania aplikacji dla [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
### <a name="installation"></a>Instalacja  
 Wszystkie platformy zestawów SDK zostanie zainstalowana w kluczu HKLM\Software\Microsoft\Microsoft zestawów SDK\\\v [TPI] [TPV]\\ @InstallationFolder = [folderu głównego zestawu SDK]. W związku z tym [!INCLUDE[win81](../debugger/includes/win81_md.md)] w kluczu HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1 jest zainstalowany zestaw SDK.  
  
### <a name="layout"></a>Układ  
 Zestaw SDK platformy mają następujący układ:  
  
```  
\[InstallationFolder root]  
            SDKManifest.xml  
            \References  
                  \[config]  
                        \[arch]  
            \DesignTime  
                  \[config]  
                        \[arch]  
```  
  
|Węzeł|Opis|  
|----------|-----------------|  
|Folder Odwołania|Zawiera pliki binarne, zawierające interfejsów API, który można zakodować przed. Te mogą obejmować plików metadanych systemu Windows (WinMD) lub zestawów.|  
|Folder czasu projektowania|Zawiera pliki, które są wymagane tylko w czasie wstępnie przygotowany-run/debugowania. Te mogą obejmować dokumentów XML, bibliotek, nagłówki, pliki binarne czasu projektowania przybornika, MSBuild artefakty i tak dalej<br /><br /> Dokumenty XML najlepiej, jeśli zostanie umieszczony w folderze \DesignTime, ale dokumentów XML dla odwołań będą w dalszym ciągu umieszczone obok pliku odwołanie w Visual Studio. Na przykład dokumentów XML \References odwołanie\\[config]\\[arch]\sample.dll będzie \References\\[config]\\[arch]\sample.xml i zlokalizowanej wersji tego dokumentu będą \References\\[config]\\[arch]\\[locale]\sample.xml.|  
|Folder konfiguracji|Może istnieć tylko trzy foldery: debugowania, detalicznych i CommonConfiguration. Autorzy zestawu SDK można umieścić swoich plików w obszarze CommonConfiguration, jeśli ten sam zestaw SDK plików powinny być używane niezależnie od ustawień konfiguracji klienta SDK będzie obowiązywać.|  
|Architektura folderu|Obsługiwana architektura folderu może istnieć. Program Visual Studio obsługuje następujące architektur: x86, x64, ARM i neutral. Uwaga: Win32 mapuje x86 oraz AnyCPU mapuje neutralne.<br /><br /> Program MSBuild wyszukuje tylko w obszarze \CommonConfiguration\neutral zestawów SDK platformy.|  
|SDKManifest.xml|Ten plik zawiera opis sposobu Visual Studio powinien korzystać z zestawu SDK. Szukaj w manifeście zestawu SDK dla [!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **Nazwa wyświetlana:** wartość, która wyświetla przeglądarki obiektów na liście przeglądania.<br /><br /> **PlatformIdentity:** istnienie ten atrybut informuje program Visual Studio i MSBuild czy zestaw SDK jest zestawu SDK platformy i nie można skopiować odwołania dodane z niego lokalnie.<br /><br /> **TargetFramework:** ten atrybut jest używany przez program Visual Studio, aby upewnić się, że tylko projektów przeznaczonych takie same struktury określony w wartości tego atrybutu mogą korzystać z zestawu SDK.<br /><br /> **MinVSVersion:** ten atrybut jest używany przez program Visual Studio korzystać tylko z zestawów SDK, które mają zastosowanie do niej.<br /><br /> **Odwołanie:** ten atrybut musi mieć określony tylko te odwołania, zawierające formanty. Aby uzyskać informacje o sposobie określania, czy odwołanie zawiera formanty zobacz poniżej.|  
  
##  <a name="ExtensionSDKs"></a>Rozszerzenia SDK  
 W poniższych sekcjach opisano, co należy zrobić, aby wdrożyć rozszerzenie SDK.  
  
### <a name="installation"></a>Instalacja  
 Zestawy SDK rozszerzeń można zainstalować dla określonego użytkownika lub dla wszystkich użytkowników bez określania klucza rejestru. Aby zainstalować zestaw SDK dla wszystkich użytkowników, należy użyć następującej ścieżki:  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Aby przeprowadzić instalację specyficzne dla użytkownika należy użyć następującej ścieżki:  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Jeśli chcesz użyć w innej lokalizacji, wykonaj jedną z następujących operacji:  
  
1.  Określ wartość w kluczu rejestru:  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     i dodać podklucz (ustawienie domyślne), który ma wartość `<path to SDK><SDKName><SDKVersion>`.  
  
2.  Dodaj właściwość MSBuild `SDKReferenceDirectoryRoot` do pliku projektu. Wartość tej właściwości jest częściowej średnikami lista katalogów, w których znajdują się zestawy SDK rozszerzeń ma dotyczyć odwołanie.  
  
### <a name="installation-layout"></a>Układ instalacji  
 Zestawy SDK rozszerzeń są następujące układu instalacji:  
  
```  
\<ExtensionSDKs root>  
           \<SDKName>  
                 \<SDKVersion>  
                        SDKManifest.xml  
                        \References  
                              \<config>  
                                    \<arch>  
                        \Redist  
                              \<config>  
                                    \<arch>  
                        \DesignTime  
                               \<config>  
                                     \<arch>  
  
```  
  
1.  \\< Nazwazestawusdk\>\\< Wersjazestawusdk\>: Nazwa i wersja rozszerzenia SDK pochodzi od odpowiedniej nazwy folderów w ścieżce do folderu głównego zestawu SDK. Program MSBuild używa tej tożsamości można znaleźć zestawu SDK na dysku, a program Visual Studio Wyświetla tej tożsamości w **właściwości** okna i **Menedżera odwołań** okna dialogowego.  
  
2.  Folder odwołań: pliki binarne, które zawierają interfejsy API. Mogą to być plików metadanych systemu Windows (WinMD) lub zestawów.  
  
3.  Folderu redystrybucyjnego: pliki, które są wymagane przez środowisko uruchomieniowe/debugowania i należy pobrać opakowane w ramach aplikacji użytkownika. Wszystkie pliki binarne ma zostać umieszczony pod \redist\\< config\>\\< arch\>, i nazwami plików binarnych powinna mieć następujący format dla zapewnienia unikatowości:  **\<firmy >.\< produktu >. \<cel >. \<rozszerzenia >**. Na przykład Microsoft.Cpp.Build.dll. Wszystkie pliki z nazwami, które może dojść do kolizji z nazwami plików od innych zestawów SDK (na przykład pliki javascript, css, Lo, xaml, png i jpg) powinny być umieszczone pod \redist\\< config\>\\< arch\> \\< nazwazestawusdk\>\ Określa, z wyjątkiem plików, które są skojarzone z XAML. Pliki te powinny być umieszczone pod \redist\\< config\>\\< arch\>\\< NazwaSkładnika\>\\.  
  
4.  Folder czasu projektowania: pliki, które są potrzebne w tylko wstępnie przygotowany-run/profilowanie czasu i nie umieszczone w ramach aplikacji użytkownika. Mogą to być dokumenty XML, bibliotek, nagłówki, pliki binarne czasu projektowania przybornika, MSBuild artefakty i tak dalej. Żadnych zestawu SDK, który jest przeznaczony do użycia przez natywnego projektu musi mieć *Nazwazestawusdk*.props pliku. Poniżej przedstawiono przykład tego typu pliku.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>  
        <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>  
        <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>  
        <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>  
        <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>  
        <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>  
        <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>  
      </PropertyGroup>  
    </Project>  
  
    ```  
  
     Dokumenty XML odwołania są umieszczane obok pliku odwołania. Na przykład odwołania dokumentu XML **\References\\< config\>\\< arch\>\sample.dll** zestaw jest **\References\\ < config\>\\< arch\>\sample.xml**, i zlokalizowanej wersji tego dokumentu jest **\References\\< config\>\\< Architektura\>\\< ustawień regionalnych\>\sample.xml**.  
  
5.  Folder konfiguracji: trzy podfoldery: debugowania, detaliczna i CommonConfiguration. Autorzy zestawu SDK można umieścić swoich plików w obszarze CommonConfiguration, gdy powinny być używane ten sam zestaw SDK plików niezależnie od konfiguracji objęci konsumenta zestawu SDK.  
  
6.  Architektura folderu: obsługiwane są następujące architektur: x86, x64, ARM i neutral. Mapuje Win32 x86 oraz AnyCPU mapuje neutralne.  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 Ten plik zawiera opis sposobu Visual Studio powinien korzystać z zestawu SDK. Poniżej przedstawiono przykład.  
  
```  
<FileList>  
DisplayName = "My SDK"  
ProductFamilyName = "My SDKs"  
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"  
MinVSVersion = "14.0"  
MaxPlatformVersion = "8.1"  
AppliesTo = "WindowsAppContainer + WindowsXAML"  
SupportPrefer32Bit = "True"  
SupportedArchitectures = "x86;x64;ARM"  
SupportsMultipleVersions = "Error"  
CopyRedistToSubDirectory = "."  
DependsOn = "SDKB, version=2.0"  
MoreInfo = "http://msdn.microsoft.com/MySDK">  
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">  
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />  
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />  
<ToolboxItems VSCategory = "Toolbox.Default" />  
</File>  
</FileList>  
```  
  
 Poniższa lista zawiera elementy pliku.  
  
1.  Nazwa wyświetlana: wartość, która jest wyświetlana w Menedżera odwołań, Eksploratora rozwiązań przeglądarki obiektów i innych lokalizacjach w interfejsie użytkownika dla programu Visual Studio.  
  
2.  ProductFamilyName: Ogólną SDK nazwę produktu. Na przykład [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK nosi nazwę "Microsoft.WinJS.1.0" i "Microsoft.WinJS.2.0", które należą do tej samej rodziny rodziny produktów SDK "Microsoft.WinJS". Ten atrybut umożliwia Visual Studio i MSBuild tego połączenia. Jeśli ten atrybut nie istnieje, nazwa zestawu SDK jest używana jako nazwa rodziny produktów.  
  
3.  FrameworkIdentity: Określa zależności na co najmniej jedną bibliotekę składników systemu Windows, którego wartość tego atrybutu jest umieszczany w manifeście aplikacji korzystanie. Ten atrybut ma zastosowanie tylko do bibliotek składników systemu Windows.  
  
4.  TargetFramework: Określa zestawy SDK, które są dostępne w Menedżerze odwołania i przybornika. Jest to rozdzielana średnikami lista monikerów framework docelowy, na przykład ".NET Framework, wersja = v2.0; .NET Framework, wersja = v4.5.1". Jeśli określono kilka wersji platformy docelowej, Menedżera odwołań używa Najniższa wersja określonego celu ich filtrowania. Na przykład jeśli ".NET Framework, wersja = v2.0; .NET Framework, wersja = v4.5.1" jest określony, będzie używać Menedżera odwołań ".NET Framework w wersji = v2.0". Jeśli określono profil platformy docelowej określonej, tylko ten profil będzie używany przez Menedżera odwołań celu ich filtrowania. Na przykład, gdy "Silverlight, wersja = v4.0, profil = WindowsPhone" jest określony, filtry Menedżera odwołań tylko Windows Phone w profilu; Projekt przeznaczony dla full Silverlight 4.0 Framework nie ma wglądu w Menedżerze odwołanie do zestawu SDK.  
  
5.  MinVSVersion: minimalną wersją programu Visual Studio.  
  
6.  MaxPlatformVerson: Maksymalna docelową wersję platformy należy określić wersji platformy, na których zestawu SDK rozszerzenia nie będą działać. Na przykład v11.0 Microsoft Visual C++ Runtime Package ma być utworzone odwołanie, tylko w projektach systemu Windows 8. W związku z tym MaxPlatformVersion projektu systemu Windows 8 jest 8.0. Oznacza to, że Menedżera odwołań odfiltrowuje Microsoft Visual C++ Runtime Package dla projektu Windows 8.1 i MSBuild zgłasza błąd podczas [!INCLUDE[win81](../debugger/includes/win81_md.md)] go odwołań w projekcie. Uwaga: ten element jest obsługiwany w systemie [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)].  
  
7.  Element AppliesTo: Określa zestawy SDK, które są dostępne w Menedżerze odwołanie przez określenie odpowiednich typów projektów programu Visual Studio. Dziewięć wartości są rozpoznawane: WindowsAppContainer, VisualC VB, CSharp, WindowsXAML, JavaScript, zarządzane i natywne. Można użyć autorem zestawu SDK i ("+"), lub ("&#124;"), nie ("!") operatory, aby określić dokładnie zakres typów projektów, które mają zastosowanie do zestawu SDK.  
  
     WindowsAppContainer identyfikuje projektów dla [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji.  
  
8.  SupportPrefer32Bit: Obsługiwane wartości to "True" i "False". Wartość domyślna to "True". Jeśli wartość jest ustawiona na wartość "False", MSBuild zwraca błąd dla [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] projektów (lub ostrzegawczy dla projektów pulpitu) Jeśli projekt, który odwołuje się do zestawu SDK ma Prefer32Bit włączone. Aby uzyskać więcej informacji o Prefer32Bit, zobacz [strona kompilacji, Projektant projektu (C#)](../ide/reference/build-page-project-designer-csharp.md) lub [strona kompilowania, Projektant projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  
  
9. SupportedArchitectures: podzielona średnikami lista architektur obsługiwanych przez zestaw SDK. MSBuild wyświetli ostrzeżenie, jeśli docelowa architektura zestawu SDK w projekcie odbierającą nie jest obsługiwany. Jeśli ten atrybut nie jest określony, program MSBuild nigdy nie wyświetla tego typu Ostrzeżenie.  
  
10. SupportsMultipleVersions: Jeśli ten atrybut ma ustawioną **błąd** lub **ostrzeżenie**, MSBuild wskazuje, że projekt nie może odwoływać się wiele wersji z tej samej rodziny zestawu SDK. Jeśli ten atrybut nie istnieje lub ma ustawioną wartość **Zezwalaj**, program MSBuild nie wyświetla ten typ błędu lub ostrzeżenia.  
  
11. AppX: Określa ścieżkę do pakietów aplikacji dla biblioteki składników systemu Windows na dysku. Ta wartość jest przekazywana do składnika rejestracji biblioteki składników systemu Windows podczas lokalnego debugowania. Konwencja nazewnictwa dla nazwy pliku jest  **\<firmy >.\< Produktu >. \<Architektura >. \<Konfiguracji >. \<Wersji > .appx**. Konfiguracji i architektury są opcjonalne w nazwie atrybutu, a wartość atrybutu, jeśli nie można ich stosować do biblioteki składników systemu Windows. Ta wartość ma zastosowanie tylko do bibliotek składników systemu Windows.  
  
12. CopyRedistToSubDirectory: Określa, gdzie względem katalogu głównego pakietu aplikacji, w którym powinny zostać skopiowane pliki w folderze \redist (to znaczy **lokalizacja pakietu** wybrane w kreatorze tworzenia pakietu aplikacji) i środowiska uruchomieniowego głównego układu. Domyślna lokalizacja to katalog główny pakietu aplikacji i układu F5.  
  
13. DependsOn: Lista tożsamości zestawu SDK, definiujące zestawy SDK, od których zależy ten zestaw SDK. Ten atrybut zostanie wyświetlony w okienku szczegółów Menedżera odwołań.  
  
14. MoreInfo: adres URL do strony sieci web, która zapewnia pomoc i więcej informacji. Ta wartość jest używana w łącza więcej informacji, w okienku po prawej stronie Menedżera odwołań.  
  
15. Typ rejestracji: Określa rejestracji WinMD w manifeście aplikacji i jest wymagany do natywnej WinMD, który ma duplikat implementację biblioteki DLL.  
  
16. Odwołanie do pliku: określona dla tylko tych odwołań, które zawiera formanty lub jest natywny metadanych Winmd. Aby uzyskać informacje o sposobie określania, czy odwołanie zawiera formanty, zobacz [Określanie lokalizacji elementy przybornika](#ToolboxItems) poniżej.  
  
##  <a name="ToolboxItems"></a>Określanie lokalizacji elementy przybornika  
 Element ToolBoxItems schematu SDKManifest.xml określa kategorii i lokalizacji elementy przybornika zarówno platformy i zestawy SDK rozszerzeń. Poniższe przykłady przedstawiają sposób określenia różnych lokalizacjach. Dotyczy on odwołania WinMD i bibliotek DLL.  
  
1.  Umieść formanty w kategorii domyślnego przybornika.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2.  Umieść formanty pod nazwą określonej kategorii.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3.  Umieść formanty w obszarze nazwy określonej kategorii.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  Umieść formanty w obszarze nazw różnych kategorii w programie Blend i Visual Studio.  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  Wyliczanie określonych formantów inaczej w programie Blend i Visual Studio.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  Wyliczanie kontrolek i umieść je w ścieżce wspólnej Visual Studio lub tylko w grupie wszystkie formanty.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  Wyliczanie kontrolek i Pokaż tylko określonego zestawu w ChooseItems bez ich w przyborniku.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie zestawu SDK, w języku C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Wskazówki: Tworzenie SDK przy użyciu języka C# lub Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)