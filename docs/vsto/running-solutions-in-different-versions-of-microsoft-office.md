---
title: "Uruchamianie rozwiązań w różnych wersjach pakietu Microsoft Office | Dokumentacja firmy Microsoft"
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
helpviewer_keywords:
- solutions [Office development in Visual Studio], multiple Office versions
- Office applications [Office development in Visual Studio], multiple Office versions
- Office development in Visual Studio, multiple Office versions
- Office solutions [Office development in Visual Studio]
- multiple Office versions
ms.assetid: 414e7741-c07d-4900-9d10-68b821413b3f
caps.latest.revision: "61"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a52ab5c2f2f5a367681929966175ca4c4cb33b56
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="running-solutions-in-different-versions-of-microsoft-office"></a>Uruchamianie rozwiązań w różnych wersjach pakietu Microsoft Office
    
## <a name="running-office-solutions-created-by-using-visual-studio-2010-and-above"></a>Uruchamianie rozwiązań pakietu Office utworzone za pomocą programu Visual Studio 2010 i nowszych  
  
|Wersja pakietu Office objęci szablonu projektu|Docelowy .NET Framework projektu<sup>1</sup>|Wersje pakietu Office, który można uruchomić rozwiązanie|Wymagane środowisko uruchomieniowe na komputerze użytkownika końcowego|  
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|  
|Pakiet Office 2016 i[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]lub nowszy|Pakiet Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Microsoft Office system 2007<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]lub nowszy|Pakiet Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Microsoft Office system 2007<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Program .NET Framework 3,5|Pakiet Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Visual Studio 2010 Tools for Office Runtime|  
|System Microsoft Office 2007|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]lub nowszy,<br /><br /> lub<br /><br /> Program .NET Framework 3,5|Pakiet Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> System Microsoft Office 2007|Visual Studio 2010 Tools for Office Runtime|  
  
 1. Wersja programu .NET Framework na komputerach użytkowników końcowych do rozwiązania uruchomić wymagane elementy docelowe projektu. Na przykład jeśli elementem docelowym projektu jest program .NET Framework 3.5, .NET Framework 3.5 jest wymagana na komputerach użytkowników końcowych. W tym przykładzie rozwiązania nie uruchomi jeśli tylko [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] jest zainstalowany na komputerach użytkowników końcowych.  
  
 2. W tym scenariuszu rozwiązania będą uruchamiane bez błędów w Microsoft Office system 2007 tylko wtedy, gdy nie używa funkcji, które są nowością w programie [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
## <a name="running-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>Uruchomiona Office rozwiązania utworzone przez przy użyciu wersji programu Visual Studio przed Visual Studio 2010  
 Aplikacje Microsoft Office mogą działać rozwiązania utworzone przy użyciu wersji programu Visual Studio przed Visual Studio 2010. W niektórych przypadkach te rozwiązania wymagają różnych wersji [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Różne wersje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] mogą być zainstalowane obok siebie na jednym komputerze.  
  
 W poniższej tabeli przedstawiono, które wersje pakietu Microsoft Office, można uruchomić rozwiązania utworzone przy użyciu poprzedniej wersji programu Visual Studio oraz wersjach programu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] i .NET Framework są wymagane dla poszczególnych rozwiązań.  
  
|Wersja programu Visual Studio pozwala tworzyć rozwiązania|Wersja pakietu Office objęci szablonu projektu|Wersje pakietu Office, który można uruchomić rozwiązanie|Wymagane środowisko uruchomieniowe na komputerze użytkownika końcowego|Wymagana wersja programu .NET Framework na komputerze użytkownika końcowego|  
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|  
|Visual Studio 2008 Professional<br /><br /> lub<br /><br /> Visual Studio Team System 2008|System Microsoft Office 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] <sup>1</sup><br /><br /> System Microsoft Office 2007|Visual Studio 2010 Tools for Office Runtime<sup>1</sup><br /><br /> lub<br /><br /> Visual Studio Tools dla pakietu Microsoft Office system (wersja 3.0 Runtime)|Program .NET Framework 3,5|  
|Jedną z następujących wersji programu Visual Studio 2005 z VSTO 2005 SE<sup>2</sup> zainstalowane:<br /><br /> — Program visual Studio 2005 Tools dla pakietu Office<br />— Program visual Studio Team System 2005<br />— Program visual Studio 2005 Professional|System Microsoft Office 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (32-bitowych<sup>3</sup>)<br /><br /> System Microsoft Office 2007|Visual Studio 2005 Tools dla pakietu Office drugie wersji środowiska uruchomieniowego|.NET framework 2.0, .NET Framework 3.0 lub .NET Framework 3.5|  
|Dowolny z następujących wersji programu Visual Studio:<br /><br /> — Program visual Studio 2008 Professional<br />— Program visual Studio Team System 2008<br />— Program visual Studio 2005 Tools dla pakietu Office (z lub bez VSTO 2005 SE<sup>2</sup> zainstalowana)<br />— Program visual Studio Team System 2005 (lub bez VSTO 2005 SE<sup>2</sup> zainstalowana)<br />— Program visual Studio 2005 Professional z VSTO 2005 SE<sup>2</sup> zainstalowany|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (32-bitowych<sup>3</sup>)<br /><br /> System Microsoft Office 2007<br /><br /> Microsoft Office 2003|Visual Studio 2005 Tools dla pakietu Office drugie wersji środowiska uruchomieniowego|.NET framework 2.0, .NET Framework 3.0 lub .NET Framework 3.5|  
  
 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] zastosowań Visual Studio 2010 Tools for Office Runtime. W związku z tym te aplikacje zawsze używać programu Visual Studio 2010 Tools dla pakietu Office Runtime niż Visual Studio Tools dla pakietu Microsoft Office system (wersja 3.0 Runtime) w tym scenariuszu. Aplikacje Microsoft Office System 2007 mogą używać programu Visual Studio 2010 Tools dla pakietu Office Runtime lub Visual Studio Tools dla pakietu Microsoft Office system (wersja 3.0 Runtime).  
  
 2. VSTO 2005 SE jest bezpłatny dodatek Visual Studio, która zapewnia dodatku VSTO szablony projektu Microsoft Office 2003 i Microsoft Office system 2007. Można zainstalować go z programu Visual Studio 2005 Professional, Visual Studio 2005 Tools dla pakietu Office lub wersji programu Visual Studio Team System 2005. Aby uzyskać więcej informacji, zobacz [Visual Studio 2005 Tools dla pakietu Office wydanie drugie](http://go.microsoft.com/fwlink/?LinkId=148446).  
  
 3. Rozwiązania pakietu Office, które wymagają programu Visual Studio 2005 Tools for Office Runtime drugi w wersji nie są zgodne z 64-bitowe wersje [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] i [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]. Aby uruchomić te rozwiązania w 64-bitowej wersji systemu [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] lub [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)], należy uaktualnić projekt, aby [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] lub projektu programu Visual Studio 2008 przeznaczonego dla systemu Microsoft Office 2007.  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Visual Studio Tools for Office Runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Visual Studio Tools for Office Runtime ― scenariusze instalacji](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)  
  
  