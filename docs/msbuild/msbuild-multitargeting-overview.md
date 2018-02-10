---
title: "Przegląd MSBuild przeznaczanie dla wielu platform | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1b7581754aaf9690fce8b2f6cf5d0da5bb4a7e45
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="msbuild-multitargeting-overview"></a>Przegląd wielowersyjności kodu w programie MSBuild
Przy użyciu programu MSBuild, będzie można kompilować aplikacji do uruchomienia na jednym z kilku wersji programu .NET Framework i na jednym z kilku platform system. Na przykład można skompilować aplikację do uruchamiania na .NET Framework 2.0 na platformie 32-bitowe i skompilować tej samej aplikacji do uruchamiania na na 64-bitowej platformy .NET Framework 4.5.  
  
> [!IMPORTANT]
>  Niezależnie od nazwy "przeznaczanie dla wielu platform" Projekt może kierować framework tylko jeden i tylko jedną platformę w czasie.  
  
 Oto niektóre funkcje programu MSBuild docelowych:  
  
-   Możesz utworzyć aplikację, która jest przeznaczony dla starszej wersji programu .NET Framework, na przykład w wersji 2.0, 3.5 lub 4.  
  
-   Możesz zastosować framework innej niż programu .NET Framework, na przykład platformę Silverlight.  
  
-   Celem może być *profilu framework*, który jest wstępnie zdefiniowanych podzbiór platformy docelowej.  
  
-   Jeśli zostanie zwolniony z dodatkiem Service pack dla bieżącej wersji programu .NET Framework, można stosowanie ich.  
  
-   Celem MSBuild gwarantuje, że aplikacja używa tylko funkcje, który jest dostępny w docelowej framework i platformę.  
  
## <a name="target-framework-and-platform"></a>Platforma  
 A *platformy docelowej* jest to wersja platformy .NET Framework, korzysta z wbudowanej projektu do uruchamiania na i *platformy docelowej* czy projekt jest budowany na Platforma systemu.  Na przykład możesz chcieć aplikacji .NET Framework 2.0, do uruchamiania na platformie 32-bitowego, która jest zgodna z rodziny procesorów 802 x 86 (x86) docelowej. Kombinacja platformy docelowej i platforma docelowa jest nazywany *kontekst docelowy*. Aby uzyskać więcej informacji, zobacz [platformy docelowej i platformy docelowej](../msbuild/msbuild-target-framework-and-target-platform.md).  
  
## <a name="toolset-toolsversion"></a>Zestaw narzędzi (ToolsVersion)  
 Zestaw narzędzi zbiera razem narzędzia, zadań i elementów docelowych, które są używane do tworzenia aplikacji. Zestaw narzędzi zawiera kompilatory, takie jak csc.exe i vbc.exe, typowe plik elementów docelowych (microsoft.common.targets) i typowych zadań plików (microsoft.common.tasks). 4.5 zestaw narzędzi może służyć do docelowej wersji .NET Framework 2.0, 3.0, 3.5, 4 i 4.5. Jednak 2.0 zestawu narzędzi można używać tylko docelową programu .NET Framework w wersji 2.0. Aby uzyskać więcej informacji, zobacz [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  
  
## <a name="reference-assemblies"></a>Zestawy referencyjne  
 Zestawy odwołań, które są określone w zestawie narzędzi ułatwić projektowanie i kompilowanie aplikacji. Te zestawy odwołań nie tylko włączyć kompilacji określonego elementu docelowego, ale również ograniczyć składników i funkcji w środowisku IDE programu Visual Studio do tych, które są zgodne z elementem docelowym. Aby uzyskać więcej informacji, zobacz [rozwiązywanie zestawów w czasie projektowania](../msbuild/resolving-assemblies-at-design-time.md)  
  
## <a name="configuring-targets-and-tasks"></a>Konfigurowanie obiektów docelowych i zadań  
 Można skonfigurować program MSBuild obiektów docelowych i zadań w celu uruchomienia poza procesem przy użyciu programu MSBuild, dzięki czemu można wskazać kontekstach, które są nieco inne niż są uruchomione na.  Na przykład można kierować aplikacją 32-bitowy, .NET Framework 2.0 jest uruchomiona na komputerze deweloperskim na 64-bitowej platformy z programu .NET Framework 4.5. Aby uzyskać więcej informacji, zobacz [Konfigurowanie obiektów docelowych i zadań](../msbuild/configuring-targets-and-tasks.md).  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Jeśli spróbujesz się odwołanie do zestawu, który nie jest częścią kontekst docelowy, mogą wystąpić błędy. Aby uzyskać więcej informacji o te błędy i co należy zrobić ich temat, zobacz [Rozwiązywanie problemów z błędami docelowy Framework .NET](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).