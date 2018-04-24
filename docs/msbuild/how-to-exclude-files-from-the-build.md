---
title: 'Porady: wykluczanie plików z kompilacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, excluding files
- wildcards, MSBuild
ms.assetid: 1be36e45-01da-451c-972d-f9fc0e7d663c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb8e8ba51f4aaeed0242147d46fd282b95452d91
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-exclude-files-from-the-build"></a>Porady: wykluczanie plików z kompilacji
W pliku projektu można używać symboli wieloznacznych, aby uwzględnić wszystkie pliki w jednym katalogu lub zagnieżdżony zbiór katalogi jako dane wejściowe dla kompilacji. Jednak może być jeden plik w katalogu lub w katalogu w zestawie zagnieżdżonych katalogów, których nie chcesz dołączyć jako dane wejściowe dla kompilacji. Na liście wejść można jawnie wykluczyć tego pliku lub katalogu. W projekcie, który ma być uwzględniony w niektórych warunkach również może być plikiem. Można jawnie deklarować warunków, w których pliku jest uwzględniona w kompilacji.  
  
## <a name="excluding-a-file-or-directory-from-the-inputs-for-a-build"></a>Wykluczanie pliku lub katalogu dane wejściowe dla kompilacji  
 Element listy są pliki wejściowe dla kompilacji. Elementy, które mają zostać uwzględnione są deklarowane jako pojedynczo lub jako grupę za pomocą `Include` atrybutu. Na przykład:  
  
```xml  
<CSFile Include="Form1.cs"/>  
<CSFile Include ="File1.cs;File2.cs"/>  
<CSFile Include="*.cs"/>  
<JPGFile Include="Images\**\*.jpg"/>  
```  
  
 Jeśli zostały użyte symboli wieloznacznych, aby uwzględnić wszystkie pliki w jednym katalogu lub zagnieżdżony zbiór katalogi jako dane wejściowe dla kompilacji, może być jeden lub więcej plików w katalogu lub w katalogu w zagnieżdżonych zestaw katalogów, których nie chcesz dołączyć. Aby wyłączyć element z listy elementów, użyj `Exclude` atrybutu.  
  
#### <a name="to-include-all-cs-or-vb-files-except-form2"></a>Aby uwzględnić wszystkie pliki .cs lub .vb, z wyjątkiem formularz2  
  
-   Użyj jednej z następujących `Include` i `Exclude` atrybuty:  
  
    ```xml  
    <CSFile Include="*.cs" Exclude="Form2.cs"/>  
    ```  
  
     - lub -  
  
    ```xml  
    <VBFile Include="*.vb" Exclude="Form2.vb"/>  
    ```  
  
#### <a name="to-include-all-cs-or-vb-files-except-form2-and-form3"></a>Aby uwzględnić wszystkie pliki .cs lub .vb, z wyjątkiem Formularz2 i Form3  
  
-   Użyj jednej z następujących `Include` i `Exclude` atrybuty:  
  
    ```xml  
    <CSFile Include="*.cs" Exclude="Form2.cs;Form3.cs"/>  
    ```  
  
     - lub -  
  
    ```xml  
    <VBFile Include="*.vb" Exclude="Form2.vb;Form3.vb"/>  
    ```  
  
#### <a name="to-include-all-jpg-files-in-subdirectories-of-the-images-directory-except-those-in-the-version2-directory"></a>Aby uwzględnić wszystkie pliki jpg w podkatalogach katalogu obrazów, z wyjątkiem tych, które w katalogu Version2  
  
-   Należy użyć następującego `Include` i `Exclude` atrybuty:  
  
    ```xml  
    <JPGFile  
        Include="Images\**\*.jpg"  
        Exclude = "Images\**\Version2\*.jpg"/>  
    ```  
  
    > [!NOTE]
    >  Należy określić ścieżkę dla obu atrybutów. Jeśli ścieżka bezwzględna użyć do określenia lokalizacji plików w `Include` atrybutu, należy również użyć ścieżki bezwzględnej w `Exclude` atrybutu; Jeśli używasz ścieżki względnej `Include` atrybutu, należy również użyć ścieżki względnej w `Exclude`atrybutu.  
  
## <a name="using-conditions-to-exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Za pomocą warunków do wykluczenia pliku lub katalogu z danych wejściowych dla kompilacji  
 Jeśli istnieją elementy, które chcesz dołączyć, na przykład w kompilacji debugowania, ale nie kompilacji wydania, można `Condition` atrybutu można określić warunki, w których chcesz dołączyć elementu.  
  
#### <a name="to-include-the-file-formulavb-only-in-release-builds"></a>Aby dołączyć plik Formula.vb tylko w kompilacjach wydania  
  
-   Użyj `Condition` atrybutu podobny do następującego:  
  
    ```xml  
    <Compile  
        Include="Formula.vb"  
        Condition=" '$(Configuration)' == 'Release' " />  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy projekt z wszystkich plików .cs w katalogu, z wyjątkiem Form2.cs.  
  
```xml  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs Exclude="Form2.cs"/>  
  
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
 [Elementy](../msbuild/msbuild-items.md)   
 [MSBuild](../msbuild/msbuild.md) [porady: Wybieranie plików do kompilacji](../msbuild/how-to-select-the-files-to-build.md)