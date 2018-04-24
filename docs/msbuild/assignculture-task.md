---
title: Assignculture — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AssignCulture task
- AssignCulture task [MSBuild]
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 26adf9bd97e10e25402db100ebb0140917ac6143
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="assignculture-task"></a>AssignCulture — Zadanie
To zadanie akceptuje listę elementów, które mogą zawierać prawidłowy ciąg identyfikatora kultury .NET jako część nazwy pliku i tworzy elementy, które mają metadanych o nazwie `Culture` zawierającego odpowiednie kultury identyfikator. Na przykład nazwa pliku Form1.fr fr.resx ma osadzonych kultury identyfikator "fr-fr", dlatego to zadanie spowoduje utworzenie elementu, który ma taką samą nazwę z metadanymi `Culture` równa `fr-fr`. Zadanie również tworzy listę nazw plików z kulturą usunięte z nazwy pliku.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `AssignCulture` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AssignedFiles`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Zawiera listę elementów odebranych w `Files` parametru z `Culture` wpis metadanych dodane do każdego elementu.<br /><br /> Jeśli element przychodzącego z `Files` zawiera już parametr `Culture` wpis metadanych, oryginalny wpis metadanych jest używany.<br /><br /> Przypisuje tylko zadania `Culture` wpis metadanych, jeśli nazwa pliku zawiera identyfikator prawidłową kulturą. Identyfikator kultury musi należeć do zakresu od ostatnich dwóch kropki w nazwie pliku.|  
|`AssignedFilesWithCulture`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Zawiera podzbiór elementów z `AssignedFiles` parametr, który ma `Culture` wpis metadanych.|  
|`AssignedFilesWithNoCulture`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Zawiera podzbiór elementów z `AssignedFiles` parametr, który nie ma `Culture` wpis metadanych.|  
|`CultureNeutralAssignedFiles`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Zawiera tę samą listę elementów, które jest tworzone w `AssignedFiles` parametru, chyba że kultura usunięte z nazwy pliku.<br /><br /> Zadanie tylko usuwa kultura od nazwy pliku, jeśli jest identyfikator prawidłową kulturą.|  
|`Files`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa listę plików z nazwy kultury osadzonych można przypisać do kultury.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje `AssignCulture` zadań z `ResourceFiles` Kolekcja elementów.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ResourceFiles Include="MyResource1.fr.resx"/>  
        <ResourceFiles Include="MyResource2.XX.resx"/>  
    </ItemGroup>  
  
    <Target Name="Culture">  
        <AssignCulture  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
            <Output TaskParameter="AssignedFilesWithCulture"  
                ItemName="OutAssignedFilesWithCulture"/>  
            <Output TaskParameter="AssignedFilesWithNoCulture"  
                ItemName="OutAssignedFilesWithNoCulture"/>  
            <Output TaskParameter="CultureNeutralAssignedFiles"  
                ItemName="OutCultureNeutralAssignedFiles"/>  
        </AssignCulture>  
    </Target>  
</Project>  
```  
  
 W poniższej tabeli opisano wartości elementów wyjściowych po wykonaniu zadań. Metadane elementu jest wyświetlany w nawiasach po elemencie.  
  
|Kolekcji elementów|Spis treści|  
|---------------------|--------------|  
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx` (Brak dodatkowych metadanych)|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx` (Brak dodatkowych metadanych)|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (`nie dodatkowe metadane)|  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)