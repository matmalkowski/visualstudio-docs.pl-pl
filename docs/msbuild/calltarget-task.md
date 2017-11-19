---
title: "Calltarget — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
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
caps.latest.revision: "6"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: e88638d83a0d5920727e531f7101d4230abcce7c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="calltarget-task"></a>CallTarget — Zadanie
Wywołuje określone elementy docelowe w pliku projektu.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `CallTarget` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`RunEachTargetSeparately`|Opcjonalne `Boolean` parametru wyjściowego.<br /><br /> Jeśli `true`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] aparat jest wywoływana raz na docelowy. Jeśli `false`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] aparat jest wywoływana raz w celu zbudowania wszystkie elementy docelowe. Wartość domyślna to `false`.|  
|`TargetOutputs`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Zawiera wszystkie elementy docelowe wbudowanych dane wyjściowe.|  
|`Targets`|Opcjonalne `String[]` parametru.<br /><br /> Określa docelowy lub obiekty docelowe do skompilowania.|  
|`UseResultsCache`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, buforowane wynik jest zwracany, jeśli jest obecny.<br /><br /> **Uwaga** MSBuild gdy zadanie zostanie uruchomione, dane wyjściowe są buforowane w zakresie (ProjectFileName, GlobalProperties) [TargetNames] jako listę pozycji kompilacji.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli element docelowy określony w `Targets` nie powiedzie się i `RunEachTargetSeparately` jest `true`, zadanie kontynuuje tworzenie pozostałe elementy docelowe.  
  
 Jeśli chcesz utworzyć domyślne elementy docelowe, użyj [zadanie programu MSBuild](../msbuild/msbuild-task.md) i ustaw `Projects` parametru równa `$(MSBuildProjectFile)`.  
  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Następujące przykładowe wywołania `TargetA` z wewnątrz `CallOtherTargets`.  
  
```xml  
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
 [Obiekty docelowe](../msbuild/msbuild-targets.md)