---
title: "MOVE — zadanie | Dokumentacja firmy Microsoft"
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
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 521a5239e47ffcab4d93c2cd2a46c30f881b0abd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="move-task"></a>Move — Zadanie
Przenosi pliki do nowej lokalizacji.  
  
## <a name="parameters"></a>Parametry  
 W tabeli następujących opisano parametry `Move` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`DestinationFiles`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Określa listę plików, aby przenieść pliki źródłowe do. Ta lista powinien być mapowanie jeden do jednego do listy, która została określona w `SourceFiles` parametru. Oznacza to, że pierwszy plik określony w `SourceFiles` zostaną przeniesione do pierwszej lokalizacji określonej w `DestinationFiles`, itd.|  
|`DestinationFolder`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa katalog, do którego chcesz przenieść pliki.|  
|`MovedFiles`|Opcjonalne <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego.<br /><br /> Zawiera elementy, które zostały prawidłowo przeniesione.|  
|`OverwriteReadOnlyFiles`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, zastępuje pliki, nawet jeśli są one oznaczone jako pliki tylko do odczytu.|  
|`SourceFiles`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki, aby przenieść.|  
  
## <a name="remarks"></a>Uwagi  
 Albo `DestinationFolder` parametru lub `DestinationFiles` parametr musi być określony, ale nie oba. W razie podania obu parametrów zadanie nie powiedzie się i zostanie zarejestrowany błąd.  

 `Move` Zadanie, tworzy foldery, co jest wymagane dla docelowej lokalizacji plików.

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
