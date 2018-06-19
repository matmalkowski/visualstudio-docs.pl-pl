---
title: Cppclean — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.cppclean
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a871effd2b7560cc34ae8e2a91c0b55f63bcfe44
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31568519"
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