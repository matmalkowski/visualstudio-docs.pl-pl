---
title: "Konfigurowanie komputera do opracowywania rozwiązań pakietu Office | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Office development in Visual Studio, installing tools
ms.assetid: 0b481186-fd31-43bf-aa4a-591f94309555
caps.latest.revision: "97"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2d3e0b354375d6116a1bcc0cc2b0d69ecc2f16b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="configuring-a-computer-to-develop-office-solutions"></a>Konfigurowanie komputera do opracowywania rozwiązań pakietu Office
  Tworzenie dodatków narzędzi VSTO i dostosowań pakietu Microsoft Office, należy zainstalować obsługiwaną wersję programu Visual Studio, .NET Framework i program Microsoft Office.  
  
|Oprogramowanie|Obsługiwane wersje|  
|--------------|------------------------|  
|Visual Studio|-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]<br />-   [!INCLUDE[vsPreShort](../vsto/includes/vspreshort-md.md)]<br />-   [!INCLUDE[vsUltShort](../vsto/includes/vsultshort-md.md)]**Ważne:** musi zaznacz pole wyboru Microsoft Office Developer Tools podczas instalacji.|  
|.NET Framework|-Programu .NET Framework 4 lub nowszej.|  
|Microsoft Office|<ul><li>Dowolnej wersji pakietu Office, w tym Office Professional Plus dla usługi Office 365.</li><li>Jedną z następujących aplikacji autonomicznych:<br /><br /> <ul><li>Excel</li><li>InfoPath (Office 2013 i Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Project</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic for Applications (VBA) musi być zainstalowany jako część pakietu Office. **Ważne:** wersje kliknij polecenie do uruchomienia aplikacji pakietu Office 2010 nie są obsługiwane.|  
  
 Aby instalacja szczegółowe instrukcje, zobacz [porady: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).  
  
## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Jeśli szablony projektów nie pojawiają się lub nie działają w programie Visual Studio  
 Zainstaluj obsługiwaną wersję programu Visual Studio, .NET Framework i program Microsoft Office, ale szablony projektów pakietu Office nie występować w programie Visual Studio **nowy projekt** okno dialogowe, lub wystąpi błąd podczas próby użycia jednej, Sprawdź następujące informacje:  
  
-   Upewnij się, że narzędzia Microsoft Office developer tools zainstalowany na tym komputerze.  
  
     Narzędzia Office developer tools są opcjonalnym składnikiem programu Visual Studio, ale są zwykle zainstalowane automatycznie wraz z programu Visual Studio. Jeśli instalacji programu Visual Studio można dostosować, określając funkcje do zainstalowania, upewnij się, że wybierasz **Microsoft Office Developer Tools** podczas instalacji, aby zainstalować narzędzia.  
  
     W celu zapewnienia, że te narzędzia są zainstalowane, uruchom Instalatora programu Visual Studio, a następnie wybierz **Modyfikuj** przycisku. Wybierz **Microsoft Office Developer Tools** pole wyboru, a następnie wybierz pozycję **aktualizacji** przycisku.  
  
-   Upewnij się, że nie używasz wersji pakietu Office, który został dostarczony przez kliknięcie do uruchomienia. Zobacz [porady: Sprawdź, czy program Outlook aplikacji kliknij polecenie do uruchomienia na komputerze](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx).  
  
-   Upewnij się, że używasz tylko jedna wersja programu Microsoft Office.  
  
 Jeśli nadal występują problemy, zobacz [dodatkowa obsługa błędów w rozwiązaniach pakietu Office](../vsto/additional-support-for-errors-in-office-solutions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie &#40; programowanie Office w Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Porady: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Porady: Instalowanie narzędzi Visual Studio Tools for Office Runtime pakietu redystrybucyjnego](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [Porady: zainstalować podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Funkcje dostępne w aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md)  
  
  