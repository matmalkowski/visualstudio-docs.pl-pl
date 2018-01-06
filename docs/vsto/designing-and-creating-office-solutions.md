---
title: "Projektowanie i tworzenie rozwiązań pakietu Office | Dokumentacja firmy Microsoft"
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
- Office solutions [Office development in Visual Studio], creating
- Office development in Visual Studio, creating solutions
- solutions [Office development in Visual Studio], creating
- Office project types in Visual Studio
ms.assetid: 53c32c61-3d3a-4427-a5a7-f9c2c8f1de02
caps.latest.revision: "103"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8b7322faa797ea9ce51af0cd716ffb6536f062ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="designing-and-creating-office-solutions"></a>Projektowanie i tworzenie rozwiązań Office
  Program Visual Studio udostępnia szablony projektów, które umożliwia tworzenie wielu różnych typów rozwiązań pakietu Office. Ta sekcja dokumentacji opisano szablony projektów i zawiera wskazówki dotyczące tworzenia projektów pakietu Office. Aby dowiedzieć się, jak wdrożyć dostosowania interfejsu kodu i użytkownika, po utworzeniu projektu, zobacz [opracowywania rozwiązań pakietu Office](../vsto/developing-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Pytań dotyczących projektowania rozwiązań, które rozszerzają możliwości pakietu Office przez [wielu platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatków pakietu Office mieć niewielkie rozmiary w porównaniu do dodatków VSTO i rozwiązań i można ich tworzyć przy użyciu prawie każdego technologii, takich jak HTML5, CSS3, JavaScript i XML programowanie dla sieci web.  
  
## <a name="creating-office-projects"></a>Tworzenie projektów pakietu Office  
 Przed rozpoczęciem należy określić wymagania i odnajdywanie typ rozwiązania, które oferuje najlepsze dopasowanie. Jeśli na przykład rozwiązania pakietu Office musi co czas wykonywania jest używana w aplikacji, dodatku VSTO najlepsze mieści się z wymaganiami. Jeśli kod jest ściśle zintegrowany z pojedynczego dokumentu, należy utworzyć dostosowania poziomie dokumentu. Tych typów projektów są dostępne jako szablony projektu Visual Studio. Aby uzyskać więcej informacji na temat szablonów projektu pakietu Office, które są dołączone do programu Visual Studio, zobacz [Omówienie szablonów programu Office Project](../vsto/office-project-templates-overview.md). Aby uzyskać więcej informacji na temat tworzenia projektów pakietu Office, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Projekty Office ma funkcje i elementy projektu, które różnią się od innych typów projektów programu Visual Studio. Na przykład podczas tworzenia projektu poziomie dokumentu, dokument lub skoroszyt w projekcie można go otworzyć i edytować w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [projekty pakietu Office w Visual Studio środowiska](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="choosing-a-net-framework-version"></a>Wybieranie wersji programu .NET Framework  
 Po wybraniu typu projektu, który najlepiej spełnia wymagania, możesz wersji programu .NET Framework do użycia w procesie tworzenia aplikacji. Można wskazać następujące wersje programu .NET Framework w projektach pakietu Office:  
  
-   [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]  
  
-   [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]  
  
-   [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
  
 .NET Framework w wersji wybranego projektu jest wymagany na komputerach użytkowników końcowych do rozwiązania uruchomić. Na przykład jeśli elementy docelowe projektu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] jest wymagany na komputerach użytkowników końcowych. W tym przykładzie rozwiązania nie będzie działać, jeśli tylko program .NET Framework 3.5 jest zainstalowana na komputerach użytkowników końcowych.  
  
 W przypadku migrowania projektów dodatku VSTO przeznaczonego dla programu .NET Framework 3.5, Visual Studio zmienia platformy docelowej projektu do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, w zależności od wersji pakietu Office, który został zainstalowany.  
  
 Jednak po Visual Studio zmian platformę docelową, może być konieczne do modyfikacji niektórych kodu w projekcie, jeśli korzysta z niektórych funkcji. Aby uzyskać więcej informacji o sposobie zmienić platformę docelową, zobacz [porady: wersja docelowa platformy .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Aby uzyskać więcej informacji na temat zmian, konieczne może być w projekcie, zobacz [Migrowanie rozwiązań pakietu Office do programu .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
 Jeśli używasz ClickOnce do wdrażania rozwiązania Visual Studio zmienia docelowej platformy .NET Framework dla projektu, upewnij się, czy też wybrać odpowiednią wersję programu .NET Framework w **wymagania wstępne** okno dialogowe. To pole wyboru nie ulega zmianie automatycznie zmienić platformę docelową projektu. Aby uzyskać więcej informacji, zobacz [porady: Instalowanie wymagań wstępnych na komputerach użytkowników końcowych do uruchamiania rozwiązań pakietu Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
> [!NOTE]  
>  Nie może wskazać .NET Framework 3.5 lub starszej w projektach pakietu Office, które utworzono za pomocą [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]. Projekty Office, utworzonych przy użyciu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] wymagane funkcje, które zostały najpierw wprowadzone w systemie[!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]  
  
### <a name="understanding-when-the-office-pias-are-required-on-end-user-computers"></a>Opis, gdy na komputerach użytkowników końcowych wymagane są PIAs pakietu Office  
 Domyślnie podstawowe zestawy międzyoperacyjne pakietu Office (PIAs) nie są zainstalowane na komputerach użytkowników końcowych, jeśli **Osadź typy międzyoperacyjne** właściwość każdego odwołania PIA pakietu Office, w projekcie jest ustawiona na **True**, która jest to wartość domyślna. W tym scenariuszu informacji o typie dla typów PIA, które są używane w tym rozwiązaniu są osadzone w zestawie rozwiązania podczas kompilowania projektu. W czasie wykonywania osadzonego typu informacje są używane zamiast PIAs do wywoływania aplikacji pakietu Office oparte na modelu COM object model. Aby uzyskać więcej informacji dotyczących sposobu typów z PIAs są osadzone w ramach rozwiązania, zobacz [równoważność typów i osadzone typy międzyoperacyjne](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types).  
  
 Jeśli **Osadź typy międzyoperacyjne** właściwość każdego odwołania PIA pakietu Office, w projekcie jest ustawiona na **False**, Office PIAs musi być zainstalowane i zarejestrowane w globalnej pamięci podręcznej zestawów na każdym komputerze użytkownika końcowego, który Uruchamia rozwiązania. W większości przypadków PIAs są instalowane domyślnie w pakiecie Office, ale mogą również obejmować PIA do dystrybucji jako warunek wstępny dla rozwiązania. Aby uzyskać więcej informacji, zobacz [Office rozwiązania z wymagań wstępnych dotyczących wdrażania](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### <a name="understanding-the-client-profile"></a>Opis profilu klienta  
 Profil klienta programu .NET Framework jest podzbiorem pełnej .NET Framework. Jeśli należy użyć tylko funkcje klienta w programie .NET Framework i chcesz zapewnić najszybszym środowisko wdrażania rozwiązania pakietu Office, można kierować .NET Framework Client Profile. Aby uzyskać więcej informacji, zobacz [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).  
  
 Podczas tworzenia projektu pakietu Office, którego element docelowy [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] domyślny. Jeśli chcesz na w pełni [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], należy ustawić tę opcję po utworzeniu projektu. Aby uzyskać więcej informacji, zobacz [porady: wersja docelowa platformy .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## <a name="creating-solutions-for-the-64-bit-edition-of-microsoft-office"></a>Tworzenie rozwiązań dla 64-bitowej wersji pakietu Microsoft Office  
 Microsoft Office jest dostępna w wersji 64-bitowe i 32-bitowych. Aby utworzyć rozwiązań pakietu Office, które można uruchomić w każdej wersji, ustawienie platformy docelowej projektu musi mieć ustawioną **Any CPU**. Jest to wartość domyślna dla projektów pakietu Office. Aby uzyskać więcej informacji, zobacz [kompilowanie rozwiązań pakietu Office](../vsto/building-office-solutions.md).  
  
 Istnieją różne wersje 64-bitowe i 32-bitowego z [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] używanych przez wersje 64-bitowe i 32-bitowego pakietu Microsoft Office. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools for Office Runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="assemblies-in-office-solutions"></a>Zestawy w rozwiązaniach pakietu Office  
 Podczas tworzenia projektu pakietu Office przy użyciu narzędzia deweloperskie pakietu Office w Visual Studio, kod napisany ostatecznie jest kompilowany do zestawu. Zestaw zwykle jest wdrożony na serwerze udostępnionego lub katalogu na komputerze klienckim.  
  
 Zestawy w rozwiązaniach pakietu Office są ładowane według aplikacji pakietu Office. Po zestaw jest ładowany, kod w zestawie mogą odpowiadać na zdarzeń występujących w aplikacji, na przykład po kliknięciu elementu menu. Kod w zestawie także wywołać object model automatyzacji i rozszerzenie aplikacji i może używać dowolnej klasy w [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]. Aby uzyskać więcej informacji, zobacz [architektura poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md) i [dodatki architektura VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
 Do identyfikacji zestawu rozwiązań pakietu Office użyć manifesty wdrożenia i manifestów aplikacji. Manifesty zawierają informacje o nazwę zestawu, wersję i lokalizacji, dzięki czemu aplikacji można znaleźć, Połącz i uruchomić poprawny zestaw. Aby uzyskać więcej informacji, zobacz [manifesty wdrożenia w rozwiązaniach pakietu Office i aplikacji](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 Projektów na poziomie dokumentu obejmują dokumentu oprócz zestawu. Dokument działa jako fronton aplikacji i jest, gdzie odbywa się wszystkie interakcji z użytkownikiem. Każdy dokument można mieć tylko jeden zestaw głównego projektu skojarzonych z nim; jednak wielu dokumentów może wskazywać tego samego zestawu.  
  
 Zestawy w projektach na poziomie dokumentu nie są osadzone w dokumencie. Zamiast tego są przechowywane w innym miejscu i są identyfikowane za pomocą dokumentu w manifeście aplikacji.  
  
## <a name="security-considerations-for-assemblies"></a>Zagadnienia dotyczące zabezpieczeń zestawów  
 Dla rozwiązań pakietu Office uruchomić na komputerze musi być zaufany, aby uruchomić zestawy używane przez to rozwiązanie. Aby uzyskać więcej informacji o zabezpieczeniach, zobacz [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md).  
  
 Domyślnie są zaufane do uruchomienia na komputerze dewelopera podczas kompilowania projektu zestawu rozwiązania i przywoływanych zestawach, które znajdują się w folderze wyjściowym projektu. Aby uzyskać więcej informacji, zobacz [kompilowanie rozwiązań pakietu Office](../vsto/building-office-solutions.md).  
  
 Ze względów bezpieczeństwa jest najlepiej jest tworzyć projekty na komputerze lokalnym, a nie rozwijających się w lokalizacji udostępnionej. Aby uzyskać więcej informacji, zobacz [zespołowe programowania rozwiązań pakietu Office](../vsto/collaborative-development-of-office-solutions.md).  
  
## <a name="referenced-assemblies"></a>Zestawy, do których istnieją odwołania  
 Zestaw może odwoływać się do innych zestawów, które są wymienione w odwołaniach projektu. Jednak jeden zestaw projektów na poziomie dokumentu nie może odwoływać się inny zestaw projektów na poziomie dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd szablonów projektu pakietu Office](../vsto/office-project-templates-overview.md)   
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Projekty pakietu Office w środowisku Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)   
 [Właściwości w projektach pakietu Office](../vsto/properties-in-office-projects.md)   
 [Uruchamianie rozwiązań w różnych wersjach pakietu Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)   
 [Porady: docelowa aplikacji pakietu Office za pośrednictwem podstawowe zestawy międzyoperacyjne](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Aplikacji i manifestów wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [Porady: Ustawianie informacji o konfiguracji dla rozwiązań pakietu Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)   
 [Przy użyciu funkcji pakietu Office w Visual Studio](../vsto/using-office-functionality-inside-of-visual-studio.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Typowe zadania w programowaniu pakietu Office](../vsto/common-tasks-in-office-programming.md)   
 [Tworzenie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)   
 [Architektura rozwiązań pakietu Office w Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  