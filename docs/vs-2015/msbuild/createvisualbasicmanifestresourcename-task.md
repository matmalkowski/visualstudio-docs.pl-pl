---
title: Createvisualbasicmanifestresourcename — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a1588ce170ad9e833f7378a837e4e75853c19ba
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679857"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [createvisualbasicmanifestresourcename — zadanie](https://docs.microsoft.com/visualstudio/msbuild/createvisualbasicmanifestresourcename-task).  
  
  
Tworzy [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]— styl nazwy manifestu z nazwę pliku ResX danego lub innego zasobu.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry [createvisualbasicmanifestresourcename — zadanie](../msbuild/createvisualbasicmanifestresourcename-task.md).  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ManifestResourceNames`|<xref:Microsoft.Build.Framework.ITaskItem> `[]` Parametr tylko do odczytu danych wyjściowych.<br /><br /> Wynikowy nazwy manifestu.|  
|`ResourceFiles`|Wymagane `String` parametru.<br /><br /> Nazwa pliku zasobów, z której ma zostać utworzona [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nazwy manifestu.|  
|`RootNamespace`|Opcjonalnie `String` parametru.<br /><br /> Przestrzeń nazw głównego pliku zasobów, zwykle pobierane z pliku projektu. Może być `null`.|  
|`PrependCultureAsDirectory`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, nazwa kultury jest dodawany jako nazwę katalogu, tuż przed nazwę zasobu manifestu. Wartość domyślna to `true`.|  
|`ResourceFilesWithManifestResourceNames`|Opcjonalnie, tylko do odczytu `String` parametr wyjściowy.<br /><br /> Zwraca nazwę pliku zasobu, który teraz zawiera nazwę zasobu manifestu.|  
  
## <a name="remarks"></a>Uwagi  
 [Createvisualbasicmanifestresourcename — zadanie](../msbuild/createvisualbasicmanifestresourcename-task.md) Określa nazwę odpowiedniego zasobu manifestu, można przypisać do danej resx lub inny plik zasobów. Zadanie zawiera nazwę logiczną do pliku zasobów i dołącza go do parametru wyjściowego jako metadane.  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)



