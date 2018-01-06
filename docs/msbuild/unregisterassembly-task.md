---
title: "Unregisterassembly — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#UnregisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UnregisterAssembly task
- UnregisterAssembly task [MSBuild]
ms.assetid: 04f549dd-3591-4dda-9c3a-cf6ede9df2c3
caps.latest.revision: "21"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f1f2f0826b89a7a06d1682d4c991087f29c274c9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly — Zadanie
Wyrejestrowuje określonych zestawów do COM interop celów. Wykonuje odwrotnej [registerassembly — zadanie](../msbuild/registerassembly-task.md).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `UnregisterAssembly` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Assemblies`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa zestawy, które ma być wyrejestrowany.|  
|`AssemblyListFile`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Zawiera informacje o stanie między `RegisterAssembly` zadań i `UnregisterAssembly` zadań. Zapobiega to zadanie próby wyrejestrować zestawu, którego nie udało się zarejestrować w `RegisterAssembly` zadań.<br /><br /> Jeśli ten parametr jest określony, `Assemblies` i `TypeLibFiles` parametry są ignorowane.|  
|`TypeLibFiles`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Wyrejestrowuje określonej biblioteki typów z określonego zestawu. **Uwaga:** ten parametr tylko jest to konieczne, jeśli nazwa pliku biblioteki typów różni się od nazwy zestawu.|  
  
## <a name="remarks"></a>Uwagi  
 Nie jest wymagane, czy zestaw istnieje dla tego zadania powiódł się. Przy próbie wyrejestrować zestawu, który nie istnieje, zadanie powiedzie się ostrzeżenie. Dzieje się tak, ponieważ to zadanie to zadanie do usunięcia rejestracji zestawu z rejestru. Jeśli zestaw nie istnieje, nie znajduje się w rejestrze i w związku z tym zadanie zakończyło się pomyślnie.  
  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension> dziedziczy klasa, która sama <xref:System.MarshalByRefObject> klasy. `MarshalByRefObject` Klasy zapewnia te same funkcje co <xref:Microsoft.Build.Utilities.Task> klasy, ale można wdrożyć w domenie aplikacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `UnregisterAssembly` zadań można wyrejestrować zestawu w ścieżce określonej przez `OutputPath` i `FileName` właściwości, jeśli istnieje.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <OutputPath>\Output\</OutputPath>  
        <FileName>MyFile.dll</FileName>  
    </PropertyGroup>  
    <Target Name="UnregisterAssemblies">  
        <UnregisterAssembly  
            Condition="Exists('$(OutputPath)$(FileName)')"  
            Assemblies="$(OutputPath)$(FileName)" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Registerassembly — zadanie](../msbuild/registerassembly-task.md)   
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)