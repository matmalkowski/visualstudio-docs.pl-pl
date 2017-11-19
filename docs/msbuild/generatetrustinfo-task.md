---
title: "Generatetrustinfo — zadanie | Dokumentacja firmy Microsoft"
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
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 9360cce21ab859e962734e240977c67627b8739f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo — Zadanie
Generuje zaufanie aplikacji w manifeście podstawowej i z `TargetZone` i `ExcludedPermissions` parametrów.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `GenerateTrustInfo` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ApplicationDependencies`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa zestawów zależnych.|  
|`BaseManifest`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa podstawowy manifest można wygenerować zaufanie aplikacji z.|  
|`ExcludedPermissions`|Opcjonalne `String` parametru.<br /><br /> Określa jedną lub więcej wartości tożsamości oddzielonych średnikami uprawnienia mają zostać wykluczone z domyślnego zestawu uprawnień strefy.|  
|`TargetZone`|Opcjonalne `String` parametru.<br /><br /> Określa zestaw uprawnień domyślne strefy, które są uzyskiwane z zasad komputera.|  
|`TrustInfoFile`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru wyjściowego.<br /><br /> Określa plik, który zawiera informacje dotyczące zaufania zabezpieczeń aplikacji.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)