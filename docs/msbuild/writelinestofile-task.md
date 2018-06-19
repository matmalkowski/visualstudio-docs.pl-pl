---
title: Writelinestofile — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f321eadf4fa02d55e869dcc0d9c93b637a2d3ac3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31578383"
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