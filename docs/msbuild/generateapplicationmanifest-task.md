---
title: Generateapplicationmanifest — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateApplicationManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateApplicationManifest task
- HostInBrowser property (MSBuild)
- GenerateApplicationManifest task [MSBuild]
ms.assetid: a494102b-0cb2-4755-8e2a-d2c0f39fac1d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e40e74dd8e7b2b83f6d4239e6b66c9852c6de604
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31575322"
---
# <a name="generateapplicationmanifest-task"></a>GenerateApplicationManifest — Zadanie
Generuje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji lub natywny manifest. Natywny manifest opisuje składnika przez definiowanie unikatową tożsamość składnika i zidentyfikowaniu wszystkie pliki wchodzące w skład składnika i zestawów. A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji rozszerza natywny manifest wskazujący punkt wejścia aplikacji, a następnie określając poziom zabezpieczeń aplikacji.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `GenerateApplicationManifest` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AssemblyName`|Opcjonalne `String` parametru.<br /><br /> Określa `Name` pole tożsamości zestawu wygenerowanego manifestu. Jeśli ten parametr nie jest określony, nazwa jest wywnioskowany na podstawie `EntryPoint` lub `InputManifest` parametrów. Jeśli nazwa nie mogą być tworzone zadania zgłasza błąd.|  
|`AssemblyVersion`|Opcjonalne `String` parametru.<br /><br /> Określa `Version` pole tożsamości zestawu wygenerowanego manifestu. Jeśli ten parametr nie jest określony, wartością domyślną "1.0.0.0" jest używany.|  
|`ClrVersion`|Opcjonalne `String` parametru.<br /><br /> Określa minimalną wersję z wspólnego języka środowiska uruchomieniowego (CLR) wymagane przez aplikację. Wartość domyślna to wersja CLR używany przez system kompilacji. Jeśli zadanie generuje natywny manifest, ten parametr zostanie zignorowany.|  
|`ConfigFile`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa, który element zawiera plik konfiguracji aplikacji. Jeśli zadanie generuje natywny manifest, ten parametr zostanie zignorowany.|  
|`Dependencies`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa, który określa zbiór zestawów zależnych dla manifest wygenerowanego listy elementów. Każdy element może być opisane przez metadane elementu w celu wskazania stanu dodatkowe wdrożenia, a typ zależność. Aby uzyskać więcej informacji zobacz sekcję "Metadanych elementu" poniżej.|  
|`Description`|Opcjonalne `String` parametru.<br /><br /> Określa opis aplikacji lub składnika.|  
|`EntryPoint`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa pojedynczy element, która wskazuje punkt wejścia dla zestawu wygenerowanego manifestu.<br /><br /> Aby uzyskać [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji, ten parametr określa zestaw, który rozpoczyna się po uruchomieniu aplikacji.|  
|`ErrorReportUrl`|Opcjonalne <xref:System.String?displayProperty=fullName> parametru.<br /><br /> Określa adres URL strony sieci Web wyświetlaną w oknach dialogowych podczas raportów o błędach w instalacjach ClickOnce.|  
|`FileAssociations`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa listę co najmniej jeden typ pliku, które są skojarzone z manifest wdrażania ClickOnce.<br /><br /> Skojarzeń plików jedyne prawidłowe, tylko jeśli .NET Framework w wersji 3.5 lub nowszej.|  
|`Files`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Pliki do uwzględnienia w manifeście. Określ pełną ścieżkę dla każdego pliku.|  
|`HostInBrowser`|Opcjonalne <xref:System.Boolean> parametru.<br /><br /> Jeśli `true`, aplikacja jest obsługiwana w przeglądarce (jak są aplikacje przeglądarki sieci Web WPF).|  
|`IconFile`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa plik ikony aplikacji. Ikona aplikacji jest wyrażona w manifeście aplikacji wygenerowany i jest używany dla okna dialogowego Start Menu i Dodaj lub usuń programy. Jeśli nie określono tych danych wejściowych, ikony domyślnej jest używana. Jeśli zadanie generuje natywny manifest, ten parametr zostanie zignorowany.|  
|`InputManifest`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Wskazuje wejściowy dokument XML służyć jako podstawa dla generatora manifestu. Dzięki temu danych strukturalnych, takich jak zabezpieczenia aplikacji lub niestandardowe definicje manifestu zostaną odzwierciedlone w manifeście danych wyjściowych. Element główny dokumentu XML musi być węzłem zestawu w przestrzeni nazw asmv1.|  
|`IsolatedComReferences`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa składniki COM do izolowania w wygenerowanego manifestu. Ten parametr umożliwia do izolowania składników COM dla wdrożenia "Rejestracji wolnego COM". Działa on przez automatyczne generowanie manifestu z standardowe definicje rejestracji COM. Jednak składniki modelu COM musi być zarejestrowany na maszynie kompilacji, aby to działać prawidłowo.|  
|`ManifestType`|Opcjonalne `String` parametru.<br /><br /> Określa typ manifestu do wygenerowania. Ten parametr może mieć następujące wartości:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Jeśli ten parametr nie jest określony, domyślnie zadanie `ClickOnce`.|  
|`MaxTargetPath`|Opcjonalne `String` parametru.<br /><br /> Określa maksymalną dozwoloną długość ścieżki do pliku w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia aplikacji. Jeśli ta wartość jest określona, długość ścieżki każdego pliku w aplikacji jest porównywany ten limit. Wszystkie elementy, które przekraczają limit zostanie podniesiony w ostrzeżeniu kompilacji. Jeśli tych danych wejściowych nie została określona lub jest równa zero, następnie nie jest przeprowadzane żadne sprawdzanie. Jeśli zadanie generuje natywny manifest, ten parametr zostanie zignorowany.|  
|`OSVersion`|Opcjonalne `String` parametru.<br /><br /> Określa minimalnej wymaganej wersji systemu operacyjnego (OS) wymagane przez aplikację. Na przykład wartość "5.1.2600.0" oznacza, że systemem operacyjnym jest Windows XP. Jeśli ten parametr nie jest określony, zostanie użyta wartość "4.10.0.0", która wskazuje, Windows 98 Wydanie drugie, minimalny obsługiwany system operacyjny programu .NET Framework. Jeśli zadanie jest generowany natywny manifest, tych danych wejściowych jest ignorowana.|  
|`OutputManifest`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru wyjściowego.<br /><br /> Określa nazwę pliku manifestu wygenerowanych danych wyjściowych. Jeśli ten parametr nie jest określony, nazwa pliku wyjściowego jest wywnioskowany na podstawie tożsamości wygenerowanego manifestu.|  
|`Platform`|Opcjonalne `String` parametru.<br /><br /> Określa platformę docelową aplikacji. Ten parametr może mieć następujące wartości:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Jeśli ten parametr nie jest określony, domyślnie zadanie `AnyCPU`.|  
|`Product`|Opcjonalne `String` parametru.<br /><br /> Określa nazwę aplikacji. Jeśli ten parametr nie jest określony, nazwa jest wywnioskowany na podstawie tożsamości wygenerowanego manifestu. Ta nazwa jest używana dla nazwy skrótu w Start menu i jest częścią nazwy, która jest wyświetlana w oknie dialogowym Dodaj lub usuń programy.|  
|`Publisher`|Opcjonalne `String` parametru.<br /><br /> Określa wydawcy aplikacji. Jeśli ten parametr nie jest określony, nazwa jest wywnioskowany na podstawie zarejestrowanego użytkownika lub tożsamość wygenerowanego manifestu. Ta nazwa jest używana nazwa folderu, w Start menu i jest częścią nazwy, która jest wyświetlana w oknie dialogowym Dodaj lub usuń programy.|  
|`RequiresMinimumFramework35SP1`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli PRAWDA, aplikacja wymaga platformy .NET Framework 3.5 z dodatkiem SP1 lub nowsza wersja.|  
|`TargetCulture`|Opcjonalne `String` parametru.<br /><br /> Określa kulturę aplikacji i określa `Language` pole tożsamości zestawu wygenerowanego manifestu. Jeśli ten parametr nie jest określony, zakłada się, że aplikacja jest niezmienna kultura.|  
|`TargetFrameworkMoniker`|Opcjonalne `String` parametru.<br /><br /> Określa moniker platformy docelowej.|  
|`TargetFrameworkProfile`|Opcjonalne `String` parametru.<br /><br /> Określa profil platformy docelowej.|  
|`TargetFrameworkSubset`|Opcjonalne `String` parametru.<br /><br /> Określa nazwę podzbioru .NET Framework do obiektu docelowego.|  
|`TargetFrameworkVersion`|Opcjonalne `String` parametru.<br /><br /> Określa docelowy Framework .NET projektu.|  
|`TrustInfoFile`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Wskazuje dokument XML, który określa zabezpieczeń aplikacji. Element główny dokumentu XML musi być węzłem trustinfo — w obszarze nazw asmv2. Jeśli zadanie generuje natywny manifest, ten parametr zostanie zignorowany.|  
|`UseApplicationTrust`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli PRAWDA, `Product`, `Publisher`, i `SupportUrl` właściwości są zapisywane w manifeście aplikacji.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.GenerateManifestBase> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę parametrów klasy zadania, zobacz [klasa podstawowa zadania](../msbuild/task-base-class.md).  
  
 Aby uzyskać informacje o sposobie używania `GenerateDeploymentManifest` zadań, zobacz [generateapplicationmanifest — zadanie](../msbuild/generateapplicationmanifest-task.md).  
  
 Dane wejściowe dla zależności i plików może mieć więcej przypisany metadanych elementu, aby określić stan dodatkowe wdrożenia dla każdego elementu.  
  
## <a name="item-metadata"></a>Metadane elementu  
  
|Nazwa metadanych|Opis|  
|-------------------|-----------------|  
|`DependencyType`|Wskazuje, czy zależność jest opublikowana i zainstalować aplikację lub wymagań wstępnych. Te metadane jest prawidłowa dla wszystkich zależności, ale nie jest używana w przypadku plików. Dostępne wartości to metadane są:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Wartością domyślną jest instalacja.|  
|`AssemblyType`|Wskazuje, czy zależność jest zarządzanego lub zestaw macierzysty. Te metadane jest prawidłowa dla wszystkich zależności, ale nie jest używana w przypadku plików. Dostępne wartości to metadane są:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified` jest to wartość domyślna, co oznacza, że manifestu generator automatycznie zadecyduje o typie zestawu.|  
|`Group`|Wskazuje grupę do pobrania dodatkowych plików na żądanie. Nazwa grupy jest zdefiniowane przez aplikację i może być dowolnym ciągiem. Pustego ciągu oznacza, że plik nie jest częścią grupy pobierania, która jest ustawiona domyślnie. Plików w grupie nie są częścią pobrania początkowej aplikacji. Pliki w grupie tylko są pobierane, gdy wyraźnie zażąda aplikacji przy użyciu <xref:System.Deployment.Application>.<br /><br /> Te metadane jest prawidłowa dla wszystkich plików gdzie `IsDataFile` jest `false` i wszystkie zależności gdzie `DependencyType` jest `Install`.|  
|`TargetPath`|Określa, jak ścieżka powinien być zdefiniowany w manifeście wygenerowany. Ten atrybut jest prawidłowy dla wszystkich plików. Jeśli ten atrybut nie jest określony, używana jest określenie elementu. Ten atrybut jest nieprawidłowy dla wszystkich plików i zależności z `DependencyType` wartość `Install`.|  
|`IsDataFile`|A `Boolean` wartość metadanych, która wskazuje, czy plik jest plikiem danych. Plik danych jest specjalne, że jest migrowana między aktualizacjami aplikacji. Te metadane jest prawidłowa tylko dla plików. `False` jest to wartość domyślna.|  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `GenerateApplicationManifest` zadań, aby wygenerować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest aplikacji i `GenerateDeploymentManifest` zadań do generowania manifestu wdrożenia dla aplikacji z jednym zestawie. Następnie używa `SignFile` zadań do podpisywania manifestów.  
  
 Przedstawiono to najprostszy scenariusz możliwe generowanie manifestu gdzie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty są generowane w jednym programie. Domyślną nazwę i tożsamości są wywnioskować na podstawie zestawu dla manifest.  
  
> [!NOTE]
>  W poniższym przykładzie wszystkie pliki binarne aplikacji są wstępnie przygotowanych, aby skupić się na aspektach Generowanie manifestu. Ten przykład generuje w pełni pracy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat `Thumbprint` właściwości używane w `SignFile` zadań w tym przykładzie, zobacz [signfile — zadanie](../msbuild/signfile-task.md).  
  
```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            EntryPoint="@(EntryPoint)">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            EntryPoint="@(ApplicationManifest)">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `GenerateApplicationManifest` i `GenerateDeploymentManifest` zadań w celu wygenerowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji i wdrażania manifesty dla aplikacji z jednego zestawu, określanie nazwy i tożsamości manifestów.  
  
 W tym przykładzie jest podobny do poprzedniego przykładu, z wyjątkiem nazwy i tożsamości manifesty jawnie określony. Ponadto w tym przykładzie jest skonfigurowana jako aplikacji online zamiast zainstalowanej aplikacji.  
  
> [!NOTE]
>  W poniższym przykładzie wszystkie pliki binarne aplikacji są wstępnie przygotowanych, aby skupić się na aspektach Generowanie manifestu. Ten przykład generuje w pełni pracy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat `Thumbprint` właściwości używane w `SignFile` zadań w tym przykładzie, zobacz [signfile — zadanie](../msbuild/signfile-task.md).  
  
```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            EntryPoint="@(EntryPoint)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
                AssemblyName="SimpleWinApp.application"  
                AssemblyVersion="1.0.0.0"  
                EntryPoint="@(ApplicationManifest)"  
                Install="false"  
                OutputManifest="SimpleWinApp.application">  
                <Output  
                    ItemName="DeployManifest"  
                    TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `GenerateApplicationManifest` i `GenerateDeploymentManifest` zadań w celu wygenerowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji i wdrażania manifesty dla aplikacji z wielu plików i zestawów.  
  
> [!NOTE]
>  W poniższym przykładzie wszystkie pliki binarne aplikacji są wstępnie przygotowanych, aby skupić się na aspektach Generowanie manifestu. Ten przykład generuje w pełni pracy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat `Thumbprint` właściwości używane w `SignFile` zadań w tym przykładzie, zobacz [signfile — zadanie](../msbuild/signfile-task.md).  
  
```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
        <DeployUrl>  
            <!-- Insert the deployment URL here -->  
        </DeployUrl>  
        <SupportUrl>  
            <!-- Insert the support URL here -->  
        </SupportUrl>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe"/>  
        <Dependency Include="ClassLibrary1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <Dependency Include="ClassLibrary2.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <Group>Secondary</Group>  
        </Dependency>  
        <Dependency Include="MyAddIn1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <TargetPath>Addins\MyAddIn1.dll</TargetPath>  
        </Dependency>  
        <Dependency Include="ClassLibrary3.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Prerequisite</DependencyType>  
        </Dependency>  
  
        <File Include="Text1.txt">  
            <TargetPath>Text\Text1.txt</TargetPath>  
            <Group>Text</Group>  
        </File>  
        <File Include="DataFile1.xml ">  
            <TargetPath>Data\DataFile1.xml</TargetPath>  
            <IsDataFile>true</IsDataFile>  
        </File>  
  
        <IconFile Include="Heart.ico"/>  
        <ConfigFile Include="app.config">  
            <TargetPath>SimpleWinApp.exe.config</TargetPath>  
        </ConfigFile>  
        <BaseManifest Include="app.manifest"/>  
    </ItemGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            ConfigFile="@(ConfigFile)"  
            Dependencies="@(Dependency)"  
            Description="TestApp"  
            EntryPoint="@(EntryPoint)"  
            Files="@(File)"  
            IconFile="@(IconFile)"  
            InputManifest="@(BaseManifest)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            AssemblyName="SimpleWinApp.application"  
            AssemblyVersion="1.0.0.0"  
            DeploymentUrl="$(DeployToUrl)"  
            Description="TestDeploy"  
            EntryPoint="@(ApplicationManifest)"  
            Install="true"  
            OutputManifest="SimpleWinApp.application"  
            Product="SimpleWinApp"  
            Publisher="Microsoft"  
            SupportUrl="$(SupportUrl)"  
            UpdateEnabled="true"  
            UpdateInterval="3"  
            UpdateMode="Background"  
            UpdateUnit="weeks">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `GenerateApplicationManifest` zadań do generowania manifestu natywnych aplikacji Test.exe odwołanie do natywnego Alpha.dll i izolowane składnik modelu COM Bravo.dll.  
  
 W tym przykładzie powoduje Test.exe.manifest, co aplikacja XCOPY można wdrożyć, korzystając z modelu COM. wolnego rejestracji  
  
> [!NOTE]
>  W poniższym przykładzie wszystkie pliki binarne aplikacji są wstępnie przygotowanych, aby skupić się na aspektach Generowanie manifestu. Ten przykład generuje w pełni pracy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia.  
  
```xml  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <File Include="Test.exe" />  
        <Dependency Include="Alpha.dll">  
            <AssemblyType>Native</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <ComComponent Include="Bravo.dll" />  
    </ItemGroup>  
  
    <Target Name="Build">  
        <GenerateApplicationManifest  
            AssemblyName="Test.exe"  
            AssemblyVersion="1.0.0.0"  
            Dependencies="@(Dependency)"  
            Files="@(File)"  
            IsolatedComReferences="@(ComComponent)"  
            ManifestType="Native">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Generatedeploymentmanifest — zadanie](../msbuild/generatedeploymentmanifest-task.md)   
 [Signfile — zadanie](../msbuild/signfile-task.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)