---
title: "Migracja rozwiązań pakietu Office do programu .NET Framework 4 lub nowszego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
ms.assetid: 31f6c48b-c086-4362-8629-f644d6083a44
caps.latest.revision: "55"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c47c99f8d9a907d86461098f1f569fdbcac8841c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="migrating-office-solutions-to-the-net-framework-4-or-later"></a>Migracja rozwiązań pakietu Office do programu .NET Framework 4 lub nowszego
  Jeśli platforma docelowa programu Office project jest zmieniana na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później ze starszej wersji programu .NET Framework, dodatkowe kroki mogą być wymagane do kontynuować działanie rozwiązania na programowanie i użytkownik końcowy komputerów. Aby uzyskać więcej informacji, zobacz [zmiany wymagane do uruchomienia projektów pakietu Office migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).  
  
 Ponadto projekt nie może być kompilacji. Niektóre funkcje projektów pakietu Office mają różne modele programowania dla różnych wersji programu .NET Framework. Zmiany platformy docelowej projektu pakietu Office na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później w ze starszej wersji programu .NET Framework, do projektu należy wprowadzić następujące zmiany kodu:  
  
-   [Aktualizowanie programu Excel i Word projektów, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualizowanie dostosowań Wstążki w projektach pakietu Office, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualizowanie regionów formularzy w projektach programu Outlook, których można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 Platforma docelowa programu Office project zmienia się po uaktualnieniu tego projektu z wcześniejszej wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [uaktualnianie i migracja rozwiązań pakietu Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
 Aby uzyskać więcej informacji na temat przyczyn niektóre funkcje w projektach pakietu Office mieć inny model programowania, jeśli zostanie rozpoczęta [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, zobacz [zmiany do projektu z pakietu Office projektów, który współpracować z programu .NET Framework 4 lub .NET Framework 4.5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) i [Visual Studio Tools for Office Runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Porady: wersja docelowa platformy .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Rozwiązywanie problemów z błędami w rozwiązaniach pakietu Office](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Dodatkowa obsługa błędów w rozwiązaniach pakietu Office](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  