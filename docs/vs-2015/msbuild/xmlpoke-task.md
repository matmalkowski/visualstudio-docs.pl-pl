---
title: Xmlpoke — zadanie | Dokumentacja firmy Microsoft
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
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad3950c3aecb1144a588b0d232216a8a316b3b26
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676695"
---
# <a name="xmlpoke-task"></a>XmlPoke — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [xmlpoke — zadanie](https://docs.microsoft.com/visualstudio/msbuild/xmlpoke-task).  
  
  
Ustawia wartości określonych przez zapytanie XPath do pliku XML.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `XmlPoke` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Namespaces`|Opcjonalnie `String` parametru.<br /><br /> Określa obszary nazw w przypadku prefiksów kwerendy XPath.|  
|`Query`|Opcjonalnie `String` parametru.<br /><br /> Określa zapytanie XPath.|  
|`Value`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa plik wyjściowy.|  
|`XmlInputPath`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa dane wejściowe XML jako ścieżkę do pliku.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)



