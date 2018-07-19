---
title: Createcsharpmanifestresourcename — zadanie | Dokumentacja firmy Microsoft
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
- MSBuild, CreateCSharpManifestResourceName task
- CreateCSharpManifestResourceName task [MSBuild]
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7906cce0f8c9a2ac490f0877c539fbfc1b8e4b72
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37945472"
---
# <a name="createcsharpmanifestresourcename-task"></a>CreateCSharpManifestResourceName — zadanie
Tworzy [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]— styl nazwy manifestu z danym *resx* nazwa pliku lub innego zasobu.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry [createcsharpmanifestresourcename — zadanie](../msbuild/createcsharpmanifestresourcename-task.md).  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ManifestResourceNames`|<xref:Microsoft.Build.Framework.ITaskItem> `[]` Parametr tylko do odczytu danych wyjściowych.<br /><br /> Wynikowy nazwy manifestu.|  
|`ResourceFiles`|Wymagane `String` parametru.<br /><br /> Nazwa pliku zasobów, z której ma zostać utworzona [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] nazwy manifestu.|  
|`RootNamespace`|Opcjonalnie `String` parametru.<br /><br /> Przestrzeń nazw głównego pliku zasobów, zwykle pobierane z pliku projektu. Może być `null`.|  
|`PrependCultureAsDirectory`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, nazwa kultury jest dodawany jako nazwę katalogu, tuż przed nazwę zasobu manifestu. Wartość domyślna to `true`.|  
|`ResourceFilesWithManifestResourceNames`|Opcjonalnie, tylko do odczytu `String` parametr wyjściowy.<br /><br /> Zwraca nazwę pliku zasobu, który teraz zawiera nazwę zasobu manifestu.|  
  
## <a name="remarks"></a>Uwagi  
 [Createvisualbasicmanifestresourcename — zadanie](../msbuild/createvisualbasicmanifestresourcename-task.md) Określa nazwę odpowiedniego zasobu manifestu, można przypisać do danej *resx* lub inny plik zasobów. Zadanie zawiera nazwę logiczną do pliku zasobów i dołącza go do parametru wyjściowego jako metadane.  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)