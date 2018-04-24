---
title: Zadanie MSBuild | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MSBuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild task [MSBuild]
- MSBuild, MSBuild task
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04b76df9a174bcbc03269e42ce37b1103c3bfd2f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="msbuild-task"></a>Zadanie MSBuild
Tworzy [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektów z innego [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektu.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `MSBuild` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`BuildInParallel`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, projekty określone w `Projects` parametru są wbudowane równolegle, jeśli jest to możliwe. Wartość domyślna to `false`.|  
|`Projects`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki projektu do kompilacji.|  
|`Properties`|Opcjonalne `String` parametru.<br /><br /> Rozdzielana średnikami lista par nazwa/wartość właściwości dotyczyć jako globalnych właściwości projektu podrzędnego. Po określeniu tego parametru jest funkcjonalnym odpowiednikiem ustawienie właściwości, które mają **/property** przełącznika podczas kompilowania z [MSBuild.exe](../msbuild/msbuild-command-line-reference.md). Na przykład:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Podczas przekazywania właściwości do projektu przy użyciu `Properties` parametru [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] tworzy nowe wystąpienie projektu, nawet jeśli plik projektu został już załadowany. Podczas tworzenia nowego wystąpienia projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] traktuje go jako inny projekt, który ma inne właściwości globalne i mogą być wbudowane równolegle z innymi wystąpieniami projektu. Na przykład konfiguracji wydanie można utworzyć w tym samym czasie co Konfiguracja debugowania.|  
|`RebaseOutputs`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, względnych ścieżek docelowych output elementy z skompilowanych projektach mają ich ścieżek dostosowuje się względem wywoływania projektu. Wartość domyślna to `false`.|  
|`RemoveProperties`|Opcjonalne `String` parametru.<br /><br /> Określa zbiór właściwości globalne do usunięcia.|  
|`RunEachTargetSeparately`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadań wywołuje każdego obiektu docelowego na liście, który został przekazany do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pojedynczo, a nie w tym samym czasie. Ustawienie tego parametru `true` gwarantuje, że kolejne elementy docelowe są wywoływane nawet wtedy, gdy wcześniej wywołana elementów docelowych nie powiodło się. W przeciwnym razie błąd kompilacji przestaną wywołania wszystkie kolejne elementy docelowe. Wartość domyślna to `false`.|  
|`SkipNonexistentProjects`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, pliki projektu, które nie istnieją na dysku zostanie pominięte. W przeciwnym razie takich projektów spowoduje błąd.|  
|`StopOnFirstFailure`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, gdy jeden z projektów nie można tworzyć, zostaną skompilowane żadne projekty więcej. Obecnie nie jest to obsługiwane podczas kompilowania równolegle (z wielu procesorów).|  
|`TargetAndPropertyListSeparators`|Opcjonalne `String[]` parametru.<br /><br /> Określa listę elementów docelowych i właściwości jako `Project` metadanych elementu). Separatory będzie niezmieniony przed rozpoczęciem przetwarzania. np. % 3B (zmienionym znaczeniu ";") będzie traktowana tak, jakby był on niezmieniony ";".|  
|`TargetOutputs`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy tylko do odczytu.<br /><br /> Zwraca dane wyjściowe wbudowanych elementów docelowych z wszystkie pliki projektu. Tylko dane wyjściowe z elementów docelowych, które zostały określone są zwracane, nie wszystkie dane wyjściowe, które mogą istnieć dla elementów docelowych, które zależą od tych celów.<br /><br /> `TargetOutputs` Parametr zawiera również następujące metadane:<br /><br /> -   `MSBuildSourceProjectFile`: [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Pliku projektu, który zawiera element docelowy, który ustawić dane wyjściowe.<br />-   `MSBuildSourceTargetName`: Element docelowy, który ustawić dane wyjściowe. **Uwaga:** Jeśli chcesz zidentyfikować dane wyjściowe z każdego pliku projektu lub docelowe oddzielnie, uruchom `MSBuild` zadań osobno dla każdego pliku projektu lub docelowego. Po uruchomieniu `MSBuild` zadanie tylko raz, aby utworzyć pliki projektu, dane wyjściowe wszystkie elementy docelowe są zbierane w tablicy.|  
|`Targets`|Opcjonalne `String` parametru.<br /><br /> Określa docelowy lub obiekty docelowe do skompilowania w plikach projektu. Użyj średnika do rozdzielenia lista nazw docelowych. Jeśli nie określono elementów docelowych w `MSBuild` są wbudowane zadanie, domyślne elementy docelowe, określona w plikach projektu. **Uwaga:** elementy docelowe muszą występować we wszystkich plikach projektu. Jeśli nie, występuje błąd kompilacji.|  
|`ToolsVersion`|Opcjonalne `String` parametru.<br /><br /> Określa `ToolsVersion` do użycia podczas tworzenia projektów przekazany do tego zadania.<br /><br /> Umożliwia [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadań do tworzenia projektu, którego celem jest inna wersja [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] niż określona w projekcie. Prawidłowe wartości to `2.0`, `3.0` i `3.5`. Wartość domyślna to `3.5`.|  
|`UnloadProjectsOnCompletion`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, projekt zostanie zwolniona po zakończeniu operacji.|  
|`UseResultsCache`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, buforowane wynik zostanie zwrócony, jeśli jest obecny. Jeśli theMSBuild zadanie zostanie uruchomione, wynik będą buforowane w zakresie (ProjectFileName, GlobalProperties) [TargetNames]<br /><br /> jako listę pozycji kompilacji|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
 W przeciwieństwie do usługi [zadanie Exec](../msbuild/exec-task.md) zacząć MSBuild.exe to zadanie wykorzystuje takie same [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] procesu w projektach kompilacji elementu podrzędnego. Lista już utworzone obiekty docelowe, które mogą być pominięte jest udostępniana między kompilacje nadrzędnych i podrzędnych. To zadanie jest również szybciej ponieważ żadna nowa [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proces został utworzony.  
  
 To zadanie może przetworzyć nie tylko pliki projektu, ale także pliki rozwiązania.  
  
 Całą konfigurację, która jest wymagana przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Aby włączyć projektów do kompilacji w tym samym czasie, nawet jeśli konfiguracja obejmuje zdalnego infrastruktury (na przykład portów, protokoły przekroczeń limitu czasu, ponownych prób i tak dalej), należy dokonać można skonfigurować przy użyciu plik konfiguracji. Jeśli to możliwe, elementy konfiguracji powinno być możliwe można określić jako parametry zadania na `MSBuild` zadań.  
  
 Począwszy od [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, teraz powierzchni TargetOutputs ze wszystkich podprojekty tworzenia projektów rozwiązania.  
  
## <a name="passing-properties-to-projects"></a>Przenoszenie właściwości do projektów  
 W wersjach [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] przed [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, przekazywanie różnych zestawów właściwości do różnych projektów na liście [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] elementu była utrudniona. Użycie atrybutu właściwości [zadanie programu MSBuild](../msbuild/msbuild-task.md), a następnie jego ustawienia została zastosowana do wszystkich projektów konstruowany, o ile nie można umieścić w zadaniu wsadowym [zadanie programu MSBuild](../msbuild/msbuild-task.md) i warunkowo dostępne różne właściwości dla każdego projektu w listy elementów.  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, jednak zapewnia dwie nowe zastrzeżone metadane elementów, właściwości i parametr AdditionalProperties umożliwia elastyczny sposób przekazywania inne właściwości różnych projektów jest utworzony przy użyciu [zadanie programu MSBuild](../msbuild/msbuild-task.md).  
  
> [!NOTE]
>  Te nowe elementy metadanych mają zastosowanie tylko do elementów przekazany w atrybucie projekty [zadanie programu MSBuild](../msbuild/msbuild-task.md).  
  
## <a name="multi-processor-build-benefits"></a>Korzyści kompilacji wieloprocesorowej  
 Jedną z najważniejszych zalet przy użyciu tej nowej metadanych występuje podczas kompilacji projektów równolegle w systemie wieloprocesorowym. Metadane umożliwia konsolidowanie wszystkie projekty w pojedynczy [zadanie programu MSBuild](../msbuild/msbuild-task.md) wywołania bez konieczności wykonywania żadnych przetwarzanie wsadowe lub warunkowego [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadania. I gdy jest wywoływana tylko jeden [zadanie programu MSBuild](../msbuild/msbuild-task.md), wszystkie projekty wymienione w atrybucie projekty zostaną skompilowane równolegle. (Tylko w przypadku jednak, jeśli `BuildInParallel=true` atrybutu znajduje się w [zadanie programu MSBuild](../msbuild/msbuild-task.md).) Aby uzyskać więcej informacji, zobacz [tworzenie wielu projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).  
  
## <a name="properties-metadata"></a>Właściwości metadanych  
 Typowy scenariusz obejmuje podczas tworzenia wielu plików rozwiązania przy użyciu [zadanie programu MSBuild](../msbuild/msbuild-task.md), tylko przy użyciu różnych kompilacji konfiguracji. Może zajść potrzeba kompilacji a1 rozwiązania przy użyciu a2 konfiguracji i rozwiązaniu debugowania przy użyciu konfiguracji wydanie. W [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, ten plik projektu będzie wyglądać podobnie do następującej:  
  
> [!NOTE]
>  W poniższym przykładzie "..." reprezentuje pliki dodatkowe rozwiązania.  
  
### <a name="aproj"></a>a.proj  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
 Przy użyciu metadanych właściwości, jednak można uprościć tutaj, aby użyć pojedynczego [zadanie programu MSBuild](../msbuild/msbuild-task.md), jak pokazano w poniższych:  
  
### <a name="aproj"></a>a.proj  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln...">  
            <Properties>Configuration=Debug</Properties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"/>  
    </Target>  
</Project>  
```  
  
 \- lub -  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln..."/>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Debug"/>  
    </Target>  
</Project>  
```  
  
## <a name="additionalproperties-metadata"></a>Dodatkowe właściwości metadanych  
 Rozważmy poniższy scenariusz, w którym tworzysz dwa pliki rozwiązania przy użyciu [zadanie programu MSBuild](../msbuild/msbuild-task.md), zarówno przy użyciu konfiguracji wydanie, ale go przy użyciu x86 architektury i innych za pomocą o architekturze ia64. W [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, trzeba utworzyć wiele wystąpień [zadanie programu MSBuild](../msbuild/msbuild-task.md): jeden do tworzenia projektu przy użyciu konfiguracji wydanie z x86 architektury, innych przy użyciu konfiguracji wydanie z ia64 Architektura. Plik projektu może wyglądać następująco:  
  
### <a name="aproj"></a>a.proj  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Release;   
          Architecture=x86"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;   
          Architecture=ia64"/>  
    </Target>  
</Project>  
```  
  
 Posługując się metadanymi parametr AdditionalProperties, można uprościć tutaj, aby użyć pojedynczego [zadanie programu MSBuild](../msbuild/msbuild-task.md) przy użyciu następujących czynności:  
  
### <a name="aproj"></a>a.proj  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln...">  
            <AdditionalProperties>Architecture=x86  
              </AdditionalProperties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <AdditionalProperties>Architecture=ia64  
              </AdditionalProperties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `MSBuild` zadań do kompilacji projektów określony przez `ProjectReferences` Kolekcja elementów. Wynikowy obiekt docelowy wyjściowe są przechowywane w `AssembliesBuiltByChildProjects` Kolekcja elementów.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ProjectReferences Include="*.*proj" />  
    </ItemGroup>  
  
    <Target Name="BuildOtherProjects">  
        <MSBuild  
            Projects="@(ProjectReferences)"  
            Targets="Build">  
            <Output  
                TaskParameter="TargetOutputs"  
                ItemName="AssembliesBuiltByChildProjects" />  
        </MSBuild>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)