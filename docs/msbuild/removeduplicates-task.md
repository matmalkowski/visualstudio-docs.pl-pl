---
title: Removeduplicates — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/01/2018
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RemoveDuplicates task
- RemoveDuplicates task [MSBuild]
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 596c066018a5f6f731c4ca0cefbefae458646ec1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="removeduplicates-task"></a>RemoveDuplicates — Zadanie
Usuwa zduplikowane elementy z kolekcji określony element.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `RemoveDuplicates` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Filtered`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Zawiera kolekcję elementów z wszystkie zduplikowane elementy usunięte. Jest zachowana kolejność elementów wejściowych utrzymywanie pierwszego wystąpienia każdej zduplikowanego elementu.|  
|`Inputs`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Aby usunąć zduplikowane elementy z kolekcji elementów.|  
  
## <a name="remarks"></a>Uwagi  
 To zadanie jest uwzględniana wielkość liter i nie porównuje metadanych elementu podczas określania duplikaty.  
  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `RemoveDuplicates` zadań w celu usunięcia zduplikowane elementy z `MyItems` Kolekcja elementów. Po zakończeniu zadania `FilteredItems` kolekcji elementów zawiera jeden element.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyItems Include="MyFile.cs"/>  
        <MyItems Include="MyFile.cs">  
            <Culture>fr</Culture>  
        </MyItems>  
        <MyItems Include="myfile.cs"/>  
    </ItemGroup>  
  
    <Target Name="RemoveDuplicateItems">  
        <RemoveDuplicates  
            Inputs="@(MyItems)">  
            <Output  
                TaskParameter="Filtered"  
                ItemName="FilteredItems"/>  
        </RemoveDuplicates>  
    </Target>  
</Project>  
```  

 W poniższym przykładzie pokazano, że `RemoveDuplicates` zadań zachowuje ich kolejność wprowadzania. Po zakończeniu zadania `FilteredItems` kolekcji elementów zawiera elementy "MyFile2.cs", "MyFile1.cs" i "MyFile3.cs" w tej kolejności.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyItems Include="MyFile2.cs"/>  
        <MyItems Include="MyFile1.cs" />  
        <MyItems Include="MyFile3.cs" />  
        <MyItems Include="myfile1.cs"/>  
    </ItemGroup>  
  
    <Target Name="RemoveDuplicateItems">  
        <RemoveDuplicates  
            Inputs="@(MyItems)">  
            <Output  
                TaskParameter="Filtered"  
                ItemName="FilteredItems"/>  
        </RemoveDuplicates>  
    </Target>  
</Project>  
```  

## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Zadania](../msbuild/msbuild-tasks.md)
