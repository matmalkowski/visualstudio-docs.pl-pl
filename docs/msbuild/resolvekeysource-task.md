---
title: "Resolvekeysource — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: "10"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: cdbbdd476d37d19be63402b970beef84e9802fb5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="resolvekeysource-task"></a>ResolveKeySource — Zadanie
Określa źródło klucza silnej nazwy.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `ResolveKeySource` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AutoClosePasswordPromptShow`|Opcjonalne `Int32` parametru.<br /><br /> Pobiera lub ustawia czas, w sekundach, aby wyświetlić liczbę w dół wiadomości.|  
|`AutoClosePasswordPromptTimeout`|Opcjonalne `Int32` parametru.<br /><br /> Pobiera lub ustawia czas, w ciągu sekund oczekiwania przed zamknięciem okna dialogowego monitu o hasło.|  
|`CertificateFile`|Opcjonalne `String` parametru.<br /><br /> Pobiera lub ustawia ścieżkę pliku certyfikatu.|  
|`CertificateThumbprint`|Opcjonalne `String` parametru.<br /><br /> Pobiera lub ustawia odcisk palca certyfikatu.|  
|`KeyFile`|Opcjonalne `String` parametru.<br /><br /> Pobiera lub ustawia ścieżkę pliku klucza.|  
|`ResolvedKeyContainer`|Opcjonalne `String` parametru wyjściowego.<br /><br /> Pobiera lub ustawia rozpoznać kontener klucza.|  
|`ResolvedKeyFile`|Opcjonalne `String` parametru wyjściowego.<br /><br /> Pobiera lub ustawia rozpoznać pliku klucza.|  
|`ResolvedThumbprint`|Opcjonalne `String` parametru wyjściowego.<br /><br /> Pobiera lub ustawia rozpoznać odcisk palca.|  
|`ShowImportDialogDespitePreviousFailures`|Opcjonalne `Boolean` parametru.<br /><br /> Jeśli `true`, Pokaż okno dialogowe Importuj pomimo poprzednie błędy.|  
|`SuppressAutoClosePasswordPrompt`|Opcjonalne `Boolean` parametru.<br /><br /> Pobiera lub ustawia wartość logiczna określająca, czy okno dialogowe monitu o hasło powinno nie automatycznego zamykania.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)