---
title: "Warning — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: "18"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: a7fca3c4981a038bba4d84c520704f1a43e01b1e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="warning-task"></a>Warning — Zadanie
Dzienniki ostrzeżenie podczas kompilacji w oparciu obliczane instrukcji warunkowej.  
  
## <a name="parameters"></a>Parametry  
 W tabeli następujących opisano parametry `Warning` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Code`|Opcjonalne `String` parametru.<br /><br /> Kod ostrzeżenia do skojarzenia z ostrzeżeniem.|  
|`File`|Opcjonalne `String` parametru.<br /><br /> Określa odpowiedniego pliku, jeśli istnieje. Jeśli plik nie zostanie podany, jest używany plik zawierający ostrzeżenie zadań.|  
|`HelpKeyword`|Opcjonalne `String` parametru.<br /><br /> Słowo kluczowe pomocy do skojarzenia z ostrzeżeniem.|  
|`Text`|Opcjonalne `String` parametru.<br /><br /> Tekst ostrzeżenia który [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] rejestruje Jeśli `Condition` daje w wyniku parametru `true`.|  
  
## <a name="remarks"></a>Uwagi  
 `Warning` Zadanie pozwala [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektów, aby sprawdzić obecność wymaganej konfiguracji lub właściwości przed wykonaniem następnego kroku kompilacji.  
  
 Jeśli `Condition` parametr `Warning` daje w wyniku zadania `true`, wartość `Text` parametru jest rejestrowana i kontynuuje wykonywanie kompilacji. Jeśli `Condition` parametru nie nie exisit, tekst ostrzeżenie jest rejestrowane. Aby uzyskać więcej informacji, zobacz [uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu sprawdza, czy właściwości, które są ustawiane w wierszu polecenia. Jeśli nie ma nie ustawiono właściwości, projekt wywołuje zdarzenie ostrzeżenia i rejestruje wartość `Text` parametr `Warning` zadań.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)