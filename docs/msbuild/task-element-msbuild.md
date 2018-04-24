---
title: Zadanie — Element (MSBuild) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc67d881f48c99cd8e53de086f0c8b08c96d7844
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="task-element-msbuild"></a>Task — Element (MSBuild)
Tworzy i wykonuje wystąpienia [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadań. Nazwa elementu jest określana przez nazwę zadania tworzenia.  

 \<Project>  
 \<Docelowy >  

## <a name="syntax"></a>Składnia  

```  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  

### <a name="attributes"></a>Atrybuty  

|Atrybut|Opis|  
|---------------|-----------------|  
|`Condition`|Atrybut opcjonalny. Warunek do sprawdzenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Atrybut opcjonalny. Może zawierać jedną z następujących wartości:<br /><br /> -   **WarnAndContinue** lub **true**. Jeśli zadanie nie powiedzie się, kolejne zadania w [docelowej](../msbuild/target-element-msbuild.md) element i kompilacji, nadal można wykonać, a wszystkie błędy z zadania są traktowane jako ostrzeżenia.<br />-   **ErrorAndContinue**. Jeśli zadanie nie powiedzie się, kolejne zadania w `Target` element i kompilacji, nadal można wykonać, a wszystkie błędy z zadania są traktowane jako błędy.<br />-   **ErrorAndStop** lub **false** (ustawienie domyślne). Jeśli zadanie nie powiedzie się, kolejnych zadań na `Target` element i kompilacji nie są wykonywane i całą `Target` element i kompilacji jest traktowane jako powiodła się.<br /><br /> Wersje programu .NET Framework, przed 4.5 obsługiwane tylko `true` i `false` wartości.<br /><br /> Aby uzyskać więcej informacji, zobacz [porady: ignorowanie błędów w zadaniach](../msbuild/how-to-ignore-errors-in-tasks.md).|  
|`Parameter`|Wymagane, jeśli klasa zadania zawiera jeden lub więcej właściwości etykietą `[Required]` atrybutu.<br /><br /> Parametr zadania zdefiniowane przez użytkownika, który zawiera wartość parametru jako jego wartość. Może to być dowolna liczba parametrów w `Task` element z każdy jest mapowany na właściwość platformy .NET w klasie zadań.|  

### <a name="child-elements"></a>Elementy podrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[Output](../msbuild/output-element-msbuild.md)|Magazyny danych wyjściowych z zadania w pliku projektu. Może wynosić zero lub więcej `Output` elementów w zadaniu.|  

### <a name="parent-elements"></a>Elementy nadrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[docelowy](../msbuild/target-element-msbuild.md)|Element kontenera dla [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadania.|  

## <a name="remarks"></a>Uwagi  
 A `Task` element [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu powoduje utworzenie wystąpienia zadania, ustawia właściwości i go uruchomi. `Output` Element przechowuje parametry wyjściowe właściwości lub elementy do użycia w innym miejscu w pliku projektu.  

 Czy istnieją jakieś [OnError](../msbuild/onerror-element-msbuild.md) elementów w obiekcie nadrzędnym `Target` element zadania, one będą nadal oceniane Jeśli zadanie nie powiedzie się i `ContinueOnError` ma wartość `false`. Aby uzyskać więcej informacji na temat zadań, zobacz [zadania](../msbuild/msbuild-tasks.md).  

## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy wystąpienie [CSC — zadanie](../msbuild/csc-task.md) klasy, ustawia sześć właściwości, a następnie wykonuje zadanie. Po wykonaniu wartość `OutputAssembly` właściwości obiektu jest umieszczany w listy elementów o nazwie `FinalAssemblyName`.  

```xml  
<Target Name="Compile" DependsOnTarget="Resources" >  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  

## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
