---
title: "Registerassembly — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RegisterAssembly task
- RegisterAssembly task [MSBuild]
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 9d4d1f5cda41fd7c72d32feda40f62d691a0d3cd
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="registerassembly-task"></a>RegisterAssembly — Zadanie
Odczytuje metadanych w obrębie określonego zestawu i dodaje niezbędne wpisy w rejestrze, dzięki czemu klienci COM utworzyć [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] klas w sposób niewidoczny dla użytkownika. Zachowanie tego zadania jest podobny, ale nie są identyczne, te [Regasm.exe (narzędzie rejestracji zestawów)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `RegisterAssembly` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Assemblies`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa zestawy, które ma zostać zarejestrowany z modelu COM.|  
|`AssemblyListFile`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Zawiera informacje o stanie między `RegisterAssembly` zadań i [unregisterassembly —](../msbuild/unregisterassembly-task.md) zadań. Zapobiega to `UnregisterAssembly` zadań z próby wyrejestrować zestawu, którego nie udało się zarejestrować w `RegisterAssembly` zadań.|  
|`CreateCodeBase`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, tworzy codebase wpis w rejestrze, który określa ścieżkę do zestawu, który nie jest zainstalowany w globalnej pamięci podręcznej zestawów. Nie należy określać tej opcji, jeśli później instalowany będzie zestaw, który jest rejestrowany w globalnej pamięci podręcznej zestawów.|  
|`TypeLibFiles`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Określa bibliotekę typów, aby wygenerować z określonego zestawu. Biblioteka wygenerowanego typu zawiera definicje dostępne typy zdefiniowane w zestawie. Biblioteki typów jest generowany tylko, jeśli jest spełniony jeden z następujących czynności:<br /><br /> -Biblioteki typów o tej nazwie nie istnieje w tej lokalizacji.<br />-Biblioteki typów istnieje, ale jest starszy niż zestaw przekazywany.<br /><br /> Jeśli biblioteka typów jest nowsza niż zestaw przekazywany, nie zostanie utworzony nowy, ale nadal będzie można zarejestrować zestawu.<br /><br /> Jeśli ten parametr jest określony, musi mieć taką samą liczbę elementów jako `Assemblies` parametru lub zadanie zakończy się niepowodzeniem. Jeśli nie określono żadnych danych wejściowych, zadanie zostanie domyślnie nazwa zestawu i zmień rozszerzenie elementu .tlb.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `RegisterAssembly` zadań można zarejestrować zestawu określony przez `MyAssemblies` Kolekcja elementów.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="MyAssembly.dll" />  
    <ItemGroup>  
  
    <Target Name="RegisterAssemblies">  
        <RegisterAssembly  
            Assemblies="@(MyAssemblies)" >  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)