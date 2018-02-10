---
title: "Xsltransformation — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4eb192777b85adbfc270c7cbdb4469548333c5ec
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="xsltransformation-task"></a>XslTransformation — Zadanie
Transformacje jako XML wejściowych przy użyciu XSLT lub skompilowany XSLT i dane wyjściowe do urządzenia wyjściowego lub pliku.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `XslTransformation` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`OutputPaths`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki wyjściowe dla transformacji XML.|  
|`Parameters`|Opcjonalne `String` parametru.<br /><br /> Określa parametry do dokumentu XSLT danych wejściowych.|  
|`XmlContent`|Opcjonalne `String` parametru.<br /><br /> Określa dane wejściowe XML jako ciąg.|  
|`XmlInputPaths`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa pliki wejściowe XML.|  
|`XslCompiledDllPath`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa skompilowanych XSLT.|  
|`XslContent`|Opcjonalne `String` parametru.<br /><br /> Określa dane wejściowe XSLT jako ciąg.|  
|`XslInputPath`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa plik wejściowy XSLT.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)