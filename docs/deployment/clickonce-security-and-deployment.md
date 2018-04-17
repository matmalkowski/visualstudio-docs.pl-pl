---
title: Zabezpieczenia ClickOnce i wdrażania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 24ebab9776c6cb0b829e1b79cb089ef6b826f726
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="clickonce-security-and-deployment"></a>Wskazówki dotyczące wdrażania ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jest to technologia wdrożenia, która umożliwia tworzenie samoaktualizacji aplikacji systemu Windows, które można instalować i uruchamiać z minimalnym interakcji. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zapewnia pełną obsługę publikowanie oraz aktualizowanie aplikacje wdrożone przy użyciu technologii ClickOnce, jeśli korzystasz z projektów z języka Visual Basic i Visual C#. Aby uzyskać informacje o wdrażaniu aplikacji Visual C++, zobacz [wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenie pozwala pokonać trzy poważne problemy we wdrożeniu:  
  
-   **Trudności w aktualizacji aplikacji.** Z wdrożeniem Instalator systemu Microsoft Windows zawsze, gdy aplikacja jest zaktualizowana, użytkownik może zainstalować aktualizację, plik msp i zastosować je do zainstalowanego produktu; z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia, możesz podać aktualizacje automatyczne. Są pobierane tylko te części aplikacji, które zostały zmienione, a następnie ponowna instalacja aplikacji pełne, zaktualizowane z nowego folderu side-by-side.  
  
-   **Wpływ na komputerze użytkownika.** Z wdrożenia Instalatora Windows, aplikacje często korzystają z udostępniane składniki o potencjalnych konfliktów wersji; z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia, każda aplikacja jest niezależna i nie może kolidować z innymi aplikacjami.  
  
-   **Uprawnienia zabezpieczeń.** Wdrażanie Instalatora systemu Windows wymaga uprawnień administracyjnych i umożliwia tylko ograniczone Instalacja dla użytkownika; [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrażania umożliwia użytkownikom innych niż administracyjne zainstalować i udziela tylko tych uprawnień zabezpieczeń dostępu kodu niezbędne dla aplikacji.  
  
 W przeszłości te problemy spowodowane czasami deweloperom zdecyduje się tworzenie aplikacji sieci Web zamiast aplikacji systemu Windows, interfejs użytkownika sformatowanego łatwość instalacji ograniczania. Za pomocą aplikacje wdrażane za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], może mieć najlepsze cechy obu tych technologii.  
  
## <a name="what-is-a-clickonce-application"></a>Co to jest aplikacji ClickOnce?  
 A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jest aplikacji Windows Presentation Foundation (.xbap), program Windows Forms (.exe), aplikacji konsoli (.exe) lub rozwiązania do pakietu Office (.dll) publikowane za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] technologii. Możesz opublikować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji na trzy sposoby: ze strony sieci Web, z sieciowego udziału plików lub nośniki, takie jak dysku CD. A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji można zainstalować na komputerze użytkownika końcowego i uruchom lokalnie, nawet wtedy, gdy komputer jest w trybie offline lub jego może działać w trybie tylko w trybie online bez konieczności instalowania niczego trwale na komputerze użytkownika końcowego. Aby uzyskać więcej informacji, zobacz [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje mogą być samoaktualizacji; także sprawdzać nowsze wersje staną się dostępne i automatycznie zastąpić wszelkie zaktualizowane pliki. Deweloper można określić zachowanie aktualizacji; administrator sieci można również sterować Aktualizuj strategie, na przykład oznaczenia aktualizacji jako obowiązkowe. Aktualizacje można także cofnięta wcześniejszą wersję przez użytkownika końcowego lub przez administratora. Aby uzyskać więcej informacji, zobacz [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Ponieważ [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje są izolowane, instalowanie i uruchamianie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji nie można przerwać istniejących aplikacji. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje są niezależne; Każdy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja jest zainstalowana w celu i uruchom z bezpiecznego poszczególnych użytkowników, dla każdej aplikacji w pamięci podręcznej. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje uruchamiane w Internecie lub intranecie stref zabezpieczeń. W razie potrzeby, aplikacja może zażądać uprawnień z podwyższonym poziomem uprawnień zabezpieczeń. Aby uzyskać więcej informacji, zobacz [zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="how-clickonce-security-works"></a>Jak działają zabezpieczenia ClickOnce  
 Podstawowe [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zabezpieczenia są oparte na zasady zabezpieczenia dostępu kodu, certyfikatami i wiersz zaufania ClickOnce.  
  
### <a name="certificates"></a>Certyfikaty  
 Authenticode certyfikaty są używane do weryfikacji autentyczności wydawcy aplikacji. Za pomocą kodu Authenticode dla wdrożenia aplikacji, technologii ClickOnce zapobiega szkodliwe program portraying się jako program uzasadnionych ustanowione, zaufanego źródła. Opcjonalnie certyfikaty mogą również służyć do podpisywania aplikacji i manifesty wdrożenia w celu potwierdzenia, że pliki nie zostały zmodyfikowane. Aby uzyskać więcej informacji, zobacz [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md). Certyfikaty mogą służyć do konfigurowania komputerów klienckich, aby wyświetlić listę zaufanych wydawców. Jeśli aplikacja jest pochodzi z zaufanego wydawcę, można zainstalować bez interakcji użytkownika. Aby uzyskać więcej informacji, zobacz [zaufane Omówienie wdrożenia aplikacji](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="code-access-security"></a>Zabezpieczenia dostępu kodu  
 Zabezpieczenia dostępu kodu pomaga ograniczyć dostęp do chronionych zasobów z kodu. W większości przypadków można strefach Internet lub lokalny Intranet, aby ograniczyć uprawnienia. Użyj **zabezpieczeń** strony **ProjectDesigner** żądania strefy odpowiednie dla aplikacji. Można również debugowania aplikacji z ograniczonymi uprawnieniami, aby emulować środowisko użytkownika końcowego. Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
### <a name="clickonce-trust-prompt"></a>Wiersz zaufania ClickOnce  
 Jeśli aplikacja wymaga więcej uprawnień niż zezwala na strefy, użytkownik końcowy może monit podjęcia decyzji o zaufaniu. Użytkownik końcowy może zdecydować, jeśli aplikacji ClickOnce, takich jak aplikacji formularzy systemu Windows, aplikacje systemu Windows Presentation Foundation aplikacji konsoli, aplikacje przeglądarki XAML i rozwiązań pakietu Office zaufany, aby uruchomić. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie zachowania monitu o zaufanie ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## <a name="how-clickonce-deployment-works"></a>Jak działa wdrażania ClickOnce  
 Podstawowe [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] architektura wdrażania opiera się na dwóch plików manifestu XML: manifest aplikacji i manifest wdrażania. Pliki są używane do opisywania zainstalowaną aplikacji ClickOnce z, jak są aktualizowane i kiedy są aktualizowane.  
  
### <a name="publishing-clickonce-applications"></a>Publikowanie aplikacji ClickOnce  
 Manifest aplikacji zawiera opis aplikacji. W tym zestawów, zależności i pliki wchodzące w skład aplikacji wymaganych uprawnień i lokalizacji, w której będą dostępne aktualizacje. Deweloper aplikacji autorów manifest aplikacji za pomocą kreatora Publikowanie w Visual Studio lub generowanie manifestu i edytowania narzędzia (Mage.exe) [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Aby uzyskać więcej informacji, zobacz [porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
 Manifest rozmieszczenia w tym artykule opisano sposób wdrażania aplikacji. Obejmuje to lokalizacja manifestu aplikacji i wersja aplikacji, który należy uruchamiać klientów.  
  
### <a name="deploying-clickonce-applications"></a>Wdrażanie technologii ClickOnce  
 Po jego utworzeniu manifest rozmieszczenia jest kopiowany do lokalizacji wdrożenia. Może to być serwer sieci Web, sieciowego udziału plików lub nośniki, takie jak dysk CD. Manifest aplikacji i wszystkich plików aplikacji są również kopiowane do lokalizacji wdrożenia, która została określona w manifeście rozmieszczenia. Może to być taka sama jak lokalizacja wdrożenia, lub można ją z innej lokalizacji. Korzystając z **Kreator publikowania** w programie Visual Studio, operacje kopiowania są wykonywane automatycznie.  
  
### <a name="installing-clickonce-applications"></a>Instalowanie aplikacji ClickOnce  
 Po jej wdrożeniu do lokalizacji wdrożenia, użytkownicy końcowi można pobrać i zainstalować aplikację, klikając ikonę reprezentujący plik manifestu wdrożenia na stronie sieci Web lub w folderze. W większości przypadków użytkownik końcowy zobaczy proste okno dialogowe z pytaniem użytkownika o potwierdzenie instalacji, po których instalacja będzie kontynuowana i uruchamiania aplikacji bez interwencji dodatkowe. W przypadkach, gdy aplikacja wymaga uprawnień z podwyższonym poziomem uprawnień lub jeśli aplikacja nie jest podpisany przez zaufany certyfikat okno dialogowe pyta użytkownika, aby udzielić uprawnień, aby kontynuować instalację. Chociaż instaluje ClickOnce są na użytkownika, podniesienia uprawnień może być wymagane, jeśli istnieją wymagania wstępne, które wymagają uprawnień administratora. Aby uzyskać więcej informacji o podwyższonym poziomem uprawnień, zobacz [zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md).  
  
 Certyfikaty jest zaufany na poziomie maszyny lub enterprise, aby ClickOnce — aplikacje podpisane zaufanym certyfikatem można zainstalować w trybie dyskretnym. Aby uzyskać więcej informacji o zaufanych certyfikatów, zobacz [zaufanych Omówienie wdrożenia aplikacji](../deployment/trusted-application-deployment-overview.md).  
  
 Aplikację można dodać do użytkownika **Start** menu i **Dodaj lub usuń programy** w **Panelu sterowania**. W przeciwieństwie do innych technologii wdrażania, nic nie jest dodane do **Program Files** lub rejestru, a nie prawa administracyjne są wymagane do instalacji  
  
> [!NOTE]
>  Istnieje również możliwość uniemożliwiają aplikacji dodawanych do **Start** menu i **Dodaj lub usuń programy** grupy, ułatwiając skutkuje przypominają aplikacji sieci Web. Aby uzyskać więcej informacji, zobacz [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### <a name="updating-clickonce-applications"></a>Aktualizowanie aplikacji ClickOnce  
 Deweloperzy aplikacji tworzenia zaktualizowaną wersję aplikacji, generowanie nowego manifest aplikacji i skopiuj pliki do lokalizacji wdrożenia — zwykle równorzędny folder do oryginalnego folderu wdrożenia aplikacji. Administrator aktualizuje manifest wdrażania, aby wskazać lokalizację nowej wersji aplikacji.  
  
> [!NOTE]
>  **Kreator publikowania** w programie Visual Studio może służyć do wykonania tych czynności.  
  
 Oprócz lokalizacji wdrożenia manifest wdrażania zawiera lokalizacji aktualizacji (strona sieci Web lub pliku w udziale sieciowym), gdzie aplikacja sprawdza, czy zaktualizowane wersje. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] **Publikowanie** właściwości są używane do określania, kiedy i jak często aplikacja ma sprawdzać dostępność aktualizacji. Zachowanie aktualizacji można określić w manifeście rozmieszczenia lub mogą być przedstawiane jako opcje użytkownika w interfejsie użytkownika aplikacji za pomocą klasy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] interfejsów API. Ponadto **publikowania** właściwości można zastosować powoduje, że aktualizacje obowiązkowe lub do przywrócenia starszej wersji. Aby uzyskać więcej informacji, zobacz [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### <a name="third-party-installers"></a>Instalatorzy innych firm  
 Można dostosować Instalatorem ClickOnce do zainstalowania składników innych firm oraz aplikacji. Musi mieć pakiet redystrybucyjny programu (plik .exe i .msi) i opisz pakietu z manifestu produkt niezależny od języka i manifestu pakietu specyficzny dla języka. Aby uzyskać więcej informacji, zobacz [tworzenie pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md).  
  
## <a name="clickonce-tools"></a>Narzędzia ClickOnce  
 W poniższej tabeli przedstawiono narzędzia czy służy do generowania, edytowania, zaloguj się i ponowne podpisywanie manifestów aplikacji i wdrażania.  
  
|Narzędzie|Opis|  
|----------|-----------------|  
|[Strona zabezpieczeń, Projektant projektu](../ide/reference/security-page-project-designer.md)|Znaki manifestów aplikacji i wdrażania.|  
|[Strona publikowania, Projektant projektu](../ide/reference/publish-page-project-designer.md)|Generuje i edycji manifestów aplikacji i wdrażania dla aplikacji Visual Basic i Visual C#.|  
|[Mage.exe (narzędzie generowania manifestu i edytowania)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|Generuje manifestów aplikacji i wdrażania dla aplikacji Visual Basic, Visual C# i Visual C++.<br /><br /> Podpisuje i manifestów aplikacji i wdrażania zaloguje się ponownie.<br /><br /> Można uruchomić z wiersza polecenia i skrypty partii.|  
|[MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|Generuje i edycji manifestów aplikacji i wdrażania.<br /><br /> Podpisuje i manifestów aplikacji i wdrażania zaloguje się ponownie.|  
|[GenerateApplicationManifest, zadanie](../msbuild/generateapplicationmanifest-task.md)|Generuje manifest aplikacji.<br /><br /> Można uruchomić z programu MSBuild. Aby uzyskać więcej informacji, zobacz [odwołanie MSBuild](../msbuild/msbuild-reference.md).|  
|[GenerateDeploymentManifest, zadanie](../msbuild/generatedeploymentmanifest-task.md)|Generuje manifest wdrażania.<br /><br /> Można uruchomić z programu MSBuild. Aby uzyskać więcej informacji, zobacz [odwołanie MSBuild](../msbuild/msbuild-reference.md).|  
|[SignFile, zadanie](../msbuild/signfile-task.md)|Znaki manifestów aplikacji i wdrażania.<br /><br /> Można uruchomić z programu MSBuild. Aby uzyskać więcej informacji, zobacz [odwołanie MSBuild](../msbuild/msbuild-reference.md).|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Tworzenie aplikacji do wygenerowania manifestów aplikacji i wdrażania.|  
  
 W poniższej tabeli przedstawiono .NET Framework w wersji wymaganych do obsługi aplikacji ClickOnce w tych przeglądarek.  
  
|Przeglądarka|Wersja programu .NET Framework|  
|-------------|----------------------------|  
|Internet Explorer|2.0, 3.0, 3.5, 3.5 Z DODATKIEM SP1, 4|  
|Firefox|2.0 Z DODATKIEM SP1, 3.5 Z DODATKIEM SP1, 4|  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrożenie ClickOnce w systemie Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Wdrażanie składników COM za pomocą technologii ClickOnce](../deployment/deploying-com-components-with-clickonce.md)   
 [Tworzenie aplikacji ClickOnce z wiersza polecenia](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [Debugowanie aplikacji ClickOnce używających System.Deployment.Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)