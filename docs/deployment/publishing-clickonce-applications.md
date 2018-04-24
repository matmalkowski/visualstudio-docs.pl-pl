---
title: Publikowanie aplikacji ClickOnce | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Options
- Microsoft.VisualStudio.Publish.ClickOnceProvider.PublishWizard.Help
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- ClickOnce applications, publishing
- applications [Visual Studio], ClickOnce deployment
- deploying applications [ClickOnce], publishing ClickOnce applications
ms.assetid: eb6dfe79-f54c-4331-8e36-073688e70973
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5f0c04a23844664b5bbfa67a6e83809c250b8a9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="publishing-clickonce-applications"></a>Publikowanie aplikacji ClickOnce
Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] właściwości publikowania aplikacji po raz pierwszy, można ustawić za pomocą Kreatora publikacji. Tylko kilka właściwości są dostępne w Kreatorze; wszystkie inne właściwości są ustawiane na wartości domyślne.  
  
 Kolejne zmiany, aby opublikować właściwości są dokonywane na **publikowania** strony **projektanta projektu**.  
  
## <a name="publish-wizard"></a>Kreator publikacji  
 Kreator publikowania służy do konfigurowania podstawowych ustawień do publikowania aplikacji. Obejmuje to następujące właściwości publikacji:  
  
-   Publikowanie lokalizacji folderu - gdzie Visual Studio skopiuje pliki (komputer lokalny, sieciowego udziału plików, serwer FTP lub witryny sieci Web)  
  
-   Lokalizacja folderu instalacji - gdzie użytkownicy końcowi będą przeprowadzać z (sieciowego udziału plików, serwer FTP, witryn sieci Web, dysk CD/DVD)  
  
-   Dostępność online lub Offline — Jeśli użytkownicy końcowi mogą uzyskać dostęp do aplikacji z lub bez połączenia sieciowego  
  
-   Zaktualizuj częstotliwość — jak często Aplikacja sprawdza dostępność nowych aktualizacji.  
  
 Aby uzyskać więcej informacji, zobacz [porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
## <a name="publish-page"></a>Strona publikowania  
 **Publikowania** strony **projektanta projektu** służy do konfigurowania właściwości wdrażania ClickOnce. W poniższej tabeli wymieniono — tematy  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: określanie lokalizacji kopiowania plików przez program Visual Studio](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|Opisuje sposób ustawiania, którym Visual Studio umieszcza pliki aplikacji i manifestów.|  
|[Instrukcje: określanie lokalizacji, z której użytkownicy końcowi będą przeprowadzać instalacje](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|Opisuje sposób ustawiania lokalizacji, gdzie użytkownicy do pobrania i zainstalowania aplikacji.|  
|[Instrukcje: określanie trybu offline lub online instalowania za pomocą technologii ClickOnce](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|Opisuje sposób określić, czy aplikacja będzie dostępna w trybie offline lub online.|  
|[Instrukcje: ustawienie wersji publikacji technologii ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)|Opisuje sposób ustawiania ClickOnce **publikowania wersji** właściwość, która określa, czy w przypadku publikowania aplikacji będzie traktowany jako aktualizacji.|  
|[Instrukcje: automatyczne zwiększenie wersji publikacji ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|Opisuje sposób automatyczne zwiększenie numeru wersji **PublishVersion** zawsze będziesz publikować aplikację.|  
  
 Aby uzyskać więcej informacji, zobacz [strona publikowania, Projektant projektu](../ide/reference/publish-page-project-designer.md)  
  
### <a name="application-files-dialog-box"></a>Okno dialogowe pliki aplikacji  
 To okno dialogowe umożliwia określenie, jak pliki w projekcie są podzielone dla publikacji, dynamiczne pobierania i aktualizowania. Zawiera ona Siatka wyświetla pliki projektu, które nie zostały wykluczone domyślnie, lub które mają grupy pobierania.  
  
 Aby wykluczyć pliki, pliki są oznaczane jako pliki danych lub wymagania wstępne i tworzenia grup plików warunkowego instalacji w interfejsie użytkownika programu Visual Studio, zobacz [porady: Określ, które pliki są publikowane za pomocą technologii ClickOnce](../deployment/how-to-specify-which-files-are-published-by-clickonce.md). Można również oznaczyć pliki danych przy użyciu Mage.exe. Aby uzyskać więcej informacji, zobacz [porady: uwzględnianie pliku danych w aplikacji ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
### <a name="prerequisites-dialog-box"></a>Wstępnie wymagane składniki — Okno dialogowe  
 To okno dialogowe określa, które wstępnie wymagane składniki są zainstalowane, oraz jak są one zainstalowane. Aby uzyskać więcej informacji, zobacz [porady: instalowanie wstępnie wymaganych składników w aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) i [wstępnie wymagane składniki — okno dialogowe](../ide/reference/prerequisites-dialog-box.md).  
  
### <a name="application-updates-dialog-box"></a>Okno dialogowe aktualizacje aplikacji  
 To okno dialogowe określa sposób instalacji aplikacji ma sprawdzać dostępność aktualizacji. Aby uzyskać więcej informacji, zobacz [porady: Zarządzanie aktualizacji dla aplikacji ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md).  
  
### <a name="publish-options-dialog-box"></a>Opcje — okno dialogowe publikowania  
 Okno dialogowe Opcje publikowania Określa opcje wdrażania aplikacji.  
  
|||  
|-|-|  
|[Instrukcje: zmienianie języka publikacji dla aplikacji ClickOnce](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|Opisuje sposób określenia języka i kultury odpowiadające zlokalizowanej wersji.|  
|[Instrukcje: określanie nazwy menu Start dla aplikacji ClickOnce](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|W tym artykule opisano, jak zmienić nazwę wyświetlaną dla aplikacji ClickOnce.|  
|[Instrukcje: określanie linku do pomocy technicznej](../deployment/how-to-specify-a-link-for-technical-support.md)|Opisuje sposób ustawiania **adres URL pomocy technicznej** właściwość, która identyfikuje strony sieci Web lub udziału plików, których użytkownicy można przejść do uzyskania informacji na temat aplikacji.|  
|[Instrukcje: określanie adresu URL pomocy technicznej dla indywidualnych wstępnie wymaganych składników wdrożenia ClickOnce](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|Przedstawiono sposób ręcznej modyfikacji manifest aplikacji w celu uwzględnienia obsługi poszczególnych adresów URL, dla każdego wstępnie wymaganego programu.|  
|[Instrukcje: określanie strony publikowania dla aplikacji ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|Opisuje sposób wygenerowania i opublikowania domyślnej strony sieci Web (publish.htm) oraz aplikacji|  
|[Porady: dostosowywanie ClickOnce domyślnej strony sieci Web](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|Opisuje sposób dostosowywania strony sieci Web, który jest automatycznie generowany i opublikowani razem aplikacji.|  
|[Instrukcje: włączenie funkcji AutoStart dla instalacji z dysku CD](../deployment/how-to-enable-autostart-for-cd-installations.md)|Opisuje sposób włączyć automatyczne uruchamianie aplikacji ClickOnce jest uruchamiane automatycznie, gdy znajduje się nośnik.|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: tworzenie skojarzeń plików dla aplikacji ClickOnce](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|Opisuje sposób dodawania obsługi rozszerzenia nazw plików dla aplikacji ClickOnce.|  
|[Instrukcje: pobieranie informacji o ciągu zapytania w aplikacji ClickOnce w trybie online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|Pokazuje, jak pobrać parametry przekazywane w adresie URL używane do uruchamiania aplikacji ClickOnce.|  
|[Instrukcje: wyłączanie aktywacji adresu URL aplikacji ClickOnce za pomocą Projektanta](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|Opisuje sposób wymusić użytkownikom na uruchamianie aplikacji z **Start** menu przy użyciu projektanta.|  
|[Instrukcje: wyłączanie aktywacji adresu URL aplikacji ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|Opisuje sposób wymusić użytkownikom na uruchamianie aplikacji z **Start** menu.|  
|[Przewodnik: pobieranie zestawów na żądanie przy użyciu wdrażania interfejsu API ClickOnce za pomocą Projektanta](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|Wyjaśniono, jak pobrać zestawów aplikacji tylko wtedy, gdy najpierw są one używane przez aplikację przy użyciu narzędzia Projektant.|  
|[Przewodnik: pobieranie zestawów na żądanie przy użyciu wdrażania interfejsu API ClickOnce](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Wyjaśniono, jak pobrać zestawów aplikacji tylko wtedy, gdy najpierw są one używane przez aplikację.|  
|[Przewodnik: pobieranie zestawów satelickich na żądanie przy użyciu wdrażania interfejsu API ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Opisuje sposób oznaczyć ponownie zestawy satelickie jako opcjonalne i pobierania zestawu, komputer kliencki musi uzyskać bieżące ustawienia kultury.|  
|[Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|Opisano sposób wdrażania aplikacji ClickOnce za pomocą narzędzi .NET Framework.|  
|[Przewodnik: ręczne wdrażanie aplikacji ClickOnce, które nie wymagają ponownego podpisywania i zachowują informacje o znakowaniu](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)|Wyjaśniono, jak wdrożyć aplikację ClickOnce bez ponownego podpisywania manifestów za pomocą narzędzi .NET Framework.|  
|[Instrukcje: Konfigurowanie projektów pod kątem platform docelowych](../ide/how-to-configure-projects-to-target-platforms.md)|Opisano sposób publikowania dla 64-bitowy procesor, zmieniając **Procesora docelowej** lub **platformy docelowej** właściwości projektu.|  
|[Wskazówki: Włączanie aplikacji ClickOnce do uruchamiania na wielu wersje programu .NET Framework](http://msdn.microsoft.com/en-us/7f4383af-ed87-4853-b4d4-02a3967a5fd9)|Wyjaśniono, jak włączyć aplikacji ClickOnce zainstalować i uruchomić z różnymi wersjami NET Framework.|  
|[Przewodnik: tworzenie niestandardowego Instalatora dla aplikacji ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|Wyjaśnia sposób tworzenia niestandardowego Instalatora, aby zainstalować aplikację ClickOnce.|  
|[Instrukcje: publikowanie aplikacji WPF przy użyciu włączonej funkcji stylów wizualnych](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|Zawiera instrukcje krok po kroku, aby rozwiązać problem, który pojawia się podczas próby opublikowania aplikacji WPF, który ma włączyć style wizualne.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia ClickOnce i wdrażania](../deployment/clickonce-security-and-deployment.md)   
 [Dokumentacja ClickOnce](../deployment/clickonce-reference.md)