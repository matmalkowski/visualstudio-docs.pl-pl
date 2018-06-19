---
title: Calltarget — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83240cfa9deec2585aaa23db4aa79fbfe6929b09
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31571675"
---
# <a name="calltarget-task"></a>CallTarget — Zadanie
Wywołuje określone elementy docelowe w pliku projektu.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `CallTarget` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`RunEachTargetSeparately`|Opcjonalne `Boolean` parametru wejściowego.<br /><br /> Jeśli `true`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] aparat jest wywoływana raz na docelowy. Jeśli `false`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] aparat jest wywoływana raz w celu zbudowania wszystkie elementy docelowe. Wartość domyślna to `false`.|  
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
 [Docelowe elementy](../msbuild/msbuild-targets.md)