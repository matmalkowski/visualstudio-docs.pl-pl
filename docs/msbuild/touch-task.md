---
title: "Touch — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#Touch
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Touch task
- Touch task [MSBuild]
ms.assetid: 8a978645-1393-4904-ae69-42afabd8c109
caps.latest.revision: "17"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 459cea5aa39ae718fddbd97114528b45ddc460c6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="touch-task"></a>Touch — Zadanie
Ustawia czas dostępu i modyfikacji plików.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `Touch` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AlwaysCreate`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, tworzy pliki, które jeszcze nie istnieje.|  
|`Files`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa kolekcję plików do touch.|  
|`ForceTouch`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, wymusza touch plik, nawet jeśli pliki są tylko do odczytu.|  
|`Time`|Opcjonalne `String` parametru.<br /><br /> Określa czas niż bieżący czas. Format musi być format, która jest zgodna z <xref:System.DateTime.Parse%2A> metody.|  
|`TouchedFiles`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Zawiera kolekcję elementów, których odwoływały pomyślnie.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Touch` zadań, aby zmienić czas dostępu i modyfikacji plików określonych w `Files` elementu kolekcji i umieszcza na liście plików pomyślnie dotknąć w `FilesTouched` Kolekcja elementów.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
<ItemGroup>  
    <Files Include="File1.cs;File2.cs;File3.cs" />  
</ItemGroup>  
  
    <Target Name="TouchFiles">  
        <Touch  
            Files="@(Files)">  
            <Output  
                TaskParameter="TouchedFiles"  
                ItemName="FilesTouched"/>  
    </Touch>  
</Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)