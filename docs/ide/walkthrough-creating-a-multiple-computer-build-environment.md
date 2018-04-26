---
title: 'Wskazówki: tworzenie środowiska kompilacji na wielu komputerach'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building on multiple computers
- build environment, MSBuild
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 52c7623aff3c2aec4753f628eb9a24ecf6937275
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-creating-a-multiple-computer-build-environment"></a>Wskazówki: tworzenie środowiska kompilacji na wielu komputerach

Można utworzyć środowisko kompilacji w obrębie organizacji przez zainstalowanie programu Visual Studio na komputerze hosta, a następnie skopiować różne pliki i ustawienia na inny komputer, aby mógł działać w kompiluje. Nie trzeba zainstalować program Visual Studio na innym komputerze.

Ten dokument nie przyznaje praw do ponownej dystrybucji oprogramowania zewnętrznie lub w celu zapewnienia środowiska kompilacji do udzielania podmiotom trzecim.

> Zrzeczenie odpowiedzialności<br /><br /> Niniejszy dokument jest udostępniany na "jako — jest" podstawy. Gdy przetestowano czynności podane nie możemy do testowania wyczerpujący każdej konfiguracji. Firma Microsoft podejmie próbę aktualność dokumentu wszelkie informacje dodatkowe, które zostały rozpoznane. Informacje i poglądy wyrażone w tym dokumencie, w tym adresy URL i innymi odwołaniami do witryn internetowych, mogą ulec zmianie bez uprzedzenia. Microsoft nie udziela żadnych gwarancji, express lub domniemanych, w odniesieniu do informacji dostępnych w tym miejscu. Użytkownik ponosi ryzyko związane z użyciem jej.<br /><br /> Ten dokument nie daje użytkownikowi żadnych praw do jakiejkolwiek własności intelektualnej związanej z jakimkolwiek produktem firmy Microsoft. Można kopiować i używać tego dokumentu do wewnętrznych celów referencyjnych.<br /><br /> Użytkownik nie ma obowiązku nadaniu firmie Microsoft w dowolnym sugestie, komentarzy ani innych opinii ("opinie"), odnoszące się do tego dokumentu. Jednak opinię, dobrowolnie mogą być używane w Microsoft Products i związanych z nimi specyfikacjach lub innych dokumentacji (zbiorczo "Offerings Microsoft"), który z kolei może być stosowane przez osoby trzecie do opracowywania własnych produktów. W związku z tym jeśli Microsoft Feedback dać w dowolnej wersji tego dokumentu lub Offerings firmy Microsoft do których mają zastosowanie, akceptujesz: () firmy Microsoft może korzystać za darmo, odtworzyć licencji, rozpowszechniania i inaczej komercjalizacji tych opinii w udostępnianych przez firmę Microsoft Oferty; (b) można również przyznać stron trzecich, bez dodatkowych opłat, tylko te patentowe prawa niezbędne do obsługi innych produktów lub interfejsu z określonych części Product firmy Microsoft, wykorzystujących opinię użytkownika; i (c) użytkownik nie będzie przekazywać Microsoft opinię (i), czy masz podejrzeń podlega wszelkie oświadczenia patentowe, autorskie lub inne prawa własności intelektualnej lub prawa osobom trzecim; lub (ii) z zastrzeżeniem postanowień licencyjnych, które się wymagają żadnych Offering firmy Microsoft zawierająca lub pochodzące z takich opinii lub innych własności intelektualnej Microsoft licencji lub w inny sposób udostępniać podmiotom trzecim.

W tym przewodniku została zweryfikowana względem następujących systemów operacyjnych, wykonując MSBuild w wierszu polecenia i za pomocą Team Foundation Build.

- Windows 8 (x86 i x64)
- Windows 7 Ultimate
- Windows Server 2008 R2 Standard

 Po wykonaniu kroków w tym przewodniku służy środowisko wiele komputerów do kompilacji tego rodzaju aplikacji:

- C++ aplikacji klasycznych, które używają systemu Windows 8 SDK
- Visual Basic lub C# aplikacji klasycznych, które odnoszą się do programu .NET Framework 4.5

 W środowisku wielu komputerach nie może służyć do tworzenia tego rodzaju aplikacji:

- Aplikacje platformy uniwersalnej systemu Windows. Aby tworzenie aplikacji platformy uniwersalnej systemu Windows, należy zainstalować program Visual Studio na komputerze kompilacji.
- Aplikacji klasycznych, które odnoszą się do programu .NET Framework 4 lub starszym. Aby utworzyć tego rodzaju aplikacji, należy zainstalować na komputerze kompilacji Visual Studio lub zestawów odwołań .NET i narzędzia (zestaw Windows 7.1 SDK).

 Ten przewodnik jest podzielona na te części:

- [Instalowanie oprogramowania na komputerach](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingSoftware)

- [Kopiowanie plików z hosta na komputerze kompilacji](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles)

- [Tworzenie ustawień rejestru](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingRegistry)

- [Ustawianie zmiennych środowiskowych na komputerze kompilacji](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#SettingEnvVariables)

- [Instalowanie programu MSBuild zestawów do globalnej pamięci podręcznej zestawów (GAC) na komputerze kompilacji](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC)

- [Tworzenie projektów](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#BuildingProjects)

- [Tworzenie środowiska kompilacji, dzięki czemu może być wyewidencjonowany do kontroli źródła](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingForSourceControl)

## <a name="prerequisites"></a>Wymagania wstępne

- Program Visual Studio z obciążeniem tworzenia klasycznych aplikacji .NET, które są zainstalowane.

## <a name="InstallingSoftware"></a> Instalowanie oprogramowania na komputerach

Najpierw należy skonfigurować komputer hosta, a następnie ponowne skonfigurowanie komputera kompilacji.

Instalując program Visual Studio na komputerze-hoście, tworzenia plików i ustawień, które zostanie skopiowany na komputer kompilacji później. Visual Studio można zainstalować na x86 lub x64 komputer, ale z architekturą komputera kompilacji musi być zgodna z architekturą komputera hosta.

1. Zainstaluj program Visual Studio na komputerze hosta.

2. Na komputerze kompilacji należy zainstalować program .NET Framework 4.5. Aby sprawdzić, czy jest zainstalowany, upewnij się, że wartość rejestru klucza HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full@Version rozpoczyna się od "4.5".

## <a name="CopyingFiles"></a> Kopiowanie plików z hosta na komputerze kompilacji

Ta sekcja obejmuje kopiowanie określonych plików, kompilatory narzędzia kompilacji, zasoby MSBuild i ustawień rejestru z komputera hosta na komputerze kompilacji. W poniższych instrukcjach przyjęto, że po zainstalowaniu programu Visual Studio w domyślnej lokalizacji na komputerze hosta; Jeśli zainstalowano w innej lokalizacji, w związku z tym odpowiedniego dostosowania kroków.

- Na x86 komputera, domyślna lokalizacja to C:\Program Files\Microsoft Visual Studio 11.0\
- Na x64 komputera, domyślna lokalizacja to C:\Program Files (x86) \Microsoft Visual Studio 11.0\

Należy zauważyć, że nazwa folderu Program Files zależy od systemu operacyjnego, który jest zainstalowany. Na x86 komputera, nazwa jest \Program Files\\; na x64 komputera, nazwa jest \Program Files (x86)\\. Niezależnie od architektury systemu w tym przewodniku odnosi się do folderu Program Files jako % ProgramFiles %.

> [!NOTE]
> Na komputerze kompilacji wszystkie odpowiednie pliki muszą być na tym samym dysku; jednak litera dysku może być inny niż literę dysku, na którym jest zainstalowany program Visual Studio na komputerze hosta. W każdym przypadku należy uwzględnić lokalizację plików po utworzeniu wpisy rejestru zgodnie z opisem w dalszej części tego dokumentu.

#### <a name="to-copy-the-windows-sdk-files-to-the-build-computer"></a>Aby skopiować pliki zestawu SDK systemu Windows na komputerze kompilacji

1. Jeśli masz tylko systemu Windows SDK dla systemu Windows 8 zainstalowane, skopiuj rekursywnie tych folderów z komputera hosta na komputerze kompilacji:

    - %ProgramFiles%\Windows Kits\8.0\bin\

    - %ProgramFiles%\Windows Kits\8.0\Catalogs\

    - %ProgramFiles%\Windows Kits\8.0\DesignTime\

    - %ProgramFiles%\Windows Kits\8.0\include\

    - %ProgramFiles%\Windows Kits\8.0\Lib\

    - %ProgramFiles%\Windows Kits\8.0\Redist\

    - %ProgramFiles%\Windows Kits\8.0\References\

     Jeśli masz także te inne zestawy Windows 8...

    - Microsoft Windows Assessment and Deployment Kit

    - Zestaw sterowników systemu Windows firmy Microsoft

    - Zestawu certyfikacji sprzętu systemu Microsoft Windows

     .. one mógł zainstalować pliki w folderach Kits\8.0\ %ProgramFiles%\Windows, które są wymienione w poprzednim kroku, a ich postanowień licencyjnych może nie pozwalać na serwer kompilacji prawa do tych plików. Sprawdź umowy licencyjnej dla każdego zainstalowanego zestawu systemu Windows sprawdzić, czy pliki mogą być kopiowane na komputerze kompilacji. Jeśli postanowienia licencyjne nie zezwalaj na serwer kompilacji praw, Usuń pliki z komputera kompilacji.

2. Skopiuj następujące rekursywnie folderów z komputera hosta na komputerze kompilacji:

    - %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\

    - %ProgramFiles%\Common Files\Merge Modules\

    - %ProgramFiles%\Microsoft Visual Studio 11.0\VC\

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\ProjectComponents\

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\V110\

    - %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\. NETCore\v4.5\

    - %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\. NETFramework\v4.5\

3. Skopiuj następujące pliki z komputera hosta na komputerze kompilacji:

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\msobj110.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\mspdb110.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\mspdbcore.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\mspdbsrv.exe

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\msvcdis110.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\makehm.exe

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\VCVarsQueryRegistry.bat

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\vsvars32.bat

4. Następujące biblioteki środowiska uruchomieniowego Visual C++ są wymagane tylko w przypadku uruchomienia na komputerze kompilacji, dane wyjściowe kompilacji — na przykład w ramach testów automatycznych. Pliki są zazwyczaj znajduje się w podfolderach w ramach %ProgramFiles%\Microsoft Visual Studio 11.0\VC\redist\x86\ lub %ProgramFiles%\Microsoft Visual Studio 11.0\VC\redist\x64\ folder, w zależności od architektury systemu. Na x86 systemów plików binarnych x86 Kopiuj do folderu \Windows\System32\. Na x64 systemów plików binarnych kopiowania x86 w folderze Windows\SysWOW64\ i x64 dane binarne do folderu Windows\System32\.

    - \Microsoft.VC110.ATL\atl110.dll

    - \Microsoft.VC110.CRT\msvcp110.dll

    - \Microsoft.VC110.CRT\msvcr110.dll

    - \Microsoft.VC110.CXXAMP\vcamp110.dll

    - \Microsoft.VC110.MFC\mfc110.dll

    - \Microsoft.VC110.MFC\mfc110u.dll

    - \Microsoft.VC110.MFC\mfcm110.dll

    - \Microsoft.VC110.MFC\mfcm110u.dll

    - \Microsoft.VC110.MFCLOC\mfc110chs.dll

    - \Microsoft.VC110.MFCLOC\mfc110cht.dll

    - \Microsoft.VC110.MFCLOC\mfc110deu.dll

    - \Microsoft.VC110.MFCLOC\mfc110enu.dll

    - \Microsoft.VC110.MFCLOC\mfc110esn.dll

    - \Microsoft.VC110.MFCLOC\mfc110fra.dll

    - \Microsoft.VC110.MFCLOC\mfc110ita.dll

    - \Microsoft.VC110.MFCLOC\mfc110jpn.dll

    - \Microsoft.VC110.MFCLOC\mfc110kor.dll

    - \Microsoft.VC110.MFCLOC\mfc110rus.dll

    - \Microsoft.VC110.OPENMP\vcomp110.dll

5. Skopiuj następujące pliki z folderu \Debug_NonRedist\x86\ lub \Debug_NonRedist\x64\ na komputerze kompilacji, zgodnie z opisem w [przygotowania komputera do uruchomienia testu, plik wykonywalny debugowania](/cpp/ide/preparing-a-test-machine-to-run-a-debug-executable). Żadne inne pliki można skopiować.

    - \Microsoft.VC110.DebugCRT\msvcp110d.dll

    - \Microsoft.VC110.DebugCRT\msvcr110d.dll

    - \Microsoft.VC110.DebugCXXAMP\vcamp110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110ud.dll

    - \Microsoft.VC110.DebugMFC\mfcm110d.dll

    - \Microsoft.VC110.DebugMFC\mfcm110ud.dll

    - \Microsoft.VC110.DebugOpenMP\vcomp110d.dll

##  <a name="CreatingRegistry"></a> Tworzenie ustawień rejestru
 Należy utworzyć wpisy rejestru, aby skonfigurować ustawienia dla programu MSBuild.

#### <a name="to-create-registry-settings"></a>Aby utworzyć ustawienia rejestru

1. Określ folder nadrzędny dla wpisów rejestru. Wszystkie wpisy rejestru są tworzone w tym samym kluczu nadrzędnej. Na x86 komputera, klucz nadrzędny jest HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Na x64 komputer klucza nadrzędnego jest HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. Niezależnie od architektury systemu w tym przewodniku odnosi się do klucza nadrzędnego jako RegistryRoot %.

    > [!NOTE]
    > Jeśli architektura komputera-hosta różni się od komputera kompilacji, upewnij się użyć klucza elementu nadrzędnego na każdym komputerze. Jest to szczególnie ważne, jeśli w przypadku automatyzacji procesu eksportowania.
    >
    > Ponadto jeśli używasz innej litery dysku na komputerze kompilacji niż konto, którego używasz na komputerze-hoście, upewnij się, że zmiany wartości do dopasowania wpisów rejestru.

2. Utwórz następujące wpisy rejestru na komputerze kompilacji. Wszystkie te wpisy są ciągami (typ == "REG_SZ" w rejestrze). Ustaw wartości te wpisy tak samo jak wartości porównywalne wpisów na komputerze hosta.

    - % RegistryRoot %\\. NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSBuild Assemblies@(Default) publiczny

    - %RegistryRoot%\Microsoft SDKs\Windows\v8.0@InstallationFolder

    - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A@InstallationFolder

    - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder

    - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder

    - % RegistryRoot %\VisualStudio\11.0@Source katalogów

    - %RegistryRoot%\VisualStudio\11.0\Setup\VC@ProductDir

    - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir32

    - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir64

    - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer32

    - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer64

    - %RegistryRoot%\VisualStudio\SxS\VC7@11.0

    - %RegistryRoot%\VisualStudio\SxS\VS7@11.0

    - %RegistryRoot%\Windows Kits\Installed Roots@KitsRoot

    - %RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath

    - %RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10

    - %RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11

     Na x64 Tworzenie komputera, tworzyć następujący wpis rejestru i odwoływać się do komputera hosta, aby określić, jak ustawić go.

    - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder

     Jeśli komputer kompilacji jest x64 i chcesz używać 64-bitowej wersji programu MSBuild lub jeśli używasz usługi kompilacji Team Foundation Server na x64 komputera, należy utworzyć następujące wpisy rejestru w natywnych 64-bitowego rejestru. Odwołuje się do komputera hosta, aby określić, jak ustawić te wpisy.

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11

## <a name="SettingEnvVariables"></a> Ustawianie zmiennych środowiskowych na komputerze kompilacji

Aby użyć MSBuild na komputerze kompilacji, należy ustawić zmienne środowiskowe ścieżki. Vcvarsall.bat można użyć do ustawienia zmiennych, lub można ręcznie skonfigurować je.

### <a name="to-use-vcvarsallbat-to-set-environment-variables"></a>Aby ustawić zmienne środowiskowe za pomocą vcvarsall.bat

- Otwórz okno wiersza polecenia na komputerze kompilacji, a następnie uruchom % Program Files%\Microsoft Visual Studio 11.0\VC\vcvarsall.bat. Argument wiersza polecenia można użyć do określenia zestawu narzędzi, którego chcesz użyć — x86, natywnego x64 lub x64 między kompilatora. Jeśli nie zostanie określony argument wiersza polecenia x86 używanego zestawu narzędzi.

     W tej tabeli opisano obsługiwane argumenty vcvarsall.bat:

    |Vcvarsall.bat argument|Kompilatora|Tworzenie architektury komputera|Architektura danych wyjściowych kompilacji|
    |----------------------------|--------------|---------------------------------|-------------------------------|
    |x86 (ustawienie domyślne)|natywny 32-bitowych|x86, x64|x86|
    |x86_amd64|x64 między|x86, x64|X64|
    |amd64|x64 macierzystego|X64|X64|

     Jeśli vcvarsall.bat zostanie wykonane pomyślnie — to znaczy, że jest wyświetlany żaden komunikat o błędzie — można pominąć następny krok i Kontynuuj w [MSBuild instalowanie zestawów do globalnej pamięci podręcznej zestawów (GAC) na komputerze kompilacji](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC) sekcji tego dokumentu .

### <a name="to-manually-set-environment-variables"></a>Aby ręcznie ustawić zmienne środowiskowe

1. Aby ręcznie skonfigurować środowiska wiersza polecenia, Dodaj tę ścieżkę do zmiennej środowiskowej PATH:

    - %Program Files%\Microsoft Visual Studio 11.0\Common7\IDE

2. Opcjonalnie można również Dodaj następujące ścieżki do zmiennej PATH, aby ułatwić Użyj programu MSBuild do tworzenia rozwiązań.

     Jeśli chcesz użyć natywnego MSBuild 32-bitowy, Dodaj te ścieżki do zmiennej PATH:

    - %Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools

    - %windir%\Microsoft.NET\Framework\v4.0.30319

     Jeśli chcesz użyć natywnego MSBuild 64-bitowych, Dodaj te ścieżki do zmiennej PATH:

    - %Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\x64

    - %windir%\Microsoft.NET\Framework64\v4.0.30319

## <a name="InstallingMSBuildToGAC"></a> Instalowanie programu MSBuild zestawów do globalnej pamięci podręcznej zestawów (GAC) na komputerze kompilacji

MSBuild wymaga niektóre dodatkowe zestawy GAC na komputerze kompilacji, należy zainstalować.

1. Skopiuj następujące zestawy z komputera hosta na komputerze kompilacji. Ponieważ zostaną zainstalowane w GAC, nie ma znaczenia, gdzie umieścić je na komputerze kompilacji.

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.Common.v110.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll

2. Aby zainstalować zestawy GAC, zlokalizuj gacutil.exe na komputerze kompilacji — zazwyczaj jest w folderze %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 narzędzia\\. Jeśli nie możesz znaleźć tego folderu, powtórz kroki [kopiowanie plików z hosta na komputerze kompilacji](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) sekcji tego przewodnika.

     Otwórz okno wiersza polecenia, które ma uprawnienia administracyjne i uruchom to polecenie dla każdego pliku:

     **gacutil -i \<pliku >**

    > [!NOTE]
    > Ponowne uruchomienie komputera może być wymagane dla zestawu do w pełni zainstalowane w pamięci GAC.

## <a name="BuildingProjects"></a> Tworzenie projektów

Team Foundation Build można użyć do tworzenia [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] projektów i rozwiązań lub można je kompilować w wierszu polecenia. Korzystając z Team Foundation Build do kompilacji projektów, wywołuje MSBuild pliku wykonywalnego, umożliwiająca architektura systemu. W wierszu polecenia można użyć MSBuild 32-bitowy lub 64-bitowego programu MSBuild, a przez ustawienie zmiennej środowiskowej PATH lub bezpośrednio wywoływania MSBuild architektury pliku wykonywalnego, można wybrać architektura programu MSBuild.

Aby użyć msbuild.exe w wierszu polecenia, uruchom następujące polecenie, w którym *solution.sln* jest symbolem zastępczym dla nazwy rozwiązania.

**msbuild** *solution.sln*

Aby uzyskać więcej informacji o sposobie używania programu MSBuild w wierszu polecenia, zobacz [dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

> [!NOTE]
> Aby utworzyć [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] projektów, należy użyć zestawu narzędzi platformy "v110". Jeśli nie chcesz edytować [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] pliki projektu, należy określić zestaw narzędzi platformy przy użyciu tego argumentu wiersza polecenia:
>
> **msbuild** *solution.sln* **/p:PlatformToolset=v110**

## <a name="CreatingForSourceControl"></a> Tworzenie środowiska kompilacji, dzięki czemu może być wyewidencjonowany do kontroli źródła

Można utworzyć środowiska kompilacji, które mogą być wdrażane na różnych komputerach i nie wymaga GAC'ing plików lub modyfikowania ustawień rejestru. Poniższe kroki są tylko jeden sposób, w tym celu. Dostosować te kroki, aby unikatowych parametrów, środowiska kompilacji.

> [!NOTE]
> Należy wyłączyć kompilowanie przyrostowej tak, aby tracker.exe nie zgłosi błąd podczas kompilacji. Aby wyłączyć kompilowanie przyrostowej, ustaw ten parametr kompilacji:
>
> **msbuild** *solution.sln* **/p:TrackFileAccess=false**

1. Utwórz katalog "Magazynu" na komputerze hosta.

     Te kroki można znaleźć w katalogu jako magazynu %.

2. Skopiuj pliki i katalogi, zgodnie z opisem w [kopiowanie plików z hosta na komputerze kompilacji](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) sekcji tego przewodnika, z wyjątkiem wklej je w katalogu % magazynu %, który został właśnie utworzony. Na przykład skopiuj z %ProgramFiles%\Windows Kits\8.0\bin\ %Depot%\Windows Kits\8.0\bin\\.

3. Gdy pliki są wklejane w magazynie %, należy wprowadzić te zmiany:

    - W lokalizacji % Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets \Microsoft.Cpp.InvalidPlatforms.targets\\, \Microsoft.cppbuild.targets\\i \Microsoft.CppCommon.targets\\, zmienić każde wystąpienie z

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

         na

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

         Wcześniejsze nazewnictwa zależy od zestawu jest GAC'ed.

    - W % \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPPClean.Targets % magazynu należy zmienić każde wystąpienie

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

         na

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

4. Utwórz plik .props — na przykład Partner.AutoImports.props—and umieszcza je w katalogu głównym folderu, który zawiera projekty. Ten plik jest używany do ustawienia zmiennych, które są używane przez program MSBuild można znaleźć różnych zasobów. Jeśli zmienne nie są skonfigurowane przez ten plik, są one ustawiane przez inne pliki .props i pliki .targets, które opierają się na wartości rejestru. Ponieważ firma Microsoft nie jest ustawienie wartości rejestru, tych zmiennych może być pusta i kompilacji nie powiedzie się. Zamiast tego należy dodać ten element do Partner.AutoImports.props:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <!-- This file must be imported by all project files at the top of the project file. -->
    <Project ToolsVersion="4.0"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
    <VCTargetsPath>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath>
    <VCTargetsPath11>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath11>
    <MSBuildExtensionsPath>$(DepotRoot)MSBuild</MSBuildExtensionsPath>
    <MSBuildExtensionsPath32>$(DepotRoot)MSBuild</MSBuildExtensionsPath32>
    <VCInstallDir_110>$(DepotRoot)Microsoft Visual Studio 11.0\VC\</VCInstallDir_110>
    <VCInstallDir>$(VCInstallDir_110)</VCInstallDir>
    <WindowsKitRoot>$(DepotRoot)Windows Kits\</WindowsKitRoot>
    <WindowsSDK80Path>$(WindowsKitRoot)</WindowsSDK80Path>
    <WindowsSdkDir_80>$(WindowsKitRoot)8.0\</WindowsSdkDir_80>
    <WindowsSdkDir>$(WindowsSDKDir_80)</WindowsSdkDir>
    <WindowsSdkDir_80A>$(DepotRoot)Microsoft SDKs\Windows\v8.0A\</WindowsSdkDir_80A>
    </PropertyGroup>
    </Project>
    ```

5. W każdym z plików projektu, Dodaj następujący wiersz na początku, po `<Project Default Targets...>` wiersza.

    ```xml
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>
    ```

6. Zmień środowiska wiersza polecenia w następujący sposób:

    - Ustaw magazynu =*lokalizację katalogu magazynu, który został utworzony w kroku 1*

    - Ustaw ścieżkę = % path %; *lokalizacji MSBuild na komputerze*; %D epot%\Windows\System32;%D epot%\Windows\SysWOW64;%D epot%\Microsoft 11.0\Common7\IDE\ programu Visual Studio

         Dla natywnych 64-bitowych tworzenia, wskaż MSBuild 64-bitowych.

## <a name="see-also"></a>Zobacz także

- [Przygotowanie maszyny testowej do uruchomienia pliku wykonywalnego debugowania](/cpp/ide/preparing-a-test-machine-to-run-a-debug-executable)
- [Dokumentacja wiersza polecenia](../msbuild/msbuild-command-line-reference.md)