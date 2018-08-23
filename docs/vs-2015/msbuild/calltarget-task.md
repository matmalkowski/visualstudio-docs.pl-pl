---
title: Calltarget — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d12fde1654c4645a6b543e44f8c48f273f32349b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42694191"
---
# <a name="calltarget-task"></a>CallTarget — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [calltarget — zadanie](https://docs.microsoft.com/visualstudio/msbuild/calltarget-task).  
  
  
Wywołuje określonych celów w pliku projektu.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `CallTarget` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`RunEachTargetSeparately`|Opcjonalnie `Boolean` parametr wyjściowy.<br /><br /> Jeśli `true`, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] aparat jest wywoływana jeden raz na docelowym. Jeśli `false`, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] aparat jest wywoływana jeden raz do tworzenia wszystkich obiektów docelowych. Wartość domyślna to `false`.|  
|`TargetOutputs`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera dane wyjściowe wszystkich skompilowanych elementów docelowych.|  
|`Targets`|Opcjonalnie `String[]` parametru.<br /><br /> Określa cel lub cele do kompilacji.|  
|`UseResultsCache`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, buforowane wynik jest zwracany, jeśli jest obecny.<br /><br /> **Uwaga** podczas MSBuild, zadanie zostanie uruchomione, dane wyjściowe są buforowane w zakresie (ProjectFileName, GlobalProperties) [TargetNames] jako listę elementów kompilacji.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli obiekt docelowy określony w `Targets` kończy się niepowodzeniem i `RunEachTargetSeparately` jest `true`, zadania w dalszym ciągu kompilacji pozostałe elementy docelowe.  
  
 Do kompilacji domyślnych elementów docelowych, należy użyć [zadanie MSBuild](../msbuild/msbuild-task.md) i ustaw `Projects` równa parametr `$(MSBuildProjectFile)`.  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wywołuje `TargetA` z wewnątrz `CallOtherTargets`.  
  
```  
<Project DefaultTargets="CallOtherTargets"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <Target Name="CallOtherTargets">  
        <CallTarget Targets="TargetA"/>  
    </Target>  
  
    <Target Name="TargetA">  
        <Message Text="Building TargetA..." />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Docelowe elementy](../msbuild/msbuild-targets.md)



