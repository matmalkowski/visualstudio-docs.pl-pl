---
title: "Cppclean — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.task.cppclean
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), CPPClean task
- CPPClean task (MSBuild (Visual C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 437b4a7e6b1a8e92b4409188655dccdfcb1baf50
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="cppclean-task"></a>CPPClean — Zadanie
Usuwa pliki tymczasowe, które MSBuild tworzy podczas tworzenia projektu Visual C++. Proces usuwania plików kompilacji jest znany jako *czyszczenia*.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **cppclean —** zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**DeletedFiles**|Opcjonalne `ITaskItem[]` parametru wyjściowego.<br /><br /> Określa tablicę MSBuild wyjściowego pliku elementy, które mogą być używane i emitowane przez zadania.|  
|**DoDelete**|Opcjonalne **logiczna** parametru.<br /><br /> Jeśli `true`, czyszczenie tymczasowych plików kompilacji.|  
|**FilePatternsToDeleteOnClean**|Wymagane `String` parametru.<br /><br /> Określa listę rozszerzeń plików, aby wyczyścić rozdzielone średnikami.|  
|**FilesExcludedFromClean**|Opcjonalne `String` parametru.<br /><br /> Określa Rozdzielana średnikami lista plików nie można wyczyścić.|  
|**FoldersToClean**|Wymagane `String` parametru.<br /><br /> Określa Rozdzielana średnikami lista katalogów, aby wyczyścić. Można określić pełny lub ścieżką względną i ścieżki może zawierać symbol wieloznaczny (**\***).|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)