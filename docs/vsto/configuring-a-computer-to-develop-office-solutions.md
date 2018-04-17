---
title: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 59c00639ce839962c06cacf3c036a5cd8f74b508
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="configuring-a-computer-to-develop-office-solutions"></a>Konfigurowanie komputera do opracowywania rozwiązań pakietu Office

Tworzenie dodatków narzędzi VSTO i dostosowań pakietu Microsoft Office, należy zainstalować obsługiwaną wersję programu Visual Studio, .NET Framework i program Microsoft Office.

|Oprogramowanie|Obsługiwane wersje|
|--------------|------------------------|
|Visual Studio 2017| Dowolna wersja z **programowanie Office i SharePoint** obciążenia.|
|.NET Framework|-Programu .NET Framework 4 lub nowszej.|
|Microsoft Office|<ul><li>Dowolnej wersji pakietu Office, w tym Office Professional Plus dla usługi Office 365.</li><li>Jedną z następujących aplikacji autonomicznych:<br /><br /> <ul><li>Excel</li><li>InfoPath (Office 2013 i Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Projekt</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic for Applications (VBA) musi być zainstalowany jako część pakietu Office. **Ważne:** wersje kliknij polecenie do uruchomienia aplikacji pakietu Office 2010 nie są obsługiwane.|

Aby instalacja szczegółowe instrukcje, zobacz [porady: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Jeśli szablony projektów nie pojawiają się lub nie działają w programie Visual Studio

Zainstaluj obsługiwaną wersję programu Visual Studio, .NET Framework i program Microsoft Office, ale szablony projektów pakietu Office nie występować w programie Visual Studio **nowy projekt** okno dialogowe, lub wystąpi błąd podczas próby użycia jednej, Sprawdź następujące informacje:

- Upewnij się, że narzędzia Microsoft Office developer tools zainstalowany na tym komputerze.

     Narzędzia Office developer tools są opcjonalnym składnikiem programu Visual Studio, ale są zwykle zainstalowane automatycznie wraz z programu Visual Studio. Jeśli instalacji programu Visual Studio można dostosować, określając funkcje do zainstalowania, upewnij się, że wybierasz **Microsoft Office Developer Tools** podczas instalacji, aby zainstalować narzędzia.

     Aby upewnić się, że te narzędzia są zainstalowane, uruchom Instalatora programu Visual Studio, a następnie wybierz **Modyfikuj** przycisku. Wybierz **Microsoft Office Developer Tools** pole wyboru, a następnie wybierz pozycję **aktualizacji** przycisku.

- Upewnij się, że nie używasz wersji pakietu Office, który został dostarczony przez kliknięcie do uruchomienia. Zobacz [porady: Sprawdź, czy program Outlook aplikacji kliknij polecenie do uruchomienia na komputerze](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx).

- Upewnij się, że używasz tylko jedna wersja programu Microsoft Office.

Jeśli nadal występują problemy, zobacz [dodatkowa obsługa błędów w rozwiązaniach pakietu Office](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Zobacz też

[Wprowadzenie &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
[Instrukcje: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)  
[Instrukcje: Instalowanie pakietu redystrybucyjnego Visual Studio Tools dla pakietu Office Runtime](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)  
[Instrukcje: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
[Funkcje dostępne w aplikacjach pakietu Office i typ projektu](../vsto/features-available-by-office-application-and-project-type.md)
