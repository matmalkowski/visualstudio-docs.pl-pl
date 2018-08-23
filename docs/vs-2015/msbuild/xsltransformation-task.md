---
title: XslTransformation Task | Microsoft Docs
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
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66ba37f75267e069ede64a25ac4c56bca8a4e8c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678046"
---
# <a name="xsltransformation-task"></a>XslTransformation — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [xsltransformation — zadanie](https://docs.microsoft.com/visualstudio/msbuild/xsltransformation-task).  
  
  
Przekształcenia na XML danych wejściowych za pomocą XSLT lub skompilowane XSLT i dane wyjściowe do wyjścia urządzenia lub pliku.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `XslTransformation` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`OutputPaths`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki wyjściowe transformacji XML.|  
|`Parameters`|Opcjonalnie `String` parametru.<br /><br /> Określa parametry do dokumentu XSLT w danych wejściowych.|  
|`XmlContent`|Opcjonalnie `String` parametru.<br /><br /> Określa dane wejściowe XML jako ciąg.|  
|`XmlInputPaths`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa pliki danych wejściowych XML.|  
|`XslCompiledDllPath`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa skompilowanych XSLT.|  
|`XslContent`|Opcjonalnie `String` parametru.<br /><br /> Określa dane wejściowe XSLT jako ciąg.|  
|`XslInputPath`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa wejściowy plik XSLT.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)



