---
title: Updatemanifest — zadanie | Dokumentacja firmy Microsoft
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
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03d93e8cb6d57a0f114a7f4fa1d45342437587f2
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153705"
---
# <a name="updatemanifest-task"></a>UpdateManifest — zadanie
Aktualizuje właściwości wybranego w manifeście i rezygnuje.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `UpdateManifest` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ApplicationManifest`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa w manifeście aplikacji.|  
|`ApplicationPath`|Wymagane `String` parametru.<br /><br /> Określa ścieżkę manifestu aplikacji.|  
|`InputManifest`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa manifestu do zaktualizowania.|  
|`OutputManifest`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa manifest, który zawiera zaktualizowane właściwości.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [zadań klasy bazowej](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)