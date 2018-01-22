---
title: "Generowanie nowego projektu: Kulisy, część druga | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a35010af9ee0b0d7ad885f607b8fc1e2d54a19ba
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2018
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Generowanie nowego projektu: Kulisy, część druga
W [nowej generacji projektu: pod maską, część 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) widzieliśmy jak **nowy projekt** okna dialogowego pole zostanie wypełnione. Załóżmy, że wybrano **Visual C# Windows aplikacji**, wypełnionego **nazwa** i **lokalizacji** pola tekstowe i klikniętej OK.  
  
## <a name="generating-the-solution-files"></a>Generowanie plików rozwiązania  
 Wybieranie szablonów aplikacji kieruje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Rozpakowywanie i otwieranie odpowiedni plik .vstemplate i uruchomić szablon interpretować polecenia XML w tym pliku. Te polecenia Tworzenie projektów i elementów projektu w rozwiązaniu do nowego lub istniejącego.  
  
 Szablon wypakowuje pliki źródłowe, nazywany szablonów elementów z tego samego folderu zip, który zawiera plik .vstemplate. Szablon te pliki są kopiowane do nowego projektu, dostosowywanie ich odpowiednio.  
  
### <a name="template-parameter-replacement"></a>Zastępowanie parametru szablonu  
 Gdy szablon kopiuje szablonu elementów do nowego projektu, zastępuje wszelkie parametry szablonu z ciągami, aby dostosować plik. Parametr szablonu to specjalne token, który jest poprzedzony i następuje znak dolara ($), na przykład $date$.  
  
 Oto typowy projektu szablonu elementu. Wyodrębnij i sprawdź, czy plik Program.cs w folderze Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace $safeprojectname$  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Jeśli tworzysz nowy projekt aplikacji systemu Windows o nazwie prosty, szablon, zastępuje `$safeprojectname$` parametr o nazwie projektu.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace Simple  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Aby uzyskać pełną listę parametrów szablonu, zobacz [parametrów szablonu](../../ide/template-parameters.md).  
  
## <a name="a-look-inside-a-vstemplate-file"></a>Wygląd wewnątrz. Plik VSTemplate  
 Ten format jest plik .vstemplate podstawowe  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 Analizujemy \<TemplateData > w sekcji [nowej generacji projektu: pod maską, część 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Tagi w tej sekcji służą do sterować wyglądem **nowy projekt** okno dialogowe.  
  
 Tagi w \<TemplateContent > sekcji kontroli generowania nowych projektów i elementów projektu. Oto \<TemplateContent > sekcji z pliku cswindowsapplication.vstemplate w folderze 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip \Program Files\Microsoft programu Visual Studio.  
  
```  
<TemplateContent>  
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">  
    <ProjectItem ReplaceParameters="true"  
      TargetFileName="Properties\AssemblyInfo.cs">  
      AssemblyInfo.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Resources.resx">  
      Resources.resx  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">  
      Resources.Designer.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Settings.settings">  
      Settings.settings  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">  
      Settings.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
      Form1.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Form1.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Program.cs  
    </ProjectItem>  
  </Project>  
</TemplateContent>  
```  
  
 \<Projektu > tag kontroluje Generowanie projektu i \<ProjectItem > tag kontroluje Generowanie elementu projektu. Parametr ReplaceParameters ma wartość true, szablon dostosować wszystkie parametry szablonu w pliku projektu lub elementu. W takim przypadku wszystkie elementy projektu są dostosowane, z wyjątkiem Settings.settings.  
  
 Parametr TargetFileName Określa nazwę i ścieżkę względną, wynikowy plik projektu lub elementu. Dzięki temu można utworzyć strukturę folderów dla projektu. Jeśli nie określisz ten argument elementu projektu ma taką samą nazwę jak szablonu elementu projektu.  
  
 Wynikowa struktury folderów aplikacji systemu Windows wygląda następująco:  
  
 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 Pierwszy i tylko \<projektu > tag w odczyty szablonu:  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 To powoduje, że szablon nowego projektu, aby utworzyć plik projektu Simple.csproj, kopiowanie i dostosowując windowsapplication.csproj element szablonu.  
  
### <a name="designers-and-references"></a>Projektanci i odwołań  
 Widoczny w Eksploratorze rozwiązań czy folderze właściwości jest dostępny i zawiera oczekiwanych plików. Ale co projekt odwołuje się i zależności pliku projektanta, takich jak Resources.Designer.cs do Resources.resx i Form1.Designer.cs do pliku Form1.cs?  Te są zainstalowane w pliku Simple.csproj po jego wygenerowaniu.  
  
 Oto \<ItemGroup > z Simple.csproj, która tworzy odwołania do projektu:  
  
```  
<ItemGroup>  
    <Reference Include="System" />  
    <Reference Include="System.Data" />  
    <Reference Include="System.Deployment" />  
    <Reference Include="System.Drawing" />  
    <Reference Include="System.Windows.Forms" />  
    <Reference Include="System.Xml" />  
</ItemGroup>  
```  
  
 Widać, że są one odwołań sześciu projektu, które są widoczne w Eksploratorze rozwiązań. Oto sekcji z innego \<ItemGroup >. Wiele wierszy kodu zostały usunięte z myślą o przejrzystości. W tej sekcji sprawia, że Settings.Designer.cs jest zależny od Settings.settings:  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie nowego projektu: za kulisami, część pierwsza](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild.md)