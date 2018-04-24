---
title: 'Porady: tworzenie tych samych plików źródłowych z różnymi opcjami | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- source files, building with different options
- MSBuild, properties
- project properties, modifying
- Hello World example [Visual Studio]
ms.assetid: d14f1212-ddd9-434f-b138-f840011b0fb2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1fc33c17c245ae06b7db35a1c1e938f7e14b95b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Porady: kompilacja tych samych plików źródłowych przy użyciu różnych opcji
Podczas tworzenia projektów często kompilacji tej samej składniki z opcjami różnych kompilacji. Na przykład można utworzyć kompilację debugowania z informacji o symbolach lub kompilacji wydania bez informacji o symbolu, ale z włączonymi optymalizacjami. Lub w przypadku kompilowania projektu do uruchamiania na danej platformie, takich jak x86 lub [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)]. W takich przypadkach większość opcji kompilacji nie zmieniają się; tylko kilka opcji nie zostaną zmienione na sterowanie konfigurację kompilacji. Z [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], użyj właściwości i warunki do tworzenia konfiguracji różnych kompilacji.  
  
## <a name="using-properties-to-modify-projects"></a>Aby zmodyfikować projektów przy użyciu właściwości  
 `Property` Element definiuje zmienną, do którego odwołuje się kilka razy w pliku projektu, takie jak lokalizacja katalogu tymczasowego, lub do ustawiania wartości właściwości, które są używane w kompilacji kilka konfiguracji, takich jak kompilację debugowania i wydania. Aby uzyskać więcej informacji o właściwościach, zobacz [właściwości programu MSBuild](../msbuild/msbuild-properties.md).  
  
 Właściwości można użyć, aby zmienić konfigurację kompilacji, bez konieczności zmiany pliku projektu. `Condition` Atrybutu `Property` elementu i `PropertyGroup` element umożliwia zmianę wartości właściwości. Aby uzyskać więcej informacji na temat [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] warunkach, zobacz [warunki](../msbuild/msbuild-conditions.md).  
  
#### <a name="to-set-a-group-of-properties-based-on-another-property"></a>Aby ustawić grupę właściwości na podstawie innej właściwości  
  
-   Użyj `Condition` atrybutu w `PropertyGroup` podobny do następującego elementu:  
  
    ```xml  
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">  
        <DebugType>full</DebugType>  
        <Optimize>no</Optimize>  
    </PropertyGroup>  
    ```  
  
#### <a name="to-define-a-property-based-on-another-property"></a>Aby zdefiniować właściwości na podstawie innej właściwości  
  
-   Użyj `Condition` atrybutu w `Property` podobny do następującego elementu:  
  
    ```xml  
    <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>  
    ```  
  
## <a name="specifying-properties-on-the-command-line"></a>Określanie właściwości w wierszu polecenia  
 Po zapisaniu pliku projektu do akceptowania konfiguracji z wieloma musisz mieć możliwość zmiany tych konfiguracjach zawsze, gdy skompilowanie projektu. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] udostępnia tę możliwość, zezwalając właściwości należy określić przy użyciu wiersza polecenia **/property** lub **/p** przełącznika.  
  
#### <a name="to-set-a-project-property-at-the-command-line"></a>Aby ustawić właściwości projektu w wierszu polecenia  
  
-   Użyj **/property** przełącznik z właściwością, a wartość właściwości. Na przykład:  
  
    ```  
    msbuild file.proj /property:Flavor=Debug  
    ```  
  
     - lub -  
  
    ```  
    Msbuild file.proj /p:Flavor=Debug  
    ```  
  
#### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Aby określić więcej niż jedną właściwość projektu w wierszu polecenia  
  
-   Użyj **/property** lub **/p** przełącznik wiele razy z właściwości i wartości właściwości lub użyj jednego **/property** lub **/p** przełącznika i wiele właściwości należy rozdzielić średnikami (;). Na przykład:  
  
    ```  
    msbuild file.proj /p:Flavor=Debug;Platform=x86  
    ```  
  
     - or-  
  
    ```  
    msbuild file.proj /p:Flavor=Debug /p:Platform=x86  
    ```  
  
 Zmienne środowiskowe są także traktowane jako właściwości i są automatycznie włączane przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Aby uzyskać więcej informacji na temat używania zmiennych środowiskowych, zobacz [porady: Użycie zmiennych środowiskowych w kompilacji](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
 Wartość właściwości, która jest określona w wierszu polecenia mają pierwszeństwo przed żadnej wartości, które ustawiono tę samą właściwość w pliku projektu, a wartość w pliku projektu mają pierwszeństwo przed wartość w zmiennej środowiskowej.  
  
 To zachowanie można zmienić za pomocą `TreatAsLocalProperty` atrybut w tagu projektu. Dla nazwy właściwości, które są wyświetlane z tego atrybutu wartość właściwości, która jest określona w wierszu polecenia nie pierwszeństwo przed wartością w pliku projektu. Przykład można znaleźć w dalszej części tego tematu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu projektu "Hello World" zawiera dwa nowe grupy właściwości, które mogą służyć do tworzenia kompilację debugowania i kompilacji wydania.  
  
 Aby utworzyć wersja do debugowania tego projektu, wpisz:  
  
```  
msbuild consolehwcs1.proj /p:flavor=debug  
```  
  
 Aby utworzyć wersji detalicznej tego projektu, wpisz:  
  
```  
msbuild consolehwcs1.proj /p:flavor=retail  
```  
  
```xml  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <!-- Sets the default flavor of an environment variable called   
    Flavor is not set or specified on the command line -->  
    <PropertyGroup>  
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>  
    </PropertyGroup>  
  
    <!-- Define the DEBUG settings -->  
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">  
        <DebugType>full</DebugType>  
        <Optimize>no</Optimize>  
    </PropertyGroup>  
  
    <!-- Define the RETAIL settings -->  
    <PropertyGroup Condition="'$(Flavor)'=='RETAIL'">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>yes</Optimize>  
    </PropertyGroup>  
  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>HelloWorldCS</appname>  
    </PropertyGroup>  
  
    <!-- Specify the inputs by type and file name -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input files  
        of type CSFile -->  
        <CSC  Sources = "@(CSFile)"  
            DebugType="$(DebugType)"  
            Optimize="$(Optimize)"  
            OutputAssembly="$(appname).exe" >  
  
            <!-- Set the OutputAssembly attribute of the CSC  
            task to the name of the executable file that is   
            created -->  
            <Output TaskParameter="OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób użycia `TreatAsLocalProperty` atrybutu. `Color` Właściwość ma wartość `Blue` w pliku projektu i `Green` w wierszu polecenia. Z `TreatAsLocalProperty="Color"` w tagu projektu właściwość wiersza polecenia (`Green`) nie zastępować właściwość, która jest zdefiniowana w pliku projektu (`Blue`).  
  
 Aby skompilować projekt, wprowadź następujące polecenie:  
  
```  
msbuild colortest.proj /t:go /property:Color=Green  
```  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0" TreatAsLocalProperty="Color">  
  
    <PropertyGroup>  
        <Color>Blue</Color>  
    </PropertyGroup>  
  
    <Target Name="go">  
        <Message Text="Color: $(Color)" />  
    </Target>  
</Project>  
  
<!--  
  Output with TreatAsLocalProperty="Color" in project tag:  
     Color: Blue  
  
  Output without TreatAsLocalProperty="Color" in project tag:  
     Color: Green  
-->  
```  
  
## <a name="see-also"></a>Zobacz też  
[MSBuild](../msbuild/msbuild.md)  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md)   
 [Project, element (MSBuild)](../msbuild/project-element-msbuild.md)