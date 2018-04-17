---
title: 'Porady: Tworzenie projektu zawierającego zasoby | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1932a49af8d6a7ebd6a72ec42700bf51554990bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-build-a-project-that-has-resources"></a>Porady: kompilacja projektu zawierającego zasoby
Jeśli tworzysz zlokalizowane wersje projektu, wszystkie elementy interfejsu użytkownika muszą być rozdzielane do plików zasobów dla różnych języków. Jeśli projekt używa tylko ciągi, pliki zasobów można użyć plików tekstowych. Alternatywnie można użyć pliki .resx jako pliki zasobów.  
  
## <a name="compiling-resources-with-msbuild"></a>Kompilowanie zasobów przy użyciu programu MSBuild  
 Biblioteka typowych zadań, które jest udostępniane z [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] obejmuje `GenerateResource` zadanie, które służy do kompilowania zasobów w plikach .resx lub tekst. To zadanie obejmuje `Sources` parametr, aby określić pliki zasobów do skompilowania i `OutputResources` parametru w celu określenia nazwy plików zasobów danych wyjściowych. Aby uzyskać więcej informacji na temat `GenerateResource` zadań, zobacz [generateresource — zadanie](../msbuild/generateresource-task.md).  
  
#### <a name="to-compile-resources-with-msbuild"></a>Aby skompilować zasobów przy użyciu programu MSBuild  
  
1.  Identyfikowanie plików zasobów projektu i przekazywać je do `GenerateResource` zadań jako list elementów lub jako nazwy plików.  
  
2.  Określ `OutputResources` parametr `GenerateResource` zadania, które można ustawić nazwy dla plików zasobów danych wyjściowych.  
  
3.  Użyj `Output` element zadania do przechowywania wartości `OutputResources` parametru w elemencie.  
  
4.  Użyj elementu utworzone na podstawie `Output` element jako dane wejściowe do innego zadania.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia przykład sposobu `Output` element określa, że `OutputResources` atrybutu `GenerateResource` zadań będzie zawierać pliki zasobów skompilowanych `alpha.resources` i `beta.resources` oraz że te dwa pliki zostaną umieszczone wewnątrz `Resources` listy elementów. Identyfikując tych plików .resources jako kolekcję elementów o takiej samej nazwie, łatwo można je jako dane wejściowe innego zadania, takie jak [Csc](../msbuild/csc-task.md) zadań.  
  
 To zadanie jest odpowiednikiem przy użyciu **Kompiluj** przełączać [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator):  
  
 `Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`  
  
```xml  
<GenerateResource  
    Sources="alpha.resx; beta.txt"  
    OutputResources="alpha.resources; beta.resources">  
    <Output TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
## <a name="example"></a>Przykład  
 Następujący przykładowy projekt zawiera dwa zadania: `GenerateResource` zadanie, aby skompilować zasobów i `Csc` zadanie, aby skompilować zarówno pliki kodu źródłowego, jak i plików skompilowanych zasobów. Pliki zasobów opracowane przez `GenerateResource` zadania są przechowywane w `Resources` elementu i przekazywane do `Csc` zadań.  
  
```xml  
<Project DefaultTargets = "Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <Target Name="Resources">  
        <GenerateResource  
            Sources="alpha.resx; beta.txt"  
            OutputResources="alpha.resources; beta.resources">  
            <Output TaskParameter="OutputResources"  
                ItemName="Resources"/>  
        </GenerateResource>  
    </Target>  
  
    <Target Name="Build" DependsOnTargets="Resources">  
        <Csc Sources="hello.cs"  
                Resources="@(Resources)"  
                OutputAssembly="hello.exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
[MSBuild](../msbuild/msbuild.md)  
 [Generateresource — zadanie](../msbuild/generateresource-task.md)   
 [CSC — zadanie](../msbuild/csc-task.md)   
 [Resgen.exe (generator pliku zasobów)](/dotnet/framework/tools/resgen-exe-resource-file-generator)