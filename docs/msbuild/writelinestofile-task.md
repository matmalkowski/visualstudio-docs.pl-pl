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
ms.openlocfilehash: 062270864c3fecb6556ef9b48d00177966a41859
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233025"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile — zadanie
Zapisuje ścieżek określonych elementów do określonego pliku.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `WriteLinestoFile` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`File`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa plik do elementów do zapisania.|  
|`Lines`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa elementy do zapisu w pliku.|  
|`Overwrite`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie zastępuje istniejącą zawartość w pliku.|  
|`Encoding`|Opcjonalnie `String` parametru.<br /><br /> Wybiera kodowanie, na przykład "Unicode" znaków.  Zobacz też <xref:System.Text.Encoding>.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `Overwrite` jest `true`, tworzy nowy plik, zapisywania zawartości pliku, a następnie zamyka plik. Jeśli plik docelowy już istnieje, zostanie zastąpiony. Jeśli `Overwrite` jest `false`, dołącza zawartość do pliku, tworzenia pliku docelowego, jeśli jeszcze nie istnieje.  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `WriteLinesToFile` zadanie, aby zapisać ścieżki elementów w `MyItems` elementu kolekcji do pliku określonego przez `MyTextFile` elementu kolekcji.  
  
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
  
## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)