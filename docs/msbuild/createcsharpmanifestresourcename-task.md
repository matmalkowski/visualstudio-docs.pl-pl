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
ms.openlocfilehash: e54f9e8edd3295b87cbf6bf3c52a1874d1db89d9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31576732"
---
# <a name="createcsharpmanifestresourcename-task"></a>CreateCSharpManifestResourceName — Zadanie
Tworzy [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]— styl nazwy manifestu z nazwę pliku .resx danego lub innego zasobu.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry [createcsharpmanifestresourcename — zadanie](../msbuild/createcsharpmanifestresourcename-task.md).  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ManifestResourceNames`|<xref:Microsoft.Build.Framework.ITaskItem> `[]` tylko do odczytu parametru wyjściowego.<br /><br /> Wynikowa nazwy manifestu.|  
|`ResourceFiles`|Wymagane `String` parametru.<br /><br /> Nazwa pliku zasobu, z którym ma zostać utworzony [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] nazwę pliku manifestu.|  
|`RootNamespace`|Opcjonalne `String` parametru.<br /><br /> Główna przestrzeń nazw pliku zasobu, zazwyczaj pobierana z pliku projektu. Może być `null`.|  
|`PrependCultureAsDirectory`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, nazwa kultury jest dodawana jako nazwę katalogu, bezpośrednio przed nazwy zasobu manifestu. Wartość domyślna to `true`.|  
|`ResourceFilesWithManifestResourceNames`|Opcjonalnie tylko do odczytu `String` parametru wyjściowego.<br /><br /> Zwraca nazwę pliku zasobu, która zawiera teraz nazwę zasobu manifestu.|  
  
## <a name="remarks"></a>Uwagi  
 [Createvisualbasicmanifestresourcename — zadanie](../msbuild/createvisualbasicmanifestresourcename-task.md) Określa nazwę zasobu manifestu odpowiednie do przypisania do .resx danego pliku lub innego zasobu. Zadanie zawiera nazwę logiczną do pliku zasobów i dołącza go do parametru wyjściowego jak metadanych.  
  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)