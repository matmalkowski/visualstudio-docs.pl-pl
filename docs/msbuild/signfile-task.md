---
title: "Signfile — zadanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#SignFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, SignFile task
- SignFile task [MSBuild]
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
caps.latest.revision: "19"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8c1e5e25d6a8b3b953d28676415266ccf245d418
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="signfile-task"></a>SignFile — Zadanie
Rejestruje określony plik przy użyciu określonego certyfikatu.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `SignFile` zadań.  
  
 Należy pamiętać, że algorytm SHA-256 certyfikaty są dozwolone tylko na maszynach mających .NET 4.5 lub nowszy.  
  
> [!WARNING]
>  Począwszy od programu Visual Studio 2013 Update 3, to zadanie jest nowy podpisie, który służy do określenia docelowej wersji struktury pliku. Jesteś zaleca się stosowanie nowego podpisu wszędzie tam, gdzie to możliwe, ponieważ procesu programu MSBuild używa algorytmu SHA-256 skróty tylko wtedy, gdy platforma docelowa jest .NET 4.5 lub nowszej. W przypadku platformy docelowej .NET 4.0 lub poniżej wyznaczania wartości skrótu SHA-256, nie będzie używany.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`CertificateThumbprint`|Wymagane `String` parametru.<br /><br /> Określa certyfikat używany do podpisywania. Ten certyfikat musi być w magazynie osobistym bieżącego użytkownika.|  
|`SigningTarget`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa pliki, aby zalogować się przy użyciu certyfikatu.|  
|`TimestampUrl`|Opcjonalne `String` parametru.<br /><br /> Określa adres URL serwera sygnatur czasowych.|  
|`TargetFrameworkVersion`|Wersja programu .NET Framework, która jest używana dla elementu docelowego.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz wymienionych powyżej parametrów to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [klasa podstawowa zadania](../msbuild/task-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `SignFile` zadań do podpisywania plików określonych w `FilesToSign` Kolekcja elementów z certyfikatu określonego przez `Certificate` właściwości.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <FileToSign Include="File.exe" />  
    </ItemGroup>  
    <PropertyGroup>  
        <Certificate>Cert.cer</Certificate>  
    </PropertyGroup>  
    <Target Name="Sign">  
        <SignFile  
            CertificateThumbprint="$(CertificateThumbprint)"  
            SigningTarget="@(FileToSign)"   
            TargetFrameworkVersion="v4.5" />  
    </Target>  
</Project>  
```  
  
> [!NOTE]
>  Odcisk palca certyfikatu jest Skrót SHA-1 certyfikatu. Aby uzyskać więcej informacji, zobacz [uzyskać skrótu SHA-1 certyfikatu zaufanego głównego urzędu certyfikacji](http://msdn.microsoft.com/en-us/dd641990-9a88-4228-a245-017797131a87).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Exec` zadań do podpisywania plików określonych w `FilesToSign` Kolekcja elementów z certyfikatu określonego przez `Certificate` właściwości. Możesz użyć tego do podpisywania plików Instalatora Windows podczas procesu kompilacji.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <FileToSign Include="File.msi" />  
    </ItemGroup>  
    <PropertyGroup>  
        <Certificate>Cert.cer</Certificate>  
    </PropertyGroup>  
    <Target Name="Sign">  
        <Exec Command="signtool.exe sign /f CertFile /p Password "@(FileToSign)" "/>  
        <SignFile  
            CertificateThumbprint="$(CertificateThumbprint)"  
            SigningTarget="@(FileToSign)"   
            TargetFrameworkVersion="v4.0" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)