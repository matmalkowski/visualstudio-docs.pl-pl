---
title: CreateVisualBasicManifestResourceName Task | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
caps.latest.revision: 8
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 133b1b6cf881d014c93391b316710975a84a2f21
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName — Zadanie
Tworzy [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]— styl nazwy manifestu z nazwę pliku .resx danego lub innego zasobu.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry [createvisualbasicmanifestresourcename — zadanie](../msbuild/createvisualbasicmanifestresourcename-task.md).  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ManifestResourceNames`|<xref:Microsoft.Build.Framework.ITaskItem> `[]` tylko do odczytu parametru wyjściowego.<br /><br /> Wynikowa nazwy manifestu.|  
|`ResourceFiles`|Wymagane `String` parametru.<br /><br /> Nazwa pliku zasobu, z którym ma zostać utworzony [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nazwę pliku manifestu.|  
|`RootNamespace`|Opcjonalne `String` parametru.<br /><br /> Główna przestrzeń nazw pliku zasobu, zazwyczaj pobierana z pliku projektu. Może być `null`.|  
|`PrependCultureAsDirectory`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, nazwa kultury jest dodawana jako nazwę katalogu, bezpośrednio przed nazwy zasobu manifestu. Wartość domyślna to `true`.|  
|`ResourceFilesWithManifestResourceNames`|Opcjonalnie tylko do odczytu `String` parametru wyjściowego.<br /><br /> Zwraca nazwę pliku zasobu, która zawiera teraz nazwę zasobu manifestu.|  
  
## <a name="remarks"></a>Uwagi  
 [Createvisualbasicmanifestresourcename — zadanie](../msbuild/createvisualbasicmanifestresourcename-task.md) Określa nazwę zasobu manifestu odpowiednie do przypisania do .resx danego pliku lub innego zasobu. Zadanie zawiera nazwę logiczną do pliku zasobów i dołącza go do parametru wyjściowego jak metadanych.  
  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)