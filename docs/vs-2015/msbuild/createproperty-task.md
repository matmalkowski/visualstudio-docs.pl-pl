---
title: CreateProperty — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 961f034f2bb508175d258259097f3be25e2a0b11
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42685545"
---
# <a name="createproperty-task"></a>CreateProperty — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CreateProperty — zadanie](https://docs.microsoft.com/visualstudio/msbuild/createproperty-task).  
  
  
Zostaną wyświetlone wszystkie właściwości wartości przekazane. Dzięki temu wartości, które mają być kopiowane z jedną właściwość lub ciągu do innego.  
  
## <a name="attributes"></a>Atrybuty  
 W poniższej tabeli opisano parametry `CreateProperty` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Value`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Określa wartość do skopiowania do nowej właściwości.|  
|`ValueSetByTask`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Zawiera taką samą wartość jak `Value` parametru. Użyj tego parametru, tylko wtedy, gdy chcesz uniknąć dane wyjściowe właściwością [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] po pomija otaczającego element docelowy, ponieważ dane wyjściowe są aktualne.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `CreateProperty` zadania do utworzenia `NewFile` przy użyciu kombinacji wartości właściwości `SourceFilename` i `SourceFileExtension` właściwości.  
  
```  
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
  
 Po uruchomieniu projektu, a wartość `NewFile` właściwość `Module1.vb`.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)



