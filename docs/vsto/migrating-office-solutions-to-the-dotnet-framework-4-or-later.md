---
title: Migracja rozwiązań pakietu Office do programu .NET Framework 4 lub nowszego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7ac244bebb1a625c7858a62399ee79126e309cf2
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34571802"
---
# <a name="migrating-office-solutions-to-the-net-framework-4-or-later"></a>Migracja rozwiązań pakietu Office do programu .NET Framework 4 lub nowszej
  Jeśli platforma docelowa programu Office project jest zmieniana na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później ze starszej wersji programu .NET Framework, dodatkowe kroki mogą być wymagane do kontynuować działanie rozwiązania na programowanie i użytkownik końcowy komputerów. Aby uzyskać więcej informacji, zobacz [wymagane zmiany w celu uruchamiania projektów pakietu Office, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).  
  
 Ponadto projekt nie może być kompilacji. Niektóre funkcje projektów pakietu Office mają różne modele programowania dla różnych wersji programu .NET Framework. Zmiany platformy docelowej projektu pakietu Office na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później w ze starszej wersji programu .NET Framework, do projektu należy wprowadzić następujące zmiany kodu:  
  
-   [Aktualizacja programu Excel i Word projektów, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualizowanie dostosowań Wstążki w projektach pakietu Office, które można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Aktualizowanie regionów formularzy w projektach programu Outlook, których można dokonać migracji do programu .NET Framework 4 lub .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 Platforma docelowa programu Office project zmienia się po uaktualnieniu tego projektu z wcześniejszej wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [uaktualnienia i migracja rozwiązań pakietu Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
 Aby uzyskać więcej informacji na temat przyczyn niektóre funkcje w projektach pakietu Office mieć inny model programowania, jeśli zostanie rozpoczęta [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później, zobacz [zmiany w projektach pakietu Office przeznaczonych dla platformy .NET Framework 4 lub .NET Framework 4.5projektu](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) i [Visual Studio Tools for Office runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Porady: wersja docelowa platformy .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Rozwiązywanie problemów z błędami w rozwiązaniach pakietu Office](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Dodatkowa obsługa błędów w rozwiązaniach pakietu Office](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  