---
title: Dyrektywa T4 dotycząca zestawu
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 02d6dcfe0ed84b8f48af40162edb1ac4895c97fe
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="t4-assembly-directive"></a>Dyrektywa T4 dotycząca zestawu

W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] szablonu tekstu w czasie projektowania `assembly` dyrektywy ładuje zestaw, dzięki czemu kod szablonu można użyć jej typów. Efekt jest podobny do dodawania odwołania do zestawu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu.

 Ogólne omówienie pisania szablonów tekstowych, patrz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
>  Nie trzeba `assembly` dyrektywy w szablonie (wstępnie przetworzonych) tekstu czasu wykonywania. Zamiast tego dodać konieczne zestawy, do **odwołania** z Twojej [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu.

## <a name="using-the-assembly-directive"></a>Używanie dyrektywy Assembly
 Składnia tej dyrektywy jest następująca:

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 Nazwa zestawu powinna być jedną z następujących:

-   Silnej nazwy zestawu w pamięci podręcznej GAC, takich jak `System.Xml.dll`. Umożliwia także długich fragmentów, takich jak `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.AssemblyName>.

-   Bezwzględna ścieżka zestawu

 Można użyć `$(variableName)` składni, aby odwołać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zmiennych, takich jak `$(SolutionDir)`, i `%VariableName%` do zmiennych środowiskowych odwołania. Na przykład:

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 Dyrektywa zestawu nie ma wpływu na przetworzony wstępnie szablon tekstowy. Zamiast tego należy uwzględnić niezbędne odwołania w **odwołania** części Twojego [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu czasu wykonywania z szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="standard-assemblies"></a>Standardowe zestawy
 Następujące zestawy są ładowane automatycznie, aby nie trzeba było pisać dla nich dyrektyw zestawu:

-   `Microsoft.VisualStudio.TextTemplating.1*.dll`

-   `System.dll`

-   `WindowsBase.dll`

 Jeśli używasz niestandardowej dyrektywy, procesor dyrektywy może załadować dodatkowe zestawy. Na przykład jeśli piszesz szablony dla języka specyficznego dla domeny (domain-specific language — DSL), nie musisz pisać dyrektyw zestawu dla następujących zestawów:

-   `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`

-   `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`

-   `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`

-   Zestaw zawierający DSL.

##  <a name="msbuild"></a> Za pomocą właściwości projektu w MSBuild i Visual Studio
 Visual Studio makra podobnego do $(SolutionDir) nie działają w programie MSBuild. Aby przekształcić szablony w komputerze kompilacji, musisz użyć właściwości projektu.

 Wyedytuj plik .csproj lub .vbproj, aby zdefiniować właściwość projektu. W tym przykładzie definiuje właściwość o nazwie `myLibFolder`:

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>

```

 Teraz można używać właściwości projektu w szablonach tekstowych, które są prawidłowo przekształcane w Visual Studio i MSBuild:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
```

## <a name="see-also"></a>Zobacz też

- [Dyrektywa T4 dotycząca dołączania](../modeling/t4-include-directive.md)