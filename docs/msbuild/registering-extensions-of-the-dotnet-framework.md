---
title: "Rejestrowanie rozszerzeń środowiska .NET Framework | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 495a6bb1d72e521b3f44ea989974446def555c15
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="registering-extensions-of-the-net-framework"></a>Rejestrowanie rozszerzeń środowiska .NET Framework
Można utworzyć zestawu, który rozszerza określonej wersji programu .NET Framework. Aby włączyć zestaw pojawią się w programie Visual Studio **Dodaj odwołania** okno dialogowe, należy dodać folder zawierający go do rejestru systemowego.  
  
 Załóżmy na przykład, że firma Trey Research opracowała rozszerza programu .NET Framework 4, którą chce zestawy bibliotek, które mają być widoczne w bibliotece **Dodaj odwołania** okno dialogowe, gdy projekt jest przeznaczony dla programu .NET Framework 4. Również założono, że zestawy są zestawów 32-bitowych uruchomiony na komputerze 32-bitowy lub 64-bitowych zestawów na komputerze 64-bitowym z systemem i że ma być zainstalowany w folderze C:\TreyResearch\Extensions4\.  
  
 Rejestrowanie przy użyciu tego klucza ten folder: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\. Nadaj klucza to wartość domyślna: C:\TreyResearch\Extensions4.  
  
> [!NOTE]
>  Numer kompilacji programu .NET Framework w wersji może się różnić.  
  
 Aby zarejestrować zestawem 32-bitowych na 64-bitowym komputerze, za pomocą Wow6432 węzła, na przykład: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\.  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Integration](../msbuild/visual-studio-integration-msbuild.md)