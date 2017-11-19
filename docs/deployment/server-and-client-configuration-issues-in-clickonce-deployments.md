---
title: "Serwer i problemy z konfiguracją klienta we wdrożeniach ClickOnce | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- Windows applications, ClickOnce deployments
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
caps.latest.revision: "33"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 4b7153b0a20c10e7dbdb31ac943f150f72cb39d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>Problemy konfiguracji serwera i klienta we wdrożeniach ClickOnce
Jeśli używasz usług Internet Information Services (IIS) w systemie Windows Server, a wdrożenie zawiera typ pliku, który jest rozpoznawane przez system Windows, takich jak plik programu Microsoft Word, usługi IIS będą odrzucać do przesyłania pliku, a wdrożenie zakończy się niepowodzeniem.  
  
 Ponadto niektóre serwery i sieci Web aplikacji, takich jak [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], zawiera listę plików i typów plików, które nie mogą pobrać. Na przykład [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uniemożliwia pobieranie wszystkich plików Web.config. Te pliki mogą zawierać poufne informacje, takie jak nazwy użytkowników i hasła.  
  
 Mimo że to ograniczenie nie powinno powodować bez problemów pobierania core [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] plików, takich jak manifestów i zestawy, to ograniczenie może uniemożliwić pobieranie plików danych zawartych w ramach Twojej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. W [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], można rozwiązać ten problem, usuwając program obsługi, który uniemożliwia pobieranie tych plików z Menedżera konfiguracji usług IIS. Zobacz dokumentacji serwera IIS, aby uzyskać dodatkowe szczegóły.  
  
 Niektóre serwery sieci Web mogą blokować pliki z rozszerzeniami DLL, .config i .mdf. Aplikacje systemu Windows zwykle zawierają pliki niektóre z tych rozszerzeń. Jeśli użytkownik spróbuje uruchomić [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, która uzyskuje dostęp do pliku zablokowany na serwerze sieci Web, spowoduje błąd. Zamiast odblokowywania wszystkich rozszerzeń plików, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] publikuje każdy plik aplikacji z rozszerzeniem ".deploy" domyślnie. W związku z tym administrator musi tylko do konfigurowania serwera sieci Web, aby odblokować następujące trzy rozszerzenia:  
  
-   .Application  
  
-   Manifest  
  
-   .Deploy  
  
 Jednak wyłączyć tę opcję, usuwając zaznaczenie **rozszerzeniem ".deploy"** opcja [publikowania opcje — Okno dialogowe](http://msdn.microsoft.com/en-us/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), w którym to przypadku należy skonfigurować serwer sieci Web, aby odblokować wszystkie rozszerzenia plików używane w aplikacji.  
  
 Konieczne będzie skonfigurować manifest, .application i .deploy, na przykład jeśli korzystasz z usług IIS, w którym nie zainstalowano [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], lub jeśli używasz innego serwera sieci Web (na przykład Apache).  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce i Secure Sockets Layer (SSL)  
 A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja będzie działać prawidłowo przy użyciu protokołu SSL, z wyjątkiem przypadków, gdy program Internet Explorer zgłasza monit o certyfikat SSL. Monit mogą być wywoływane, gdy istnieje problem z certyfikatem, takie jak kiedy nazwy lokacji nie są zgodne lub certyfikat wygasł. Aby [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] działać przez połączenie SSL, upewnij się, że certyfikat jest aktualny i że dane certyfikatu odpowiada danych lokacji.  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce i uwierzytelnianie serwera Proxy  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]obsługuje zintegrowane uwierzytelnianie systemu Windows serwera proxy w programie .NET Framework 3.5. Nie dyrektywy określonych machine.config nie są wymagane. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]nie zapewniają obsługę innych protokołów uwierzytelniania, takich jak podstawowe lub szyfrowane.  
  
 Można również zastosować poprawkę do .NET Framework 2.0, aby włączyć tę funkcję. Aby uzyskać więcej informacji zobacz http://go.microsoft.com/fwlink/?LinkId=158730.  
  
 Aby uzyskać więcej informacji, zobacz [ \<defaultProxy — > elementu (ustawienia sieciowe)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).  
  
## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce i zgodność z przeglądarkami sieci Web  
 Obecnie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalacji zostanie uruchomiony tylko wtedy, gdy adres URL, który manifest rozmieszczenia jest otwarty przy użyciu programu Internet Explorer. Wdrożenia, którego adres URL jest uruchamiana z innej aplikacji, takich jak Microsoft Office Outlook, zostanie uruchomiony pomyślnie tylko wtedy, gdy program Internet Explorer jest ustawiony jako domyślnej przeglądarki sieci Web.  
  
> [!NOTE]
>  Mozilla Firefox jest obsługiwana, gdy dostawca rozmieszczenia nie jest pusty lub zainstalowano program Microsoft .NET Framework Assistant rozszerzenia. To rozszerzenie jest dostarczana z programu .NET Framework 3.5 z dodatkiem SP1. Obsługę XBAP NPWPF wtyczka została aktywowana w razie potrzeby.  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>Aktywacja aplikacji ClickOnce za pomocą skryptów w przeglądarce  
 Jeśli korzystasz niestandardowe strony sieci Web, który uruchamia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji przy użyciu wykonywanie aktywnych skryptów może się okazać, że aplikacji nie będą uruchamiane na niektórych maszynach. Program Internet Explorer zawiera ustawienie o nazwie **automatyczne monitowanie do pobierania plików**, co ma wpływ na to zachowanie. To ustawienie jest dostępne na **zabezpieczeń** karcie w jego **opcje** menu, które ma wpływ na to zachowanie. Jest to **automatyczne monitowanie do pobierania plików**, i znajduje się poniżej **pobiera** kategorii. Właściwość jest ustawiona na **włączyć** domyślnie dla stron sieci Web w sieci intranet, a także do **wyłączyć** domyślnie dla stron sieci Web. Jeśli to ustawienie jest równa **wyłączyć**, próby aktywacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji programowo (na przykład, przypisując jej adres URL do `document.location` właściwości) będą blokowane. W takim przypadku użytkowników można uruchomić aplikacji tylko za pośrednictwem pobierania zainicjowane przez użytkownika, na przykład przez kliknięcie hiperłącza Ustaw adres URL aplikacji.  
  
## <a name="additional-server-configuration-issues"></a>Problemy z konfiguracją dodatkowego serwera  
  
##### <a name="administrator-permissions-required"></a>Wymagane uprawnienia administratora  
 W przypadku publikowania protokołu HTTP, musi mieć uprawnienia administratora na serwerze docelowym. Usługi IIS wymaga tego poziomu uprawnień. Jeśli przy użyciu protokołu HTTP nie jest publikowany, musisz tylko mieć uprawnienia zapisu w ścieżce docelowej.  
  
##### <a name="server-authentication-issues"></a>Problemy z uwierzytelnianiem serwera  
 Podczas publikowania na serwerze zdalnym, który ma "Dostęp anonimowy" wyłączone, pojawi się następujące ostrzeżenie:  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  Umożliwia uwierzytelnianie NTLM (żądanie odpowiedź NT) działają, jeśli lokacji monituje o podanie poświadczeń innych niż poświadczenia domyślne, a w oknie dialogowym Zabezpieczenia kliknij **OK** po wyświetleniu monitu, jeśli chcesz zapisać podana poświadczenia na potrzeby przyszłych sesji. To rozwiązanie nie będzie działać dla uwierzytelniania podstawowego.  
  
## <a name="using-third-party-web-servers"></a>Korzystanie z serwerów sieci Web innych firm  
 Jeśli wdrażasz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji z serwera sieci Web innego niż IIS, problem może wystąpić, jeśli serwer zwrócił nieprawidłowy typ zawartości key [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] plików, takich jak manifest wdrażania i manifest aplikacji. Aby rozwiązać ten problem, zobacz Pomoc dla serwera sieci Web, w dokumentacji, jak dodać nowe typy zawartości do serwera i upewnij się, że wszystkie pliku rozszerzenia mapowania nazw wymienione w poniższej tabeli znajdują się w miejscu.  
  
|Rozszerzenie nazwy pliku|Typ zawartości|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>ClickOnce i zamapowanych dysków  
 Jeśli publikowanie aplikacji ClickOnce za pomocą programu Visual Studio nie może określić mapowany dysk jako lokalizacji instalacji. Jednak można modyfikować aplikacji ClickOnce, aby zainstalować z dysku zmapowanego za pomocą generatora manifestu i Edytor (Mage.exe i MageUI.exe). Aby uzyskać więcej informacji, zobacz [Mage.exe (Generowanie manifestu i edytowania narzędzie)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) i [MageUI.exe (Generowanie manifestu i edytowania narzędzia graficzne klienta)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>Protokół FTP nieobsługiwane w przypadku instalowania aplikacji  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]obsługuje instalowanie aplikacji z dowolnego serwera HTTP 1.1 w sieci Web lub serwera plików. FTP, protokół transferu plików, nie jest obsługiwana w przypadku instalowania aplikacji. FTP umożliwia publikowanie tylko aplikacji. Poniższa tabela zawiera podsumowanie tych różnic:  
  
|Typ adresu URL|Opis|  
|--------------|-----------------|  
|FTP: / /|Możesz opublikować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji przy użyciu tego protokołu.|  
|http://|Można zainstalować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji przy użyciu tego protokołu.|  
|https://|Można zainstalować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji przy użyciu tego protokołu.|  
|File://|Można zainstalować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji przy użyciu tego protokołu.|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Systemie Windows XP z dodatkiem SP2: Zapora systemu Windows  
 Domyślnie Windows XP z dodatkiem SP2 umożliwia włączenie zapory systemu Windows. Jeśli tworzysz aplikację na komputerze z systemem Windows XP zainstalowany jest nadal możliwość publikowania, a następnie uruchom [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje z lokalnego serwera, na którym działa program IIS. Jednak nie można uzyskać dostępu do tego serwera, który jest uruchomiony program IIS z innego komputera, jeśli nie możesz otworzyć zapory systemu Windows. Aby uzyskać instrukcje na temat zarządzania Zaporą systemu Windows można znaleźć w Pomocy systemu Windows.  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Systemie Windows Server: Rozszerzenia serwera FrontPage Włącz  
 Rozszerzenia serwera FrontPage firmy Microsoft jest wymagana w przypadku publikowania aplikacji na serwerze sieci Web systemu Windows, który korzysta z protokołu HTTP.  
  
 Domyślnie system Windows Server nie ma zainstalowanych rozszerzeń serwera FrontPage. Jeśli chcesz użyć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do publikowania na serwer sieci Web systemu Windows Server, który korzysta z protokołu HTTP z rozszerzeń serwera FrontPage, należy zainstalować rozszerzenia serwera FrontPage najpierw. Instalację można wykonać za pomocą narzędzia administracyjnego Zarządzanie tym serwerem w systemie Windows Server.  
  
## <a name="windows-server-locked-down-content-types"></a>Systemu Windows Server: Typy zawartości w trybie blokady  
 Usługi IIS w [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] blokad w dół wszystkich typów plików, z wyjątkiem niektórych znanych typów zawartości (na przykład htm, HTML, txt i tak dalej). Aby umożliwić wdrożenie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji za pomocą tego serwera, musisz zmienić ustawienia programu IIS, aby umożliwić pobieranie plików typu .application, manifest i innych typów plików niestandardowych używanych przez aplikację.  
  
 W przypadku wdrożenia przy użyciu serwera usług IIS, uruchom inetmgr.exe i dodać nowe typy plików dla domyślnej strony sieci Web:  
  
-   Dla rozszerzeń .application i manifest typ MIME powinien być "application/x-ms aplikacji." W przypadku innych typów plików typ MIME powinien być "application/octet-stream."  
  
-   W przypadku utworzenia typu MIME z rozszerzeniem "*" i typ MIME "application/octet-stream" umożliwi plików odblokowany typu do pobrania. (Jednak zablokowany plik, którego nie można pobrać typów, takie jak aspx i .asmx).  
  
 Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania typy MIME w systemie Windows Server, zobacz artykuł bazy wiedzy Microsoft Knowledge Base KB326965, "Usług IIS 6.0 jest nie obsługiwać nieznane typy MIME" w [http://support.microsoft.com/default.aspx?scid=kb;en-us;326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  
  
## <a name="content-type-mappings"></a>Mapowanie typu zawartości  
 Podczas publikowania za pośrednictwem protokołu HTTP, typu zawartości (znanej także jako typ MIME) dla pliku .application powinna być "application/x-ms aplikacji." Jeśli masz [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] zainstalowane na serwerze, to zostanie ustawiona dla Ciebie automatycznie. Jeśli to nie jest zainstalowany, a następnie musisz utworzyć skojarzenia typu MIME dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vroot aplikacji (lub cały serwer).  
  
 W przypadku wdrożenia przy użyciu serwera usług IIS, należy uruchomić inetmgr.exe i dodać nowy typ zawartości "application/x-ms aplikacji" rozszerzenia .application.  
  
## <a name="http-compression-issues"></a>Problemy z kompresji HTTP  
 Z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], można wykonywać pliki do pobrania, które używają kompresji HTTP, technologia serwer sieci Web, która używa algorytmu GZIP kompresowania strumienia danych przed wysłaniem strumienia do klienta. Klient — w takim przypadku [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]— dekompresuje strumienia przed odczyt plików.  
  
 Jeśli korzystasz z usług IIS, można łatwo włączyć kompresję HTTP. Jednak po włączeniu kompresji HTTP obejmującej go jest włączona tylko dla niektórych typów plików — to znaczy, pliki HTML i tekstowych. Aby włączyć kompresję dla zestawów (dll), XML (.xml), manifesty wdrożenia (.application) i manifestów aplikacji (manifest), niezbędny następujące typy plików do listy typów dla usługi IIS mają skompresować. Do momentu dodania typy plików do wdrożenia, zostanie skompresowany tylko tekst i pliki HTML.  
  
 Aby uzyskać szczegółowe instrukcje dotyczące usług IIS, zobacz [jak określić dodatkowe typy kompresji HTTP](http://go.microsoft.com/fwlink/?LinkId=178459).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Wymagania wstępne dotyczące wdrażania aplikacji](../deployment/application-deployment-prerequisites.md)