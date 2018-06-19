---
title: 'Porady: Wybieranie plików do kompilacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 651570ef83f5f87d96ed27538cc4f6ffd569d41f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31570681"
---
# <a name="how-to-select-the-files-to-build"></a>Porady: wybieranie plików do kompilacji
Podczas kompilowania projektu zawiera kilka plików, można wyświetlić listę każdego pliku osobno w pliku projektu lub można uwzględnić wszystkie pliki w jednym katalogu lub zagnieżdżony zbiór katalogów symboli wieloznacznych.  
  
## <a name="specifying-inputs"></a>Określanie dane wejściowe  
 Elementy reprezentują dane wejściowe dla kompilacji. Aby uzyskać więcej informacji na elementach, zobacz [elementów](../msbuild/msbuild-items.md).  
  
 Aby uwzględnić pliki dla kompilacji, muszą być uwzględnione na liście elementów w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu. Wiele plików można dodać do listy elementów przez pliki w tym indywidualnie lub przy użyciu symboli wieloznacznych, aby uwzględnić wielu plików jednocześnie.  
  
#### <a name="to-declare-items-individually"></a>Aby zadeklarować indywidualnie elementów  
  
-   Użyj `Include` atrybuty podobne do następujących:  
  
     `<CSFile Include="form1.cs"/>`  
  
     - lub -  
  
     `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    >  Jeśli elementów w kolekcji elementów nie są w tym samym katalogu co plik projektu, należy określić pełną lub względną ścieżkę do elementu. Na przykład: `Include="..\..\form2.cs"`.  
  
#### <a name="to-declare-multiple-items"></a>Aby zadeklarować wiele elementów  
  
-   Użyj `Include` atrybuty podobne do następujących:  
  
     `<CSFile Include="form1.cs;form2.cs"/>`  
  
     - lub -  
  
     `<VBFile Include="form1.vb;form2.vb"/>`  
  
## <a name="specifying-inputs-with-wildcards"></a>Określanie danych wejściowych z symbolami wieloznacznymi  
 Można również użyć symboli wieloznacznych, aby rekursywnie obejmują wszystkie pliki lub tylko pliki z podkatalogi jako dane wejściowe dla kompilacji. Aby uzyskać więcej informacji na temat symboli wieloznacznych, zobacz [elementów](../msbuild/msbuild-items.md)  
  
 Poniższe przykłady są oparte na projekt, który zawiera pliki grafiki w następujących katalogów oraz podkatalogów, z pliku projektu, znajduje się w katalogu projektu:  
  
 Project\Images\BestJpgs  
  
 Project\Images\ImgJpgs  
  
 Project\Images\ImgJpgs\Img1  
  
#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Aby dołączyć wszystkie pliki .jpg obrazy katalogu i jego podkatalogach  
  
-   Należy użyć następującego `Include` atrybutu:  
  
     `Include="Images\**\*.jpg"`  
  
#### <a name="to-include-all-jpg-files-starting-with-img"></a>Aby uwzględnić wszystkie pliki jpg, począwszy od "img"  
  
-   Należy użyć następującego `Include` atrybutu:  
  
     `Include="Images\**\img*.jpg"`  
  
#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>Aby uwzględnić wszystkie pliki w katalogach, których nazwy kończą się w "jpg"  
  
-   Użyj jednej z następujących `Include` atrybuty:  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     - lub -  
  
     `Include="Images\**\*jpgs\*"`  
  
## <a name="passing-items-to-a-task"></a>Przekazywanie elementów do zadania  
 W pliku projektu można użyć @ () notacji zadań, aby określić listę cały element jako dane wejściowe dla kompilacji. Ten element notation można użyć, czy lista wszystkich plików, oddzielnie lub użyć symboli wieloznacznych.  
  
#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>Aby używać wszystkich Visual C# lub Visual Basic plików jako dane wejściowe  
  
-   Użyj `Include` atrybuty podobny do następującego:  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     - lub -  
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
>  Należy użyć symboli wieloznacznych z elementów do określ dane wejściowe dla kompilacji; Nie można określić przy użyciu wejść `Sources` atrybutu w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadań, takich jak [Csc](../msbuild/csc-task.md) lub [Vbc](../msbuild/vbc-task.md). Poniższy przykład jest nieprawidłowy w pliku projektu:  
>   
>  `<CSC Sources="*.cs">...</CSC>`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje projekt, który zawiera wszystkie pliki wejściowe oddzielnie.  
  
```xml  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Builtdir>built</Builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="Form1.cs"/>  
        <CSFile Include="AssemblyInfo.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje symboli wieloznacznych, aby uwzględnić wszystkie pliki .cs.  
  
```xml  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Elementy](../msbuild/msbuild-items.md)