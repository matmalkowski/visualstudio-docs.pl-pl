---
title: "Usingtask — Element (MSBuild) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UsingTask
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UsingTask element [MSBuild]
- <UsingTask> element [MSBuild]
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 79d87029365d5e527f886dc3c86ff260a0cbb612
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="usingtask-element-msbuild"></a>UsingTask — Element (MSBuild)
Mapuje zadanie, które odwołują się [zadań](../msbuild/task-element-msbuild.md) elementu do zestawu zawierającego implementację zadania.  

 \<Project>  
 \<UsingTask>  

## <a name="syntax"></a>Składnia  

```  
<UsingTask TaskName="TaskName"  
    AssemblyName = "AssemblyName"   
    TaskFactory = "ClassName"  
    Condition="'String A'=='String B'" />  
```  

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  

### <a name="attributes"></a>Atrybuty  

|Atrybut|Opis|  
|---------------|-----------------|  
|`AssemblyName`|Albo `AssemblyName` atrybutu lub `AssemblyFile` atrybut jest wymagany.<br /><br /> Nazwa zestawu do załadowania. `AssemblyName` Atrybut akceptuje zestawy o silnych nazwach, silne nazwy nie jest wymagany. Użycie tego atrybutu jest równoważne podczas ładowania zestawu przy użyciu <xref:System.Reflection.Assembly.Load%2A> metody w środowisku .NET.<br /><br /> Nie można użyć tego atrybutu, jeśli `AssemblyFile` atrybut jest używany.|  
|`AssemblyFile`|Albo `AssemblyName` lub `AssemblyFile` atrybut jest wymagany.<br /><br /> Ścieżka pliku zestawu. Ten atrybut akceptuje pełnych ścieżek lub ścieżek względnych. Ścieżki względne są względem katalogu projektu pliku lub plik elementów docelowych gdzie `UsingTask` jest zadeklarowany element. Użycie tego atrybutu jest równoważne podczas ładowania zestawu przy użyciu <xref:System.Reflection.Assembly.LoadFrom%2A> metody w środowisku .NET.<br /><br /> Nie można użyć tego atrybutu, jeśli `AssemblyName` atrybut jest używany.|  
|`TaskFactory`|Atrybut opcjonalny.<br /><br /> Określa klasę w zestawie, który jest odpowiedzialny za wygenerowanie wystąpień z określonym `Task` nazwy.  Użytkownik może również określić `TaskBody` jako element podrzędny, który fabryki zadań odbiera i używane w celu wygenerowania zadania. Zawartość `TaskBody` są specyficzne dla fabryki zadań.|  
|`TaskName`|Atrybut wymagany.<br /><br /> Nazwa zadania, aby odwołać się z zestawu. Możliwe są niejednoznaczności, ten atrybut należy zawsze podać pełną przestrzeni nazw. W przypadku niejednoznaczności MSBuild wybierze dowolnego dopasowania, mogą powodować nieoczekiwane wyniki.|  
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do oceny. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Elementy podrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Zestaw parametrów, które są wyświetlane zadania, który jest generowany przez określony `TaskFactory`.|  
|[Zadanie](../msbuild/task-element-msbuild.md)|Dane, które są przekazywane do `TaskFactory` można wygenerować wystąpienia zadania.|  

### <a name="parent-elements"></a>Elementy nadrzędne  

|Element|Opis|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Wymaganego głównego elementu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu.|  

## <a name="remarks"></a>Uwagi  
 Zmienne środowiskowe, właściwości wiersza polecenia i właściwości na poziomie projektu może być dowolnym przywoływany w `UsingTask` elementu, jeśli występuje on w pliku projektu bezpośrednio lub za pośrednictwem zaimportowanego pliku projektu. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).  

> [!NOTE]
>  Właściwości na poziomie projektu mają żadnego znaczenia, jeśli `UsingTask` element pochodzi z jednego z plików .tasks, które są globalnie zarejestrowane z aparatu MSBuild. Właściwości na poziomie projektu nie są globalne dla programu MSBuild.  

 W programu MSBuild w wersji 4.0 za pomocą zadań mogą być ładowane z .overridetask plików.  

## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `UsingTask` element z `AssemblyName` atrybutu.  

```xml  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody>  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  

## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `UsingTask` element z `AssemblyFile` atrybutu.  

```xml  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  

## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
