---
title: 'Porady: kompilacja przyrostowa | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3fac1ce26c95d0a0c51c77e6ca1525d034a4e01f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-build-incrementally"></a>Porady: kompilacja przyrostowa
Podczas kompilowania dużych projektów, należy wcześniej wbudowanej składników, które są nadal aktualne nie zostały odbudowane. Jeśli wszystkie elementy docelowe są tworzone za każdym razem każdej kompilacji będzie trwać bardzo długo. Aby włączyć kompilacji przyrostowej (kompilacji, w którym tylko tych obiektów docelowych, które nie zostały utworzone przed lub elementów docelowych, które są nieaktualne, są odbudować), [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) można porównać sygnatury czasowe plików wejściowych ze znacznikami czasu plików wyjściowych i określanie, czy pominąć, kompilacji lub częściowo odbudować obiektu docelowego. Jednak musi być mapowanie jeden do jednego między wejścia i wyjścia. Aby włączyć elementy docelowe zidentyfikować ten bezpośredniego mapowania można użyć transformacji. Aby uzyskać więcej informacji na transformacje, zobacz [przekształca](../msbuild/msbuild-transforms.md).  
  
## <a name="specifying-inputs-and-outputs"></a>Określanie wejścia i wyjścia  
 Element docelowy mogą być tworzone przyrostowo, jeśli wejściami i wyjściami są określone w pliku projektu.  
  
#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Aby określić wejścia i wyjścia dla elementu docelowego  
  
-   Użyj `Inputs` i `Outputs` atrybuty `Target` elementu. Na przykład:  
  
    ```xml  
    <Target Name="Build"  
        Inputs="@(CSFile)"  
        Outputs="hello.exe">  
    ```  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] można porównać sygnatury czasowe plików wejściowych ze znacznikami czasu plików wyjściowych i określanie, czy pominąć, kompilacji lub częściowo odbudować obiektu docelowego. W poniższym przykładzie, jeśli dowolny plik w `@(CSFile)` listy elementów jest nowszy niż plik hello.exe [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] uruchomi element docelowy; w przeciwnym razie zostanie pominięte:  
  
```xml  
<Target Name="Build"   
    Inputs="@(CSFile)"   
    Outputs="hello.exe">  
  
    <Csc  
        Sources="@(CSFile)"   
        OutputAssembly="hello.exe"/>  
</Target>  
```  
  
 Jeśli wejściami i wyjściami są określone w lokalizacji docelowej, każdy dane wyjściowe można mapować tylko jednego wejścia lub nie mogą istnieć bez bezpośredniego mapowania między wyjścia i danych wejściowych. W poprzednim [CSC — zadanie](../msbuild/csc-task.md), na przykład dane wyjściowe, hello.exe, nie można mapować do dowolnego pojedynczego danych wejściowych — zależy on od wszystkich z nich.  
  
> [!NOTE]
>  Element docelowy, w którym nie ma bezpośredniego mapowania między wejściami i wyjściami zawsze kompilacji częściej niż docelowy, w którym każdy dane wyjściowe można mapować tylko jednego wejścia ponieważ [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nie może określić, które wyjść należy ponownie utworzyć zmiany niektórych danych wejściowych .  
  
 Zadania, w których można zidentyfikować bezpośredniego mapowania między wyniki i dane wejściowe, takie jak [LC — zadanie](../msbuild/lc-task.md), są najbardziej odpowiednie dla kompilacji przyrostowej, w przeciwieństwie do zadań, takich jak `Csc` i [Vbc](../msbuild/vbc-task.md), które produktu jeden wyjściowy zestaw z liczbę wejść.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto projektu, która tworzy plików pomocy dla hipotetycznego system pomocy. Projekt polega na konwertowaniu plików txt źródłowych w pośrednim .content pliki, które następnie są łączone z plikami XML metadanych do tworzenia pliku końcowego .help używane przez system pomocy. Projekt używa hipotetyczny następujące zadania:  
  
-   `GenerateContentFiles`: Konwertuje txt .content plików.  
  
-   `BuildHelp`: Łączy .content pliki i pliki metadanych XML do tworzenia pliku końcowego .help.  
  
 Projekt używa przekształceń do utworzenia mapowanie jeden do jednego między dane wejściowe i danych wyjściowych w `GenerateContentFiles` zadań. Aby uzyskać więcej informacji, zobacz [przekształca](../msbuild/msbuild-transforms.md). Ponadto `Output` elementu ustawiono automatyczne stosowanie dane wyjściowe z `GenerateContentFiles` zadanie jako dane wejściowe dla `BuildHelp` zadań.  
  
 Ten plik projektu zawiera zarówno `Convert` i `Build` elementów docelowych. `GenerateContentFiles` i `BuildHelp` zadania są umieszczane w `Convert` i `Build` odpowiednio elementów docelowych, dzięki czemu można wbudować przyrostowo każdego obiektu docelowego. Za pomocą `Output` element, dane wyjściowe `GenerateContentFiles` zadań są umieszczane w `ContentFile` listy elementów, gdzie są używane jako dane wejściowe dla `BuildHelp` zadań. Przy użyciu `Output` element w ten sposób automatycznie udostępnia dane wyjściowe z zadania jako dane wejściowe dla innego zadania, aby nie musieli poszczególnych elementów listy lub element listy ręcznie w przypadku każdego zadania.  
  
> [!NOTE]
>  Mimo że `GenerateContentFiles` docelowych można tworzyć przyrostowo, wszystkie dane wyjściowe z tego miejsca docelowego zawsze są wymagane jako dane wejściowe dla `BuildHelp` docelowej. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] automatycznie udostępnia wszystkie dane wyjściowe z jednego miejsca docelowego jako dane wejściowe dla innego celu korzystając z `Output` elementu.  
  
```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <TXTFile Include="*.txt"/>  
        <XMLFiles Include="\metadata\*.xml"/>  
    </ItemGroup>  
  
    <Target Name = "Convert"  
        Inputs="@(TXTFile)"  
        Outputs="@(TXTFile->'%(Filename).content')">  
  
        <GenerateContentFiles  
            Sources = "@(TXTFile)">  
            <Output TaskParameter = "OutputContentFiles"  
                ItemName = "ContentFiles"/>  
        </GenerateContentFiles>  
    </Target>  
  
    <Target Name = "Build" DependsOnTargets = "Convert"  
        Inputs="@(ContentFiles);@(XMLFiles)"  
        Outputs="$(MSBuildProjectName).help">  
  
        <BuildHelp  
            ContentFiles = "@(ContentFiles)"  
            MetadataFiles = "@(XMLFiles)"  
            OutputFileName = "$(MSBuildProjectName).help"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty docelowe](../msbuild/msbuild-targets.md)   
 [TARGET — Element (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Przekształca](../msbuild/msbuild-transforms.md)   
 [CSC — zadanie](../msbuild/csc-task.md)   
 [Vbc, zadanie](../msbuild/vbc-task.md)
