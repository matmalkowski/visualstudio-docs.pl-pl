---
title: 'Porady: rozszerzanie procesu kompilacji programu Visual Studio | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c6d373a6d5296e535069beeeb6ad551ad93a9444
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Porady: rozszerzanie procesu kompilacji programu Visual Studio
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Procesu kompilacji jest definiowana za pomocą serii [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliki .targets, które są importowane do pliku projektu. Jeden z tych plików zaimportowanych Microsoft.Common.targets, może zostać rozszerzony do umożliwiają uruchamianie niestandardowych zadań w kilku miejscach w procesie kompilacji. W tym temacie opisano dwie metody umożliwia rozszerzanie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proces kompilacji:  
  
-   Zastępowanie określonych wstępnie zdefiniowanego w Microsoft.Common.targets.  
  
-   Zastępowanie właściwości "DependsOn" zdefiniowane w Microsoft.Common.targets.  
  
## <a name="overriding-predefined-targets"></a>Zastępowanie wstępnie zdefiniowanych obiektów docelowych  
 Plik Microsoft.Common.targets zawiera zestaw wstępnie zdefiniowanych celów pusta, które są wywoływane przed i po niektóre z najważniejszych elementów docelowych w procesie kompilacji. Na przykład [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wywołania `BeforeBuild` docelowy przed głównym `CoreBuild` docelowych i `AfterBuild` docelowego po `CoreBuild` docelowej. Domyślnie puste elementy docelowe Microsoft.Common.targets nic nie rób, ale ich zachowanie domyślne można przesłonić, definiując obiektów docelowych, które powinny znaleźć się w pliku projektu, który importuje Microsoft.Common.targets. Dzięki temu można użyć [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadania, aby mieć lepszą kontrolę nad procesem kompilacji.  
  
#### <a name="to-override-a-predefined-target"></a>Aby zastąpić wstępnie zdefiniowanych docelowych  
  
1.  Zidentyfikuj wstępnie zdefiniowanych docelowych w Microsoft.Common.targets, który chcesz zastąpić. Poniższa tabela Pełna lista elementów docelowych, które można bezpiecznie zmienić.  
  
2.  Definiowanie docelowego lub miejsc docelowych na końcu pliku projektu bezpośrednio przed `</Project>` tagu. Na przykład:  
  
    ```xml  
    <Project>  
        ...  
        <Target Name="BeforeBuild">  
            <!-- Insert tasks to run before build here -->  
        </Target>  
        <Target Name="AfterBuild">  
            <!-- Insert tasks to run after build here -->  
        </Target>  
    </Project>  
    ```  
  
3.  Tworzenie pliku projektu.  
  
 W poniższej tabeli przedstawiono wszystkie elementy docelowe w Microsoft.Common.targets, którą można bezpiecznie zastąpić.  
  
|Nazwa obiektu docelowego|Opis|  
|-----------------|-----------------|  
|`BeforeCompile`, `AfterCompile`|Zadania w jednej z następujących elementów docelowych uruchomienia przed lub po ukończeniu kompilacji core dodaje. Większość po dostosowaniu w jednym z następujących dwóch elementów docelowych.|  
|`BeforeBuild`, `AfterBuild`|Zadania wstawione w jednym z następujących elementów docelowych zostaną uruchomione, przed lub po wszystkich pozostałych w kompilacji. **Uwaga:** `BeforeBuild` i `AfterBuild` elementy docelowe są już zdefiniowane w komentarze na końcu większości plików projektów. Dzięki temu można łatwo dodać zdarzeń przed i po kompilacji do pliku projektu.|  
|`BeforeRebuild`, `AfterRebuild`|Zadania wstawione w jednym z następujących elementów docelowych uruchomienia przed lub jest wywoływany po podstawowe odbudować funkcji. Kolejność wykonywania docelowego w Microsoft.Common.targets jest: `BeforeRebuild`, `Clean`, `Build`, a następnie `AfterRebuild`.|  
|`BeforeClean`, `AfterClean`|Zadania wstawione w jednym z następujących elementów docelowych uruchomienia przed lub po podstawowe czysta funkcja jest wywoływana.|  
|`BeforePublish`, `AfterPublish`|Zadania wstawione w jednym z następujących elementów docelowych uruchomienia przed lub po podstawowe publikowanie funkcji jest wywoływany.|  
|`BeforeResolveReference`, `AfterResolveReferences`|Zadania wstawione w jednym z następujących elementów docelowych uruchomienia przed lub po rozwiązaniu odwołania do zestawów.|  
|`BeforeResGen`, `AfterResGen`|Zadania wstawione w jednej z następujących elementów docelowych uruchomienia przed lub po wygenerowaniu zasobów.|  
  
## <a name="overriding-dependson-properties"></a>Zastępowanie właściwości "DependsOn"  
 Zastępowanie wstępnie zdefiniowanych obiektów docelowych jest łatwe rozszerzanie procesu kompilacji, ale, ponieważ [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sekwencyjnie, ocenia definicji obiektów docelowych nie istnieje sposób można zapobiec inny projekt, który importuje zastępowaniu elementy docelowe projektu już zostały zastąpione. Tak, na przykład w ciągu ostatnich `AfterBuild` docelowych określonych w pliku projektu po inne projekty zostały zaimportowane, będzie używana podczas kompilacji.  
  
 Można zabezpieczyć się przed zastąpienia niezamierzonych celów przez zastąpienie właściwości "DependsOn", które są używane w `DependsOnTargets` atrybutów w całym pliku Microsoft.Common.targets. Na przykład `Build` docelowy zawiera `DependsOnTargets` wartość atrybutu `"$(BuildDependsOn)"`. Należy wziąć pod uwagę:  
  
```xml  
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>  
```  
  
 Ten element XML wskazuje, że przed `Build` element docelowy może zostać uruchomiony, wszystkie elementy docelowe określone w `BuildDependsOn` najpierw należy uruchomić właściwości. `BuildDependsOn` Właściwość jest zdefiniowana jako:  
  
```xml  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 Wartość tej właściwości można zastąpić przez zadeklarowanie inna właściwość o nazwie `BuildDependsOn` na końcu pliku projektu. W tym poprzedniej `BuildDependsOn` właściwości w nowej właściwości, można dodać nowe elementy docelowe na początku i końca listy docelowej. Na przykład:  
  
```xml  
<PropertyGroup>  
    <BuildDependsOn>  
        MyCustomTarget1;  
        $(BuildDependsOn);  
        MyCustomTarget2  
    </BuildDependsOn>  
</PropertyGroup>  
  
<Target Name="MyCustomTarget1">  
    <Message Text="Running MyCustomTarget1..."/>  
</Target>  
<Target Name="MyCustomTarget2">  
    <Message Text="Running MyCustomTarget2..."/>  
</Target>  
```  
  
 Projekty, które importują plików projektu można zastąpić te właściwości bez zastępowania dostosowań wprowadzonych przez użytkownika.  
  
#### <a name="to-override-a-dependson-property"></a>Aby zastąpić właściwość "DependsOn"  
  
1.  Określ wstępnie zdefiniowaną właściwość "DependsOn" w Microsoft.Common.targets, który chcesz zastąpić. Poniższa tabela listę właściwości często przesłoniętych "DependsOn".  
  
2.  Zdefiniuj inne wystąpienie tej właściwości lub właściwości na końcu pliku projektu. Zawiera właściwości oryginalnej, na przykład `$(BuildDependsOn)`, w nowej właściwości.  
  
3.  Zdefiniuj niestandardowe elementy docelowe, przed lub po definicji właściwości.  
  
4.  Tworzenie pliku projektu.  
  
### <a name="commonly-overridden-dependson-properties"></a>Powszechnie zastępowane właściwości "DependsOn"  
  
|Nazwa właściwości|Opis|  
|-------------------|-----------------|  
|`BuildDependsOn`|Właściwość do zastąpienia, jeśli chcesz wstawić niestandardowe obiekty docelowe, przed lub po kompilacji całego procesu.|  
|`CleanDependsOn`|Właściwość do zastąpienia, aby wyczyścić dane wyjściowe niestandardowe proces kompilacji.|  
|`CompileDependsOn`|Właściwość, aby zastąpić, jeśli chcesz wstawić niestandardowych procesów przed lub po wykonaniu kroku kompilacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Integration](../msbuild/visual-studio-integration-msbuild.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [. Pliki obiektów docelowych](../msbuild/msbuild-dot-targets-files.md)