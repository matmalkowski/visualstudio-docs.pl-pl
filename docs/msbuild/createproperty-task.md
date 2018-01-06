---
title: "CreateProperty — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
caps.latest.revision: "11"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9ae7e6d5203ac4f2b6ff58a19d4938180b7a11c3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="createproperty-task"></a>CreateProperty — Zadanie
Wypełnia właściwości z wartości przekazane. Dzięki temu wartości do skopiowania z jedną właściwość lub ciągu na inny.  
  
## <a name="attributes"></a>Atrybuty  
 W poniższej tabeli opisano parametry `CreateProperty` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Value`|Opcjonalne `String` parametru wyjściowego.<br /><br /> Określa wartość do skopiowania do nowej właściwości.|  
|`ValueSetByTask`|Opcjonalne `String` parametru wyjściowego.<br /><br /> Zawiera taką samą wartość jak `Value` parametru. Tego parametru należy użyć tylko w przypadku, gdy chce się uniknąć określone przez właściwość danych wyjściowych [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] po pomija otaczającego obiekt docelowy, ponieważ dane wyjściowe są aktualne.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `CreateProperty` zadanie tworzenia `NewFile` przy użyciu kombinacji wartości właściwości `SourceFilename` i `SourceFileExtension` właściwości.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <SourceFilename>Module1</SourceFilename>  
        <SourceFileExtension>vb</SourceFileExtension>  
    </PropertyGroup>  
  
    <Target Name="CreateProperties">  
  
        <CreateProperty  
            Value="$(SourceFilename).$(SourceFileExtension)">  
            <Output  
                TaskParameter="Value"  
                PropertyName="NewFile" />  
        </CreateProperty>  
  
    </Target>  
  
</Project>  
```  
  
 Po uruchomieniu projektu, wartość `NewFile` jest właściwość `Module1.vb`.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)