---
title: MOVE — zadanie | Dokumentacja firmy Microsoft
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
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46fd157a1b4425f7a6f3c2f3ec6e6ba9d4ee1083
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681522"
---
# <a name="move-task"></a>Move — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [przenieść zadanie](https://docs.microsoft.com/visualstudio/msbuild/move-task).  
  
  
Przenosi pliki do nowej lokalizacji.  
  
## <a name="parameters"></a>Parametry  
 W następujących tabeli przedstawiono parametry `Move` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`DestinationFiles`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Określa listę plików, aby przenieść pliki źródłowe do. Ta lista powinna być zmapowana do listy, który jest określony w `SourceFiles` parametru. Oznacza to, że pierwszy plik określony w `SourceFiles` zostaną przeniesione do pierwszej lokalizacji określonej w `DestinationFiles`, i tak dalej.|  
|`DestinationFolder`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa katalog, do której chcesz umieścić pliki.|  
|`MovedFiles`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera elementy, które zostały prawidłowo przeniesione.|  
|`OverwriteReadOnlyFiles`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, zastępuje pliki, nawet wtedy, gdy są one oznaczone jako pliki tylko do odczytu.|  
|`SourceFiles`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki, aby przenieść.|  
  
## <a name="remarks"></a>Uwagi  
 Albo `DestinationFolder` parametru lub `DestinationFiles` parametr musi być określony, ale nie oba. W razie podania obu parametrów zadanie nie powiedzie się i zostanie zarejestrowany błąd.  
  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)



