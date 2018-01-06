---
title: Komunikat zadania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
caps.latest.revision: "23"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 80464b6f2dc0f61061dbb3fdceb8bae8ec4449c3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="message-task"></a>Komunikat — Zadanie
Rejestruje komunikat podczas kompilacji.  
  
## <a name="parameters"></a>Parametry  
 W tabeli następujących opisano parametry `Message` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Importance`|Opcjonalne `String` parametru.<br /><br /> Określa znaczenie komunikatu. Ten parametr może mieć wartość `high`, `normal` lub `low`. Wartość domyślna to `normal`.|  
|`Text`|Opcjonalne `String` parametru.<br /><br /> Tekst błędu logowania.|  
  
## <a name="remarks"></a>Uwagi  
 `Message` Zadanie pozwala [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekty do wiadomości problem do rejestratorów w różnych czynności w procesie kompilacji.  
  
 Jeśli `Condition` daje w wyniku parametru `true`, wartość `Text` parametru będą rejestrowane i kompilacji będzie kontynuować jego wykonywanie. Jeśli `Condition` parametr nie istnieje, tekst komunikatu jest rejestrowane. Aby uzyskać więcej informacji, zobacz [uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Domyślnie komunikat jest wysyłany do rejestratora konsoli programu MSBuild. Można to zmienić, ustawiając <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A> parametru. Rejestrator interpretuje `Importance` parametru.  
  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu rejestruje komunikaty wszystkich rejestratorów zarejestrowanych.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="DisplayMessages">  
        <Message Text="Project File Name = $(MSBuildProjectFile)" />  
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)