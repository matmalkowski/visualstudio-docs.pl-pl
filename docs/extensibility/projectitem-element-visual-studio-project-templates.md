---
title: Projectitem — Element (szablony projektu Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8a7dfbfd03df24c2968dc9dae141ffc7a300e8be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem — Element (Szablony projektu Visual Studio)
Określa plik, który znajduje się w szablonie projektu.  
  
> [!NOTE]
>  `ProjectItem` Element akceptuje różnych atrybutów w zależności od tego, czy szablon jest dla projektu lub elementu. W tym temacie opisano `ProjectItem` elementu dla szablonów projektu. Aby uzyskać informacje o `ProjectItem` elementu szablony elementów, zobacz [projectitem — Element (Visual Studio elementu szablony)](../extensibility/projectitem-element-visual-studio-item-templates.md).  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<Project>  
 \<ProjectItem >  
  
## <a name="syntax"></a>Składnia  
  
```  
<ProjectItem  
    TargetFileName="TargetFileName.ext"  
    ReplaceParameters="true/false"  
    OpenInEditor="true/false"  
    OpenInWebBrowser="true/false"  
    OpenInHelpBrowser="true/false"  
    OpenOrder="Value">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`TargetFileName`|Atrybut opcjonalny.<br /><br /> Określa nazwę i ścieżkę elementu projektu, gdy projekt jest tworzony na podstawie szablonu. Ten atrybut jest przydatne do tworzenia struktury katalogów różnych ze struktury katalogów w pliku zip szablonu lub do utworzenia nazwy elementu przy użyciu zastąpienia parametrów.|  
|`ReplaceParameters`|Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element ma wartości parametrów, które muszą zostać zastąpione podczas projektu jest tworzona na podstawie szablonu. Wartość domyślna to `false`.|  
|`OpenInEditor`|Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element powinien zostać otwarty w edytorze odpowiednich w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utworzenia projektu z szablonu.<br /><br /> `OpenInWebBrowser` i `OpenInHelpBrowser` atrybuty są ignorowane w elemencie z `OpenInEditor` wartość `true`.<br /><br /> Wartość domyślna to `false`.|  
|`OpenInWebBrowser`|Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element powinien zostać otwarty w przeglądarce sieci Web po utworzeniu projektu z szablonu.<br /><br /> Tylko pliki HTML i plików tekstowych, które znajdują się lokalnie do projektu, będzie można otworzyć w przeglądarce sieci Web. Zewnętrzne adresy URL nie można otworzyć z tym atrybutem.<br /><br /> Wartość domyślna to `false`.|  
|`OpenInHelpBrowser`|Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy element powinien zostać otwarty w Podglądzie pomocy, gdy projekt jest tworzony na podstawie szablonu.<br /><br /> Tylko pliki HTML i plików tekstowych, które znajdują się lokalnie w projekcie, mogą być otwierane w Pomocy przeglądarki. Zewnętrzne adresy URL nie można otworzyć z tym atrybutem.<br /><br /> Wartość domyślna to `false`.|  
|`OpenOrder`|Atrybut opcjonalny.<br /><br /> Określa wartość liczbową, która reprezentuje porządek, że elementy będą otwierane w ich odpowiednich edytory. Wszystkie wartości musi być wielokrotnością liczby 10. Elementy wyższy `OpenOrder` wartości są najpierw otwarte.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|Określa plików lub katalogów do dodania do projektu.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 A `string` reprezentujący nazwę lub ścieżkę do pliku w pliku zip szablonu.  
  
## <a name="remarks"></a>Uwagi  
 `ProjectItem` jest opcjonalne podrzędnym `Project`.  
  
 `TargetFileName` Atrybut może służyć do tworzenia struktury katalogów różnych ze struktury katalogów w pliku zip szablonu. Na przykład jeśli plik `MyFile.vb` istnieje w katalogu głównym pliku zip szablonu, ale plik ma być umieszczone w katalogu o nazwie `CustomFiles` we wszystkich projektach utworzone na podstawie szablonu, należy użyć następującego kodu XML:  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 `TargetFileName` Atrybutu mogą służyć do zmiany nazwy plików, które zawierają znaki międzynarodowe w ich nazw plików. Na przykład plik zip szablonu nie może zawierać nazwy plików znaków Unicode, więc plik należy zmienić nazwę przed można skompresować do pliku zip. `TargetFileName` Atrybut może służyć do wartość oryginalna nazwa pliku Unicode.  
  
 `TargetFileName` Atrybutu mogą służyć do zmiany nazwy plików z parametrami. W poniższej procedurze wyjaśniono, jak zmienić nazwę pliku `MyFile.vb`, który istnieje w katalogu głównym pliku zip szablonu, do nazwy pliku na podstawie nazwy projektu.  
  
### <a name="to-rename-files-with-parameters"></a>Do zmiany nazwy plików z parametrami  
  
1.  Użyj następującego kodu XML w pliku .vstemplate:  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  Otwórz plik projektu (vbproj dla [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektu) w edytorze tekstów lub [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Odszukaj wiersz w pliku projektu, która wygląda podobnie do następującego kodu XML:  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  Zastąp w wierszu kodu XML następujące:  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     Gdy projekt jest tworzony na podstawie tego szablonu, nazwa pliku będą oparte na Nazwa użytkownika wprowadzona w **nowy projekt** okno dialogowe, ze wszystkimi niebezpieczny znaków i usunięte spacje. Aby uzyskać więcej informacji, zobacz [parametrów szablonu](../ide/template-parameters.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono metadane szablonu projektu dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablony projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Parametry szablonu](../ide/template-parameters.md)   
 [ProjectItem, element (szablony elementów Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)