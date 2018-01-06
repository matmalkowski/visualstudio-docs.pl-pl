---
title: "Xsltransformation — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
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
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ac5070e874551aea3880428b106ccb13c7c76c4c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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