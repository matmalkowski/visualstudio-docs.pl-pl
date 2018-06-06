---
title: Visual Studio Tools for Office Runtime ― scenariusze instalacji
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2af3f4834fecfe4fcfba30f736892057893ed143
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767728"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Visual Studio Tools for Office Runtime ― scenariusze instalacji
  Visual Studio 2010 Tools dla pakietu Office runtime można zainstalować na trzy sposoby:  
  
-   Po zainstalowaniu programu Visual Studio.  
  
-   Po zainstalowaniu programu Microsoft Office.  
  
-   Po zainstalowaniu programu Visual Studio 2010 Tools dla pakietu Office runtime pakietu redystrybucyjnego.  
  
 Składniki środowiska uruchomieniowego, które są instalowane są zależne od konfiguracji komputera oraz Scenariusz instalacji.  
  
## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Składniki środowiska uruchomieniowego, które są zainstalowane w każdym ze scenariuszy instalacji  
 Visual Studio 2010 Tools dla pakietu Office runtime ma trzy składniki: moduł ładujący rozwiązań pakietu Office, rozszerzenia pakietu Office dla programu .NET Framework 3.5 i rozszerzenia pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym. Po zainstalowaniu środowiska uruchomieniowego, moduł ładujący rozwiązanie Office będzie zawsze instalowany. Instalacja rozszerzenia pakietu Office dla programu .NET Framework zależy od konfiguracji komputera oraz Scenariusz instalacji. Jeśli nie można zainstalować jednego z rozszerzeń pakietu Office, podczas pierwszej instalacji środowiska uruchomieniowego, środowisko uruchomieniowe automatycznie zainstaluje brakujące rozszerzenia pakietu Office później, gdy są spełnione pewne wymagania. Ta funkcja aparatu plików wykonywalnych jest nazywana *zainstalować na żądanie*.  
  
 W poniższej tabeli przedstawiono składniki środowiska uruchomieniowego są instalowane domyślnie w każdym ze scenariuszy instalacji czasu wykonywania. Więcej informacji na temat poszczególnych scenariuszy pojawi się później.  
  
|Scenariusz instalacji środowiska uruchomieniowego|Program ładujący rozwiązanie Office|Rozszerzenia pakietu Office dla programu .NET Framework 3.5|Rozszerzenia pakietu Office [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Rozszerzenia pakietu Office [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|  
|-----------------------------------|----------------------------|--------------------------------------------------|---------------------------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Z [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] i nowsze|Tak|Tak, jeśli program .NET Framework 3.5 jest już zainstalowana.|Tak|Tak|  
|Z [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Tak|Tak, jeśli program .NET Framework 3.5 jest już zainstalowana.|Nie|Nie|  
|Z pakietu Office 2010 Service Pack 1 (SP1) lub nowszym|Tak|Tak, jeśli program .NET Framework 3.5 jest już zainstalowana.|Tak, jeśli [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] jest już zainstalowana.|Nie|  
|Ze środowiskiem uruchomieniowym pakietu redystrybucyjnego|Tak|Tak, jeśli program .NET Framework 3.5 jest już zainstalowana.|Tak, jeśli [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] jest już zainstalowana.|Tak, jeśli [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] jest już zainstalowana.|  
  
### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Zainstaluj środowisko uruchomieniowe Visual Studio lub Microsoft Office Developer Tools dla programu Visual Studio  
 Po zainstalowaniu narzędzia Office developer tools w programie Visual Studio, rozszerzenia pakietu Office dla [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] i [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] są zawsze instalowane na komputerze dewelopera. Rozszerzenia pakietu Office dla programu .NET Framework 3.5, są instalowane tylko wtedy, gdy program .NET Framework 3.5 jest już obecny na komputerze dewelopera. Jeśli po zainstalowaniu programu .NET Framework 3.5 zainstalować [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], środowisko uruchomieniowe automatycznie instaluje rozszerzenia pakietu Office dla programu .NET Framework 3.5 podczas pierwszego tworzenia projektu pakietu Office, który jest przeznaczony dla programu .NET Framework 3.5.  
  
> [!WARNING]  
>  Nie można utworzyć projektu pakietu Office, przeznaczonego dla programu .NET Framework 3.5 przy użyciu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] lub nowszym.  
  
 Aby uzyskać więcej informacji o sposobie instalowania narzędzi Office developer tools, zobacz [porady: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).  
  
### <a name="install-the-runtime-with-office"></a>Zainstaluj środowisko uruchomieniowe z pakietem Office  
 Po zainstalowaniu pakietu Office rozszerzenia pakietu Office dla programu .NET Framework 3.5 są zainstalowane, jeśli program .NET Framework 3.5 jest już zainstalowana na komputerze. Po zainstalowaniu programu .NET Framework 3.5 po Office środowiska uruchomieniowego automatycznie instaluje rozszerzenia pakietu Office na określoną godzinę .NET Framework 3.5 pierwszy aplikacji pakietu Office próbuje załadować rozwiązanie, którego element docelowy .NET Framework 3.5.  
  
 Rozszerzenia pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszy nie są zainstalowane z pakietu Office, nawet jeśli [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub później znajduje się już po zainstalowaniu pakietu Office.  
  
 Rozszerzenia pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] są zainstalowane z pakietu Office. Użytkownicy końcowi mogą uzyskać rozszerzenia pakietu Office dla [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , instalując usługi Windows update.  
  
 Aby upewnić się, czy użytkownicy mają z rozszerzeniami niezbędnymi do korzystania z aplikacji, obejmują najnowszej wersji programu Visual Studio 2010 Tools dla pakietu redystrybucyjnego jako warunek wstępny dla rozwiązań pakietu Office runtime. Aby uzyskać więcej informacji na temat wymagań wstępnych, zobacz [Office rozwiązania z wymagań wstępnych dotyczących wdrażania](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>Zainstaluj środowisko uruchomieniowe przy użyciu pakietu redystrybucyjnego środowiska uruchomieniowego  
 Można zainstalować środowiska uruchomieniowego, uruchamiając Visual Studio 2010 Tools dla pakietu Office runtime pakietu redystrybucyjnego ręcznie lub przez dołączenie do dystrybucji jako warunek wstępny, wdrażając rozwiązania do pakietu Office.  
  
 Po zainstalowaniu środowiska uruchomieniowego za pomocą programu Visual Studio 2010 Tools for Office runtime do dystrybucji, rozszerzenia pakietu Office dla programu .NET Framework 3.5 oraz rozszerzenia pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym są zainstalowane, jeśli odpowiednie wersje programu .NET Framework jest już obecny na komputerze. W komputerze brakuje jednej z tych wersji programu .NET Framework, po zainstalowaniu środowiska uruchomieniowego, rozszerzenia pakietu Office Brak wersji programu .NET Framework nie są zainstalowane w tym czasie. Po zainstalowaniu Brak wersji programu .NET Framework później środowiska uruchomieniowego automatycznie instaluje odpowiedniego rozszerzenia pakietu Office przy następnym rozwiązania, które wymaga rozszerzeń zainstalowano (jeśli środowiska wykonawczego został zainstalowany z rozwiązaniem, które zostały wdrożone przy użyciu technologii ClickOnce) lub (jeśli środowiska wykonawczego został zainstalowany z rozwiązaniem, które zostały wdrożone za pomocą Instalatora systemu Windows).  
  
 Aby uzyskać więcej informacji o tym wymagania wstępne w rozwiązaniu ClickOnce, zobacz [porady: Instalowanie wymagań wstępnych na komputerach użytkowników końcowych do uruchamiania rozwiązań pakietu Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98). Aby uzyskać więcej informacji o sposobie instalowania środowiska uruchomieniowego z pakietu redystrybucyjnego ręcznie, zobacz [porady: zainstalować Visual Studio Tools for Office runtime pakietu redystrybucyjnego](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Visual Studio Tools for Office runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Zestawy w Visual Studio Tools for Office runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)  
  
  