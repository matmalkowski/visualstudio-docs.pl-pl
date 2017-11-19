---
title: "Uaktualnianie niestandardowe szablony projektów i elementów dla programu Visual Studio 2017 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76437dff5aa59e4864216318e64a07245c15c68d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>Uaktualnianie niestandardowe szablony projektów i elementów dla programu Visual Studio 2017 r.
Począwszy od programu Visual Studio 2017 Visual Studio zmienia sposób wykrytego szablonów projektów i elementów zainstalowanych przez .vsix lub msi. Jeśli jesteś właścicielem rozszerzenia używające niestandardowych projektu lub szablony elementów, należy zaktualizować rozszerzenia. W tym temacie wyjaśniono, co należy zrobić.  
  
 Ta zmiana wpływa tylko 2017 programu Visual Studio. Nie ma ona wpływu na poprzednie wersje programu Visual Studio.  
  
 Jeśli chcesz utworzyć szablon projektu lub elementu w ramach rozszerzenia VSIX, zobacz [Tworzenie niestandardowych Project and Item Templates](../extensibility/creating-custom-project-and-item-templates.md).  
  
## <a name="template-scanning"></a>Szablon skanowania  
 Wcześniej **devenv/Setup** lub **devenv/installvstemplates** skanowania dysku lokalnym, aby znaleźć szablonów projektów i elementów. Począwszy od wersji zapoznawczej 4 skanowanie zostanie wykonane tylko w przypadku lokalizacji użytkownika na poziomie (**%USERPROFILE%\Documents\\< wersji programu Visual Studio\>szablony wyeksportowane \My\\**) używanego do Szablony generowane przez **plików / Export szablony** polecenia.  
  
 Do innych lokalizacji (niezwiązanych z użytkownikiem) musi zawierać plik manifest(.vstman), który określa lokalizację i innych parametrów szablonu. Plik .vstman jest generowany wraz z pliku .vstemplate używane dla szablonów. Po zainstalowaniu rozszerzenia przy użyciu typu .vsix, można to zrobić przez kompilację rozszerzenie w Visual Studio 2017 r. Jednak użycie pliku .msi, musisz ręcznie wprowadzić zmiany. Aby uzyskać listę co należy zrobić, aby wprowadzić te zmiany, zobacz **uaktualnienia z zainstalowane rozszerzenia. MSI** dalszej części tego tematu.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Jak zaktualizować rozszerzenie VSIX z projektu lub szablony elementu  
 Ta procedura wyjaśnia, jak ma Visual Studio 2017 r
1.  Otwórz rozwiązanie w Visual Studio 2017 r. Użytkownik jest proszony o uaktualnienie kodu. Kliknij przycisk **OK**.  
  
2.  Po zakończeniu uaktualniania, może być konieczna zmiana wersji docelowej instalacji. W projekcie VSIX, otwórz plik Source.Extension.vsixmanifest,a i wybierz **zainstalować obiekty docelowe** kartę. Jeśli **zakres wersji** pole jest **[14.0]**, kliknij przycisk **Edytuj** i zmień, aby uwzględnić Visual Studio 2017 r. Na przykład można ustawić go **[14.0,15.0]** można zainstalować rozszerzenia programu Visual Studio 2015 lub Visual Studio 2017 lub do **[15.0]** Aby zainstalować ją po prostu 2017 programu Visual Studio.  
  
3.  Skompiluj ponownie kod.  
  
4.  Zamknij program Visual Studio.  
  
5.  Zainstalować pliku VSIX.  
  
6.  Aktualizację można sprawdzić, wykonując następujące czynności:  
  
    1.  Skanowanie zmiany pliku jest aktywowany przez następujący klucz rejestru:  
  
         **Polecenie reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  Po dodaniu klucza uruchomienia **devenv/installvstemplates**.  
  
    3.  Otwórz ponownie program Visual Studio. Szablon powinien znajdować się w oczekiwanej lokalizacji.  
  
    > [!NOTE]
    >  Szablony projektu Visual Studio Extensibility nie są dostępne, jeśli obecna jest wartość klucza rejestru. Należy usunąć ten klucz rejestru (i ponownie uruchom **devenv/installvstemplates**) z nich korzystać.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Inne zalecenia dotyczące wdrażania szablony projektów i elementów  
  
-   Unikaj używania plików zip szablonu. ZIP szablon, którego pliki muszą mieć nieskompresowanych w celu pobrania zasobów i zawartości, więc będą one costlier do użycia. Zamiast tego należy wdrożyć szablonów projektów i elementów jako pojedyncze pliki, w obszarze ich własnego katalogu w celu przyspieszenia inicjowania szablonu. Dla rozszerzenia VSIX zadania kompilacji zestawu SDK będą automatycznie Rozpakuj dowolnego zip szablonu podczas tworzenia pliku VSIX.  
  
-   Unikaj używania wpisy Identyfikator zasobu/pakietu do nazwy szablonu, opis, ikona lub Podgląd, aby uniknąć niepotrzebnych zasobów zestawu ładuje podczas odnajdowania szablonu. Zamiast tego można zlokalizowanych manifestów utworzyć wpis szablonu dla każdego ustawienia regionalne, które używa zlokalizowanych nazw lub właściwości.  
  
-   Jeśli w tym szablony jako elementy pliku Generowanie manifestu może nie zapewniają oczekiwanych rezultatów. W takim przypadku należy dodać ręcznie wygenerowane manifestu do projektu VSIX.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Zmiany pliku szablony projektów i elementów  
Zostanie przedstawiony punkty różnica między Visual Studio 2015 i wersji programu Visual Studio 2017 plików szablonów, dzięki czemu można tworzyć nowe pliki poprawnie.  
  
 Oto domyślny plik .vstemplate projektu utworzonych przez program Visual Studio 2015:  
  
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
  
 Oto plik .vstman (znajduje się on w katalogu manifestu VSIX projektu), który jest wynikiem odbudowywania projektu VSIX:  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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
  
 Informacje dostarczane przez [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) element pozostaje bez zmian. **\<VSTemplateContainer >** element wskazuje plik .vstemplate szablonu skojarzone.  
  
 Oto domyślny plik .vstemplate elementu utworzone w programie Visual Studio 2015:  
  
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
  
 Oto plik .vstman (znajduje się on w katalogu manifestu VSIX projektu), który jest wynikiem odbudowywania projektu VSIX:  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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
  
 Informacje dostarczane przez  **\<TemplateData >** element pozostaje bez zmian. **\<VSTemplateContainer >** element wskazuje plik .vstemplate skojarzone szablonu  
  
 Aby uzyskać więcej informacji na temat różnych elementów pliku .vstman zobacz [programu Visual Studio manifestu odwołanie do schematu szablonu](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Z zainstalowanym uaktualnień dla rozszerzeń. MSI  
 Niektóre rozszerzenia na podstawie MSI wdrażanie szablonów do wspólnej lokalizacji szablonu takie jak następujące:  
  
-   **\<Katalog instalacyjny usługi Visual Studio > \Common7\IDE\\< ProjectTemplates/elementów >**  
  
-   **\<Katalog instalacyjny usługi Visual Studio > \Common7\IDE\Extensions\\< ExtensionName\>\\< Project/elementów >**  
  
 Rozszerzenie wykonuje wdrażanie na podstawie MSI, musisz ręcznie wygenerować manifest szablonu i upewnij się, że jest uwzględnione w konfiguracji rozszerzenia. Należy porównać przykłady .vstman wymienione powyżej i [programu Visual Studio manifestu odwołanie do schematu szablonu](../extensibility/visual-studio-template-manifest-schema-reference.md). Aby zobaczyć, co jest potrzebne do dołączenia  
  
 Należy utworzyć oddzielny manifesty dla szablonów projektów i elementów i powinny wskazywać szablonu katalog główny określonych powyżej. Należy utworzyć jeden manifest według rozszerzenia i ustawień regionalnych.  
  
## <a name="troubleshooting-template-installation"></a>Rozwiązywanie problemów z instalacją szablonu  
 Jeśli wystąpiły problemy wdrażanie szablonów projektu lub elementu, można włączyć rejestrowania diagnostycznego.  
  
1.  Tworzenie pliku pkgdef w folderze Common7\IDE\CommonExtensions instalacji (np. C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) z następującą zawartość:  
  
     ```
     [$RootKey$\VsTemplate]
     "EnableTemplateDiscoveryLog"=dword:00000001
     ```

2. Otwórz "Developer wiersz polecenia" instalacji przez wyszukiwanie w wyszukiwania systemu Windows i uruchom `devenv /updateConfiguration`.

3.  Uruchom program Visual Studio, a następnie uruchom okna dialogowe nowego projektu i nowy element zainicjować obu drzewach szablonu. Zostanie wyświetlony w dzienniku szablonu **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid identyfikatorowi Instalacja wystąpienia programu Visual Studio). Inicjowanie drzewa każdego szablonu dołącza wpisy w tym dzienniku.  
  
 Plik dziennika zawiera następujące kolumny:  
  
-   **FullPathToTemplate**, która zawiera następujące wartości:  
  
    -   1 w przypadku wdrażania dla manifest  
  
    -   0 dla wdrożenia opartego na dysku  
  
-   **TemplateFileName**  
  
-   Inne właściwości szablonu

Uwaga: Aby wyłączyć rejestrowanie, Usuń pliku pkgdef lub zmień wartość `EnableTemplateDiscoveryLog` do `dword:00000000` i uruchom `devenv /updateConfiguration` ponownie.