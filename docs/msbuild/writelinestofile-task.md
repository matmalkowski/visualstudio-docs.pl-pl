---
title: "Writelinestofile — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: "9"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1c284fefa1ed296e08049bd5bb7ea5df757107ce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="writelinestofile-task"></a>WriteLinesToFile — Zadanie
Zapisuje ścieżek określonych elementów do określonego pliku.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `WriteLinestoFile` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`File`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa plik do elementów do zapisu.|  
|`Lines`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa elementy do zapisu w pliku.|  
|`Overwrite`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie zastępuje istniejącą zawartość w pliku.|  
|`Encoding`|Opcjonalne `String` parametru.<br /><br /> Wybiera kodowanie, na przykład "Unicode" znaków.  Zobacz też <xref:System.Text.Encoding>.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `Overwrite` jest `true`, tworzy nowy plik, zapisanie zawartości pliku, a następnie zamyka plik. Jeśli plik docelowy już istnieje, zostanie zastąpiony. Jeśli `Overwrite` jest `false`, dołącza zawartość do pliku, tworzenie pliku docelowego, jeśli jeszcze nie istnieje.  
  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `WriteLinesToFile` zadanie, aby zapisać ścieżki elementów w `MyItems` elementu kolekcji do pliku określonego przez `MyTextFile` Kolekcja elementów.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)