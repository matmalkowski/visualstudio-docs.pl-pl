---
title: Createitem — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateItem
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateItem task [MSBuild]
- MSBuild, CreateItem task
ms.assetid: c4311f38-979e-4324-b524-9e8c1cbdc41a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fc9ccb3788246e359183cff889f0996b4e74aecb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31577486"
---
# <a name="createitem-task"></a>CreateItem — Zadanie
Wypełnia kolekcji elementów z elementów wejściowych. Dzięki temu elementów do skopiowania z listy jeden do innego.  
  
> [!NOTE]
>  To zadanie jest przestarzały. W programie .NET Framework 3.5, element grupy może zostać umieszczony w [docelowej](../msbuild/target-element-msbuild.md) elementów. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).  
  
## <a name="attributes"></a>Atrybuty  
 W poniższej tabeli opisano parametry `CreateItem` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AdditionalMetadata`|Opcjonalne `String` parametr tablicy.<br /><br /> Określa dodatkowe metadane do dołączenia do elementów danych wyjściowych.  Określ nazwę metadanych i wartość dla elementu przy użyciu następującej składni:<br /><br /> *MetadataName* `=` *MetadataValue*<br /><br /> Wiele par nazw i wartości metadanych powinny być oddzielone średnikami. Jeśli nazwa lub wartość zawiera średnika lub innych znaków specjalnych, musi być wyjściowym. Aby uzyskać więcej informacji, zobacz [porady: znaki specjalne ucieczki w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).|  
|`Exclude`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Określa elementy do wykluczenia z kolekcji elementów danych wyjściowych. Ten parametr może zawierać specyfikacji symbolu wieloznacznego. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md) i [porady: wykluczanie plików z kompilacji](../msbuild/how-to-exclude-files-from-the-build.md).|  
|`Include`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> `[]`parametru.<br /><br /> Określa elementy do uwzględnienia w kolekcji elementów danych wyjściowych. Ten parametr może zawierać specyfikacji symbolu wieloznacznego.|  
|`PreserveExistingMetadata`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `True`, zastosuj dodatkowe metadane tylko, jeśli jeszcze nie istnieje.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod tworzy nową kolekcję elementu o nazwie `MySourceItemsWithMetadata` z kolekcji elementów `MySourceItems`. `CreateItem` Zadań wypełnia nową kolekcję elementów z elementów w `MySourceItems` elementu. Następnie dodaje wpis dodatkowych metadanych o nazwie `MyMetadata` o wartości `Hello` do każdego elementu w nowej kolekcji.  
  
 Po wykonaniu zadania `MySourceItemsWithMetadata` kolekcji elementów zawiera elementy `file1.resx` i `file2.resx`, zarówno wpisy metadanych dla `MyMetadata`. `MySourceItems` Niezmieniona kolekcji elementów.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceItems Include="file1.resx;file2.resx" />  
    </ItemGroup>  
  
    <Target Name="NewItems">  
        <CreateItem  
            Include="@(MySourceItems)"  
            AdditionalMetadata="MyMetadata=Hello">  
           <Output  
               TaskParameter="Include"  
               ItemName="MySourceItemsWithMetadata"/>  
        </CreateItem>  
  
    </Target>  
  
</Project>  
```  
  
 W poniższej tabeli opisano wartość elementu danych wyjściowych po wykonaniu zadań. Metadane elementu jest wyświetlany w nawiasach po elemencie.  
  
|Kolekcji elementów|Spis treści|  
|---------------------|--------------|  
|`MySourceItemsWithMetadata`|`file1.resx` (`MyMetadata="Hello"`)<br /><br /> `file2.resx` (`MyMetadata="Hello"`)|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)