---
title: "Visual Studio Tools for Office Runtime ― Przegląd | Dokumentacja firmy Microsoft"
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
- Office runtime [Office development in Visual Studio], about Office runtime
- VSTOLoader.dll
- runtime loader [Office development in Visual Studio]
- Office runtime [Office development in Visual Studio], assemblies
- Office runtime [Office development in Visual Studio]
- runtime [Office development in Visual Studio], assemblies
- vstoee.dll
- Visual Studio Tools for Office runtime
- Office solutions [Office development in Visual Studio], runtime
- solutions [Office development in Visual Studio], runtime
- versions [Office development in Visual Studio], runtime
- assemblies [Office development in Visual Studio], runtime
- runtime [Office development in Visual Studio], about VSTO runtime
- solution loader [Office development in Visual Studio]
- runtime [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ed9f3657fcb49a7b39ee41d2ce9b73dddda7fd93
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="visual-studio-tools-for-office-runtime-overview"></a>Visual Studio Tools dla pakietu Office Runtime ― Przegląd
  Do uruchamiania rozwiązań, które są tworzone za pomocą narzędzia Microsoft Office developer tools w programie Visual Studio, Visual Studio 2010 Tools for Office Runtime musi być zainstalowany na komputerach użytkowników końcowych. Aby uzyskać więcej informacji, zobacz [porady: Instalowanie narzędzi Visual Studio Tools dla pakietu Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md). Oprogramowanie to zawiera dwa główne składniki:  
  
-   Rozszerzenia pakietu Office dla środowiska .NET Framework. To zarządzane zestawy tworzące warstwę komunikacji między rozwiązaniem a aplikacją pakietu Microsoft Office. Aby uzyskać więcej informacji, zobacz [opis rozszerzenia pakietu Office dla programu .NET Framework](#officeextensions).  
  
-   Moduł ładujący rozwiązanie dla pakietu Office. To zestaw niezarządzanych bibliotek DLL, przy użyciu których aplikacje pakietu Office ładują środowisko uruchomieniowe i rozwiązanie. Aby uzyskać więcej informacji, zobacz [opis ładujący rozwiązanie Office](#UnmanagedLoader).  
  
 Środowisko uruchomieniowe można zainstalować na kilka różnych sposobów. Składniki środowiska dodawane podczas jego instalacji zależą od konfiguracji komputera. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools for Office Runtime ― scenariusze instalacji](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
##  <a name="officeextensions"></a>Opis rozszerzenia pakietu Office dla programu .NET Framework  
 Visual Studio 2010 Tools for Office Runtime obejmują rozszerzenia pakietu Office dla programu .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] i nowszych. Rozwiązania przeznaczone dla poszczególnych wersji środowiska .NET Framework używają rozszerzeń odpowiednich dla danej wersji.  
  
 Rozszerzenia te składają się z zestawów, przy użyciu których rozwiązania automatyzują aplikacje pakietu Office i poszerzają ich funkcjonalność. Podczas tworzenia projektu pakietu Office program Visual Studio automatycznie dodaje odwołania do zestawów używanych dla typu projektu oraz docelowego środowiska .NET Framework projektu. Aby uzyskać więcej informacji na temat zestawów w rozszerzenia pakietu Office, zobacz [zestawy w Visual Studio Tools for Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).  
  
### <a name="design-differences-in-the-office-extensions"></a>Różnice konstrukcyjne między rozszerzeniami pakietu Office  
 Większość typów używanych w rozszerzeniach pakietu Office dla środowiska .NET Framework 3.5 to klasy. Są to tej samej klasy, które zostały uwzględnione w poprzednich wersjach [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Natomiast większość typów używanych w rozszerzenia pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowsze są interfejsy. Na przykład, jeśli zostanie rozpoczęta [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, <xref:Microsoft.Office.Tools.Excel.Worksheet> i <xref:Microsoft.Office.Tools.Word.Document> typy są interfejsy zamiast klasy.  
  
 W większości przypadków kodu zapisu w rozwiązaniach pakietu Office jest taka sama czy rozwiązania jest przeznaczony dla programu .NET Framework 3.5 lub [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Jednak niektóre funkcje wymagają kodu dopasowanego do cech wersji środowiska .NET Framework. Aby uzyskać więcej informacji, zobacz [Migrowanie rozwiązań pakietu Office do programu .NET Framework 4 lub nowszego](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
### <a name="interfaces-in-the-office-extensions-for-the-net-framework-4-or-later"></a>Interfejsy rozszerzenia pakietu Office dla programu .NET Framework 4 lub nowszego  
 Większość interfejsów w rozszerzenia pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszy nie są przeznaczone do zaimplementowania przez kod użytkownika. Tylko interfejsy, które można wdrożyć bezpośrednio mają nazwy, które zaczynają się od litery **I**, takich jak <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension>.  
  
 Wszystkie interfejsy, które nie rozpoczynają się od litery **I** zaimplementowane wewnętrznie w Visual Studio 2010 Tools dla pakietu Office Runtime oraz te interfejsy mogą ulec zmianie w przyszłych wersjach. Aby utworzyć obiekty, które implementują te interfejsy, użyj metody udostępniane przez obiekt Globals.Factory w projekcie. Na przykład, aby pobrać obiekt, który implementuje <xref:Microsoft.Office.Tools.Excel.SmartTag> interfejsu, należy użyć metody Globals.Factory.CreateSmartTag. Aby uzyskać więcej informacji o Globals.Factory, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="enabling-type-equivalence-and-embedded-types-in-projects-that-target-the-net-framework-4-or-later"></a>Włączenie równoważność typów i osadzone typy w projektach przeznaczonych dla programu .NET Framework 4 lub nowszy  
 Ponieważ model obiektów rozszerzenia pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym są oparte na interfejsach, umożliwia funkcji pełnienia roli równoważnika typu, zarówno Visual C# i Visual Basic w programie Visual Studio osadzanie informacji o typie z [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] w ramach rozwiązania . Ta funkcja umożliwia rozwiązań pakietu Office i [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] do wersji niezależnie od siebie nawzajem. Na przykład, jeśli korzysta z rozwiązania <xref:Microsoft.Office.Tools.Word.Document> interfejsu jako typu osadzonego i następnej wersji środowiska uruchomieniowego dodaje członków do <xref:Microsoft.Office.Tools.Word.Document> interfejsu rozwiązania będą nadal działać z następnej wersji środowiska uruchomieniowego. Jeśli nie są używane rozwiązania <xref:Microsoft.Office.Tools.Word.Document> interfejsu jako osadzonym typem, a następnie rozwiązania nie będzie dłużej działać z następnej wersji środowiska uruchomieniowego.  
  
 Domyślnie funkcja pełnienia roli równoważnika typu nie jest włączona podczas tworzenia projektu pakietu Office, którego element docelowy [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym. Jeśli chcesz włączyć tę funkcję, ustaw **Osadź typy międzyoperacyjne** właściwość następujące odwołania do zestawów w swoim projekcie **True**:  
  
-   Microsoft.Office.Tools.dll  
  
-   Microsoft.Office.Tools.Common.dll  
  
-   Microsoft.Office.Tools.Excel.dll  
  
-   Microsoft.Office.Tools.Outlook.dll  
  
-   Microsoft.Office.Tools.Word.dll  
  
 Wprowadzenie tej zmiany spowoduje, że informacje o typie dla wszystkich typów środowisk uruchomieniowych używanych w projekcie zostaną podczas kompilowania projektu osadzane w zestawie rozwiązania. W czasie wykonywania rozwiązanie będzie używać tych osadzonych informacji o typach, a nie informacji z zestawów, do których prowadzą odwołania.  
  
##  <a name="UnmanagedLoader"></a>Opis modułu ładującego rozwiązań pakietu Office  
 Visual Studio Tools for Office runtime obejmuje kilka niezarządzanych bibliotek DLL, korzystających z aplikacji pakietu Office można załadować środowiska uruchomieniowego i rozwiązań pakietu Office. Nigdy nie powinna zajść konieczność bezpośredniej pracy z tymi bibliotekami, jednak wiedza o ich przeznaczeniu może pomóc lepiej zrozumieć architekturę rozwiązań opartych na pakiecie Office.  
  
 Aby uzyskać informacje o tych składników używanych podczas procesu obciążenia, zobacz [architektura poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md) i [architektura VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="vstoeedll"></a>VSTOEE.dll  
 Gdy użytkownik otwiera dostosowania poziomie dokumentu lub uruchamia dodatku VSTO, aplikacji pakietu Office wymaga w VSTOEE.dll do wykonania zadania wymagane do załadowania [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 VSTOEE.dll, zapewnia poprawną wersję [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] jest ładowany do rozwiązania oraz zainstalowanych wersji pakietu Office. Mimo że wiele wersji [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] można zainstalować na tym samym komputerze, tylko jedno wystąpienie VSTOEE.dll jest zainstalowany w czasie. Jest to plik VSTOEE.dll dołączony do najnowszej wersji środowiska uruchomieniowego zainstalowanego na komputerze. Aby uzyskać więcej informacji o różnych wersjach programu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] który może służyć do innych rozwiązań, zobacz [uruchamiania rozwiązań w różnych wersjach Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).  
  
### <a name="vstoloaderdll"></a>VSTOLoader.dll  
 Po VSTOEE.dll ładuje odpowiednią wersję [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], VSTOLoader.dll wykonuje większość pracy wymagane do załadowania zestawu rozwiązania. Oto najważniejsze operacje:  
  
-   Tworzy domenę aplikacji dla każdego zestawu rozwiązania.  
  
-   Wykonuje zbiór testów kontrolnych zabezpieczeń w celu sprawdzenia, czy zestaw rozwiązania ma pozwolenie na działanie.  
  
-   Ładuje wersje rozszerzeń pakietu Office dla środowiska .NET Framework wymaganego przez rozwiązanie.  
  
 VSTOLoader.dll powoduje także kilka kwestii, które są specyficzne dla dodatków VSTO:  
  
-   Implementuje <xref:Extensibility.IDTExtensibility2> interfejsu. <xref:Extensibility.IDTExtensibility2>jest interfejsem COM, które należy wdrożyć wszystkie dodatki VSTO aplikacji pakietu Microsoft Office. Ten interfejs definiuje metody, które wywołuje aplikację do komunikowania się z dodatku VSTO.  
  
-   Implementuje imanagedaddin — interfejs. Ten interfejs jest używany przez aplikacje pakietu Office, aby ułatwić obciążenia dodatków VSTO. Aby uzyskać więcej informacji, zobacz [imanagedaddin — interfejs](../vsto/imanagedaddin-interface.md).  
  
## <a name="understanding-the-32-bit-and-64-bit-versions-of-the-runtime"></a>Opis 32-bitowych i 64-bitowych wersji środowiska uruchomieniowego  
 Program Visual Studio 2010 Tools for Office Runtime ma osobne wersje 64- i 32-bitową. Te wersje środowiska uruchomieniowego są używane do uruchamiania rozwiązań w 64-bitowe i 32-bitowej wersji pakietu Office. Poniższej tabeli wersji środowiska uruchomieniowego jest wymagany dla każdej kombinacji systemu Windows oraz pakietu Office.  
  
|Wydanie systemu Windows|Wydanie pakietu Microsoft Office|Wymagana wersja środowiska Visual Studio Tools for Office Runtime|  
|------------------------|---------------------------------|--------------------------------------------------------------------|  
|32-bitowa|32-bitowa|32-bitowa|  
|64-bitowy|32-bitowa|64-bitowy|  
|64-bitowy|64-bitowy|64-bitowy|  
  
 Po zainstalowaniu pakietu Office, wymaganą wersję [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] jest instalowane wraz z pakietu Office. Na przykład po zainstalowaniu 64-bitowa wersja pakietu Office na 64-bitowej wersji systemu Windows, wersja 64-bitowych [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] jest również instalowany. Aby uzyskać więcej informacji o instalowaniu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] z pakietu Office, zobacz [Visual Studio Tools for Office Runtime ― scenariusze instalacji](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 64-bitowej wersji pakietu Office można również uruchomić rozwiązań pakietu Office, które zostały utworzone przy użyciu szablonów projektu dla systemu Microsoft Office 2007 w programie Visual Studio 2008. Nie obsługują one jednak rozwiązań dla pakietu Office utworzonych przy użyciu szablonów projektów programu Microsoft Office 2003 w środowisku Visual Studio 2008 ani rozwiązań dla pakietu Office utworzonych w programie Visual Studio 2005. Aby uzyskać więcej informacji, zobacz [uruchamiania rozwiązań w różnych wersjach Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).  
  
## <a name="repairing-the-visual-studio-2010-tools-for-office-runtime"></a>Naprawianie oprogramowania Visual Studio 2010 Tools for Office Runtime  
 Jeśli musisz naprawić środowiska uruchomieniowego, otwórz **programy i funkcje** lub **Dodaj lub usuń programy** w Panelu sterowania, wybierz **Microsoft Visual Studio 2010 Tools for Office Runtime**na liście programy, a następnie kliknij przycisk **Odinstaluj**. Zostanie uruchomiony program instalacyjny, który umożliwi naprawę środowiska. Jeśli klikniesz przycisk **zmiany**, nie podano opcję naprawy środowiska uruchomieniowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Tools for Office Runtime ― scenariusze instalacji](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Zestawy w Visual Studio Tools for Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)   
 [Architektura rozwiązań pakietu Office w Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architektura Dostosowywanie na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Uaktualnianie i migracja rozwiązań pakietu Office](../vsto/upgrading-and-migrating-office-solutions.md)  
  
  