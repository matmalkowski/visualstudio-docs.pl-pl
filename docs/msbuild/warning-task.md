---
title: Warning — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d980027ca6901e4ed657b67e9e55554c8f319b45
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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