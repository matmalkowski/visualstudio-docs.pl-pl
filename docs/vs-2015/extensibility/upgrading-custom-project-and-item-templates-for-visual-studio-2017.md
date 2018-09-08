---
title: Uaktualnianie szablonów niestandardowych projektów i elementów dla programu Visual Studio "15" | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 02c7b14051a41616ed1b98812d1f1b7762f7165e
ms.sourcegitcommit: aea5cdb76fbc7eb31d1e5cc3c8d6adb0c743220f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44126551"
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-15"></a>Uaktualnianie niestandardowych szablonów projektów i elementów dla programu Visual Studio "15"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [uaktualnianie niestandardowych szablonów projektów i elementów dla programu Visual Studio ](https://docs.microsoft.com/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017).  
  
Począwszy od programu Visual Studio "15" wersji zapoznawczej 4 program Visual Studio zmienia sposób odnajduje szablonów projektów i elementów, które zostały zainstalowane, msi lub plikiem typu .vsix. Jeśli jesteś właścicielem rozszerzenia, które używają niestandardowego projektu lub szablonów elementów, musisz zaktualizować swoje rozszerzenia. W tym temacie opisano, co należy zrobić.  
  
 Ta zmiana dotyczy tylko programu Visual Studio "15". Nie ma wpływu na poprzednie wersje programu Visual Studio.  
  
 Jeśli chcesz utworzyć szablon projektu lub elementu jako część rozszerzenia VSIX, zobacz [Tworzenie niestandardowych szablonów projektów i elementów](../extensibility/creating-custom-project-and-item-templates.md).  
  
## <a name="template-scanning"></a>Szablon skanowania  
 Wcześniej **devenv/Setup** lub **devenv/installvstemplates** skanowania dysku lokalnym, aby znaleźć szablonów projektów i elementów. Począwszy od wersji zapoznawczej 4 skanowanie zostanie wykonane tylko w przypadku lokalizacji poziom użytkownika (**%USERPROFILE%\Documents\\< wersja programu Visual Studio\>\My wyeksportowane szablony\\**) używanego do obsługi generowane przez szablony **pliku / Export szablony** polecenia.  
  
 Do innych lokalizacji (niezwiązanych z użytkownikiem) musi zawierać plik manifest(.vstman), który określa lokalizację i innych parametrów szablonu. W pliku vstman jest generowany wraz z pliku .vstemplate, używany do szablonów. Po zainstalowaniu rozszerzenia za pomocą plikiem typu .vsix, można to zrobić przez kompilację rozszerzenie w programie Visual Studio "15" (wersja zapoznawcza) 2. Ale jeśli używasz pliku .msi, musisz wprowadzić zmiany ręcznie. Aby uzyskać listę co należy zrobić, aby wprowadzić te zmiany, zobacz **uaktualnienia zainstalowane za pomocą rozszerzenia. MSI** w dalszej części tego tematu.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Jak zaktualizować rozszerzenia VSIX przy użyciu projektu lub szablonów elementów  
 Ta procedura wyjaśnia, jak aktualizacja 2 w wersji zapoznawczej programu Visual Studio "15" istniejące rozszerzenia VSIX.  
  
1.  Otwórz rozwiązanie w programie Visual Studio "15" (wersja zapoznawcza) 2. Użytkownik jest proszony o uaktualnienie kodu. Kliknij przycisk **OK**.  
  
2.  Po zakończeniu uaktualniania, konieczne może być zmiana wersji docelowej instalacji. W projekcie VSIX, otwórz plik source.extension.vsixmanifest, a następnie wybierz **Instaluj obiekty docelowe** kartę. Jeśli **zakres wersji** pole jest **[14.0]**, kliknij przycisk **Edytuj** i zmień je, aby dołączyć do programu Visual Studio "15". Na przykład można ustawić go **[14.0,15.0]** instalowania rozszerzenia do programu Visual Studio 2015 lub Visual Studio "15", lub **[15.0]** go zainstalować, aby po prostu programu Visual Studio "15".  
  
3.  Należy ponownie skompilować kod.  
  
4.  Zamknij program Visual Studio.  
  
5.  Zainstalować VSIX.  
  
6.  Aktualizację można sprawdzić, wykonując następujące czynności:  
  
    1.  Skanowania zmian plików jest aktywowany przez następujący klucz rejestru:  
  
         **Polecenie reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  Po dodaniu klucza uruchomienia **devenv/installvstemplates**.  
  
    3.  Otwórz ponownie program Visual Studio. Szablon powinien znajdować się w oczekiwanej lokalizacji.  
  
    > [!NOTE]
    >  Szablony projektów Visual Studio Extensibility nie są dostępne, gdy klucz rejestru jest obecny. Należy usunąć klucz rejestru (i ponownie uruchom **devenv/installvstemplates**) z nich korzystać.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Inne zalecenia dotyczące wdrażania szablonów projektów i elementów  
  
-   Należy unikać używania plików zip szablonu. Pliki z rozszerzeniem zip szablonu, które pliki muszą mieć bez kompresji w celu pobrania zasobów i zawartości, więc będą one costlier do użycia. Zamiast tego należy wdrożyć szablonów projektów i elementów jako pojedyncze pliki, w ramach własnego katalogu w celu przyspieszenia inicjowanie szablonu. Rozszerzenia VSIX dla zadania kompilacji zestawu SDK zostanie automatycznie Rozpakuj dowolnego zip szablonu podczas tworzenia pliku VSIX.  
  
-   Należy unikać używania wpisy identyfikator pakietu/zasobu dla nazwy szablonu, opis, ikona lub w wersji zapoznawczej, aby uniknąć niepotrzebnych zasobów załadowań zestawów podczas odnajdywania szablonów. Zamiast tego można użyć zlokalizowane manifesty można utworzyć wpisu szablonu dla poszczególnych ustawień regionalnych, który używa właściwości lub zlokalizowanych nazw.  
  
-   Jeśli w tym szablony jako elementy pliku generowania manifestu może nie dać oczekiwanych wyników. W takim przypadku należy dodać ręcznie wygenerowany manifest w projekcie VSIX.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Zmiany plików szablonów projektów i elementów  
 W tekście objaśniono punkty różnica między wersją programu Visual Studio 2015 i plików szablonów w wersji programu Visual Studio "15", aby mogli tworzyć nowe pliki poprawnie.  
  
 W tym miejscu jest to domyślny plik .vstemplate projekt utworzony przez program Visual Studio 2015:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">  
  <TemplateData>  
    <Name>ProjectTemplate1</Name>  
    <Description>ProjectTemplate1</Description>  
    <Icon>ProjectTemplate1.ico</Icon>  
    <ProjectType>CSharp</ProjectType>  
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
    <SortOrder>1000</SortOrder>  
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>  
    <CreateNewFolder>true</CreateNewFolder>  
    <DefaultName>ProjectTemplate1</DefaultName>  
    <ProvideDefaultName>true</ProvideDefaultName>  
  </TemplateData>  
  <TemplateContent>  
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">  
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>  
    </Project>  
  </TemplateContent>  
</VSTemplate>  
  
```  
  
 Oto pliku vstman (możesz go znaleźć w katalogu manifestu projekt VSIX), który jest wynikiem ponownie skompilować projekt VSIX:  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Project">  
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ProjectTemplate1</Name>  
        <Description>ProjectTemplate1</Description>  
        <Icon>ProjectTemplate1.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <SortOrder>1000</SortOrder>  
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>  
        <CreateNewFolder>true</CreateNewFolder>  
        <DefaultName>ProjectTemplate1</DefaultName>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 Informacje dostarczone przez [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) elementu pozostają bez zmian. **\<VSTemplateContainer >** elementu wskazuje plik .vstemplate dla skojarzonego szablonu.  
  
 W tym miejscu jest to domyślny plik .vstemplate elementu utworzone przez program Visual Studio 2015:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">  
  <TemplateData>  
    <Name>ItemTemplate1</Name>  
    <Description>ItemTemplate1</Description>  
    <Icon>ItemTemplate1.ico</Icon>  
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
    <ProjectType>CSharp</ProjectType>  
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    <DefaultName>Class.cs</DefaultName>  
  </TemplateData>  
  <TemplateContent>  
    <References>  
      <Reference>  
        <Assembly>System</Assembly>  
      </Reference>  
    </References>  
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>  
  </TemplateContent>  
</VSTemplate>  
  
```  
  
 Oto pliku vstman (możesz go znaleźć w katalogu manifestu projekt VSIX), który jest wynikiem ponownie skompilować projekt VSIX:  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Item">  
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ItemTemplate1</Name>  
        <Description>ItemTemplate1</Description>  
        <Icon>ItemTemplate1.ico</Icon>  
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <DefaultName>Class.cs</DefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 Informacje dostarczone przez  **\<TemplateData >** elementu pozostają bez zmian. **\<VSTemplateContainer >** elementu wskazuje plik .vstemplate dla skojarzonego szablonu  
  
 Aby uzyskać więcej informacji na temat różnych elementów pliku vstman zobacz [Visual Studio Manifest odwołanie do schematu szablonu](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Aktualizacje dla rozszerzeń zainstalowany za pomocą. TOŻSAMOŚCI USŁUGI ZARZĄDZANEJ  
 Niektóre rozszerzenia opartym na MSI wdrażania szablonów typowe lokalizacje szablonu, takie jak następujące:  
  
-   **\<Katalog instalacyjny usługi Visual Studio > \Common7\IDE\\< ProjectTemplates/elementów >**  
  
-   **\<Katalog instalacyjny usługi Visual Studio > \Common7\IDE\Extensions\\< ExtensionName\>\\< Project/elementów >**  
  
 Rozszerzenie wykonuje wdrożenie oparte na MSI, musisz ręcznie wygenerować manifest szablonu i upewnij się, że jest ona objęta Instalator rozszerzenia. Należy porównać przykłady vstman wymienionych powyżej i [Visual Studio Manifest odwołanie do schematu szablonu](../extensibility/visual-studio-template-manifest-schema-reference.md). Aby zobaczyć, co jest potrzebne do uwzględnienia  
  
 Należy utworzyć oddzielny manifesty dla szablonów projektów i elementów, a powinien wskazywać szablonu katalog główny jak określono powyżej. Należy utworzyć jeden manifest rozszerzenia i ustawień regionalnych.  
  
## <a name="troubleshooting-template-installation"></a>Rozwiązywanie problemów z instalacją szablonu  
 Jeśli napotkasz problemy z wdrażania szablonów projektu lub elementu, można włączyć rejestrowanie diagnostyczne.  
  
1.  Uruchom następujące polecenie, aby ustawić klucz rejestru, aby włączyć rejestrowanie:  
  
     **Polecenie reg add HKCU\software\microsoft\visualstudio\15.0_Config\VSTemplate /v EnableTemplateDiscoveryLog /t REG_DWORD /d 1**  
  
2.  Uruchom program Visual Studio i uruchamiaj oknach dialogowych nowy projekt i nowy element, aby zainicjować obu drzewach szablonu. Pojawia się w dzienniku szablonu **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0\VsTemplateDiagnosticsList.csv**. Każdy szablon drzewa inicjowania dołącza wpisy w tym dzienniku.  
  
 Plik dziennika zawiera następujące kolumny:  
  
-   **FullPathToTemplate**, która zawiera następujące wartości:  
  
    -   1 w przypadku wdrażania w manifeście  
  
    -   0 w przypadku wdrożenia na dysku  
  
-   **TemplateFileName**  
  
-   Inne właściwości szablonu

