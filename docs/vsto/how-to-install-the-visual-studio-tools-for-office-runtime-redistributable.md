---
title: 'Porady: Instalowanie Visual Studio Tools for Office runtime pakietu redystrybucyjnego'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 15e3c1b25d4834808fb17e596fcc7babe7dd969f
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255853"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Porady: Instalowanie Visual Studio Tools for Office runtime pakietu redystrybucyjnego
  Visual Studio 2010 Tools dla pakietu Office runtime musi być zainstalowany na każdym komputerze z konsolą rozwiązania, które są tworzone za pomocą narzędzia Microsoft Office developer tools w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Środowisko wykonawcze jest instalowana automatycznie podczas instalowania [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]i Microsoft Office. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools for Office Runtime ― scenariusze instalacji](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 Konieczne może być postępuj zgodnie z instrukcjami instalacji ręcznej poniżej w następujących sytuacjach:  
  
-   Musisz zainstalować [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] na serwerze. Na przykład chcesz użyć <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy na poziomie dokumentu rozwiązań na serwerze zarządzania.  
  
-   Należy zainstalować na komputerze, który ma już wszystkie inne wymagania wstępne dla rozwiązań pakietu Office zainstalowane środowisko uruchomieniowe.  
  
    > [!NOTE]  
    >  Musi być administratorem na komputerze dewelopera do zainstalowania programu .NET Framework i [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Aby zainstalować Visual Studio Tools for Office runtime  
  
1.  Zainstaluj [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym.  
  
    -   Aby pobrać [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], zobacz [Microsoft .NET Framework 4 (Instalator internetowy)](http://go.microsoft.com/fwlink/?LinkId=178957).  
  
    -   Aby pobrać [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], zobacz [profil klienta programu Microsoft .NET Framework 4 (Instalator internetowy)](http://go.microsoft.com/fwlink/?LinkId=178958).  
  
    -   Aby pobrać [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], zobacz [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).  
  
2.  Uruchom *vstor_redist.exe* do zainstalowania [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
     Możesz pobrać te pliki Instalatora z [Visual Studio 2010 Tools dla pakietu Office runtime](http://go.microsoft.com/fwlink/?LinkId=140384). Wymagania wstępne dotyczące [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] odpowiada wymagania wstępne dotyczące programu .NET Framework.  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Zawiera pakiety językowe. Jeśli instalacja systemu Windows jest ustawiony na języku innym niż angielski, można wyświetlić wiadomości w czasie wykonywania w języku używanym dla systemu Windows. Podobnie jeśli użytkownicy końcowi instalować [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , a następnie uruchom rozwiązań w przypadku instalacji systemu Windows, które są ustawione na język niż angielski, środowiska uruchomieniowego komunikaty będą wyświetlane w języku systemu Windows. W niektórych przypadkach może być konieczne dodatkowe pakiety językowe. Na przykład może być konieczne dodatkowe pakiety językowe, jeśli kopii systemu Windows korzysta z więcej niż jedno ustawienie języka lub przełączanie na inny język, po zainstalowaniu już [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Można znaleźć pakietów językowych w [Microsoft Visual Studio 2010 Tools dla pakietu Microsoft Office system (wersja 4.0 środowiska wykonawczego) języka](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## <a name="see-also"></a>Zobacz także  
 [Rozpoczynanie pracy &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [Porady: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Porady: podstawowe zestawy międzyoperacyjne pakietu Office instalacji](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)  
  
  