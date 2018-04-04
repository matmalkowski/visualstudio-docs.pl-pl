---
title: Zainstalować i używać programu Visual Studio i usług Azure za serwerem zapory lub serwera proxy | Dokumentacja firmy Microsoft
description: ''
ms.custom: ''
ms.date: 02/12/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13f9f83c89e09e07d6024b779a89b9a6c4374112
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2018
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Zainstalować i używać programu Visual Studio i usług Azure za serwerem zapory lub serwera proxy
Jeśli Ty lub Twoja organizacja korzysta z środki bezpieczeństwa, takie jak Zapora lub serwer proxy, będą adresów URL domen, które możesz chcieć "dozwolone" i porty i protokoły, które można otworzyć, tak aby było możliwe najlepsze doświadczenia, podczas instalacji i używania Visual Stu dio i usług Azure.

* **[Zainstaluj program Visual Studio](#install-visual-studio)**: te tabele zawierają domeny adresów URL do listy dozwolonych adresów IP tak, aby mieć dostęp do wszystkich składników i obciążeń, które mają.

* **[Użyj programu Visual Studio i usług Azure](#use-visual-studio-and-azure-services)**: tabela zawiera adresy URL domeny do listy dozwolonych adresów IP i portów i protokołów, aby otworzyć tak, aby mieć dostęp do wszystkich funkcji i usług, które mają.

## <a name="install-visual-studio"></a>Zainstaluj program Visual Studio
### <a name="urls-to-whitelist"></a>Adresy URL do listy dozwolonych adresów IP
Ponieważ Instalator programu Visual Studio pobiera pliki z różnych domen i serwerów ich pobierania, Oto adresów URL domen, które możesz chcieć dozwolonych jako zaufane w interfejsie użytkownika lub w skryptach wdrożenia.

#### <a name="microsoft-domains"></a>Microsoft domains
| Domain | Cel |
| ------ | ------- |
| go.microsoft.com | Rozpoznawanie adresu URL instalacji |
| aka.MS | Rozpoznawanie adresu URL instalacji |
| download.visualstudio.microsoft.com | Ustawienia lokalizacji pobierania pakietów |
| download.microsoft.com | Ustawienia lokalizacji pobierania pakietów |
| download.visualstudio.com | Ustawienia lokalizacji pobierania pakietów |
| dl.xamarin.com | Ustawienia lokalizacji pobierania pakietów |
| visualstudiogallery.msdn.microsoft.com | Lokalizacja pobierania rozszerzenia programu Visual Studio |
| www.visualstudio.com | Lokalizacja dokumentacji |
| docs.microsoft.com | Lokalizacja dokumentacji |
| msdn.microsoft.com | Lokalizacja dokumentacji |
| www.microsoft.com | Lokalizacja dokumentacji |
| *.windows.net | Zaloguj się w lokalizacji |
| *.microsoftonline.com | Zaloguj się w lokalizacji |
| *.live.com | Zaloguj się w lokalizacji |
|  |  | |

#### <a name="non-microsoft-domains"></a>Domeny inne niż firmy Microsoft
| Domain | Instaluje te obciążenia |
| ------ | ------- |
| archive.apache.org |  Tworzenie przenośnych za pomocą języka JavaScript (Cordova) |
| cocos2d-x.org | Tworzenia gier za pomocą języka C++ (Cocos) |
| download.epicgames.com | Tworzenia gier za pomocą języka C++ (aparatu Unreal Engine) |
| download.oracle.com | Tworzenie przenośnych za pomocą języka JavaScript (zestaw SDK Java) <br /><br />Tworzenie przenośnych za pomocą platformy .NET (Java SDK) |
| download.unity3d.com | Tworzenie gier z Unity (Unity) |
| netstorage.unity3d.com | Tworzenie gier z Unity (Unity) |
| dl.google.com | Tworzenie przenośnych za pomocą języka JavaScript (zestaw SDK systemu Android i zestawu NDK, Emulator) <br /><br />Tworzenie przenośnych za pomocą platformy .NET (zestaw SDK systemu Android i zestawu NDK, Emulator) |
| www.incredibuild.com | Tworzenia gier za pomocą języka C++ (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Tworzenia gier za pomocą języka C++ (IncrediBuild) |
| www.python.org | Tworzenie Python (Python) <br /><br />Nauki dane i aplikacje analitycznego (Python) |
|  |  | |

## <a name="use-visual-studio-and-azure-services"></a>Program Visual Studio i usług Azure
### <a name="urls-to-whitelist-and-ports-and-protocols-to-open"></a>Adresy URL do listy dozwolonych adresów IP i portów i protokołów, aby otworzyć
Aby upewnić się, że masz dostęp do wszystkich składników, które są potrzebne, korzystając z programu Visual Studio lub usług Azure za serwerem zapory lub serwera proxy, w tym miejscu są adresy URL powinny listy dozwolonych adresów IP i portów i protokołów, które można otworzyć.

| Usługa lub scenariusza | Punkt końcowy DNS | Protokół | Port | Opis |
| --- | --- | --- | --- | --- |
| Adres URL<br>rozwiązanie | go.microsoft.com<br><br>aka.MS | | |Pozwala skrócić adresów URL, które następnie rozpoznać jako dłużej adresy URL
| Strona początkowa | vsstartpage.blob.core.windows.net | | 443| Używany do wyświetlania wiadomości dla programistów wyświetlany na stronie początkowej w Visual Studio |
| Docelowe<br> powiadomienia <br>Usługa | targetednotifications.azurewebsites.net <br><br>www.research.net | | 80<br><br>443| Używane do filtrowania globalnej listy powiadomień do listy, która ma zastosowanie tylko do określonych rodzajów scenariusze maszyn/użycia |
| Rozszerzenia <br>Sprawdzanie aktualizacji | visualstudiogallery.msdn.microsoft.com<br><br>&#42;.windows.net <br>&#42;.microsoftonline.com <br>&#42;.live.com  | | 443 | Używane w celu dostarczania powiadomienia, gdy dostępna jest aktualizacja zainstalowanego rozszerzenia <br><br> Używany jako lokalizacja logowania|
| Projekt AI <br>Integracja | az861674.vo.msecnd.net  | | 443<br> | Używane do konfigurowania nowych projektów, aby wysłać dane użycia na koncie usługi Application Insights w zarejestrowany |
| Obiektyw kodu | codelensprodscus1su0.app.<br>codelens.visualstudio.com | |443 | Używane w celu dostarczania informacji w edytorze o podczas ostatniej aktualizacji pliku, na osi czasu zmiany elementów pracy, które są skojarzone zmiany, autorów i więcej|
|Eksperymentalne <br>Włączanie funkcji  | visualstudio-devdiv-c2s.msedge.net | |80 | Użyć do aktywowania eksperymentalne nowe funkcje lub zmiany funkcji |
| Tożsamość "wskaźnik" <br>(nazwa użytkownika i awatara)<br>and <br>Ustawienia roamingu | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net  | |443 | Umożliwia wyświetlenie nazwy użytkownika i awatara w środowisku IDE <br><br> Używane, aby upewnić się, że zmiany w ustawieniach są przenoszone z jednego komputera na inny |
| Ustawienia zdalnego | az700632.vo.msecnd.net | | 443| Umożliwia wyłączenie rozszerzeń, które są znane, aby spowodować problemy w programie Visual Studio   |
| Narzędzia systemu Windows | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com |Protokół HTTPS |443 | Używany w scenariuszach magazynu aplikacji systemu Windows  |
| Schematu JSON <br>Odnajdywanie <br><br>Schematu JSON <br>Definicja<br><br>Schematu JSON <br>Obsługa dla <br>Zasoby platformy Azure| json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com| Http<br>Protokół HTTPS<br><br>Http<br><br>Protokół HTTPS |80<br>443 <br><br> 443<br><br>443 | Używane do odnajdywania i Pobierz schematów JSON, które użytkownik może użyć podczas edytowania dokumentów JSON <br><br>Używany do uzyskania schemat meta weryfikacji dla formatu JSON<br><br>Używany do uzyskania bieżącego schematu dla szablonów wdrożenia usługi Azure Resource Manager|
| Pakiet NPM <br>odnajdywanie  |Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io  | Protokół HTTPS<br><br>protokołu HTTP/s<br><br>Protokół HTTPS | 443<br><br>80/443<br><br>443| Wymagane przez wyszukiwanie pakietów NPM i używane do instalacji pakietu skryptu po stronie klienta w projekty sieci web |
|Bower pakietu<br> ikony<br><br>Bower pakietu <br>search  |Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | Http<br><br>Protokół HTTPS<br>Http<br>Protokół HTTPS|80<br><br>443<br>80<br>443 |Udostępnia domyślną ikonę pakietu bower  <br><br>Pozwala, aby wyszukać pakietów Bower |
|NuGet<br><br>Pakiet NuGet<br> odnajdywanie | Api.nuget.org <br>www.nuget.org <br>Nuget.org<br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com  | Protokół HTTPS<br><br>protokołu HTTP/s |443<br><br>80/443<br> |Używany do sprawdzania podpisanych pakietów NuGet.<br><br>Wymagane do wyszukiwania pakiety NuGet i wersje |
|Informacje o repozytorium GitHub  |api.github.com  |Protokół HTTPS | 443| Wymagane do uzyskania dodatkowych informacji na temat pakietów bower |
| Linteru sieci Web|Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org  | Http|80 | |
| Cookiecutter<br>Szablon Explorer<br>odnajdywanie <br><br>Cookiecutter <br>Eksplorator projektów<br> Tworzenie | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org  | Protokół HTTPS | 443<br> | Używana do wykrywania szablonów online z naszych kanał zalecane i repozytoriów github <br><br>Pozwala utworzyć projekt z szablonu cookiecutter, który wymaga instalacji na żądanie jednorazowe cookiecutter pakiet języka Python z indeksu pakietów języka Python (PyPI)|
| Pakiet języka Python <br>odnajdywanie<br><br>Pakiet języka Python <br>zarządzanie<br><br>Python <br>Nowy projekt <br>szablony| pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com| Protokół HTTPS| 443| Zapewnia możliwość wyszukiwania pip pakiety<br><br>Używany do automatycznej instalacji narzędzia pip, jeśli jest on niedostępny <br><br> Pozwala utworzyć <br><br>Używany do rozpoznania Python następujące szablony w oknie dialogowym Nowy projekt z adresami URL, cookiecutter szablonu projektu:<br> — Klasyfikator projekt<br>-Clustering projektu <br> -Regression projektu <br> -PyGame przy użyciu PyKinect <br> -Pyvot projektu |
| Sieci web pakietu Office <br>Dodatek <br> Manifest <br>Weryfikacja <br>Usługa | verificationservice.osi.office.net | Protokół HTTPS | 443 | Używany do sprawdzania poprawności manifesty dla pakietu Office web dodatki |
| SharePoint i <br>Dodatków pakietu Office | sharepoint.com | Protokół HTTPS | 443 | Używany do publikowania i testowania dodatków pakietu Office do usługi SharePoint Online i SharePoint |
| Workflow Manager <br>Testowanie usługi<br> Host |  | Http | 12292 | Reguły zapory, która jest automatycznie utworzone na potrzeby testowania dodatków programu SharePoint z przepływami pracy |
| Zbierane automatycznie <br>statystyki niezawodności <br>i innych <br>Obsługi klienta <br>Programów poprawy jakości (obsługi klienta CEIP)<br> dla zestawu SDK platformy Azure i <br>narzędzia SQL <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com |Protokół HTTPS | 443| Używane do wysyłania statystyki niezawodności (dane awarii/zawieszenia) od użytkownika do firmy Microsoft. Rzeczywista awaria/zawieszenia zrzuty nadal zostanie przekazany, jeśli raportowanie błędów systemu Windows jest włączona; tylko informacje statystyczne będą pomijane; <br>Umożliwia ujawnienie wzorców użycia anonimowego dla rozszerzenia Azure Tools SDK dla programu Visual Studio i wzorców użytkowania dla SQL narzędzi dla programu Visual Studio |
| Visual Studio <br> Obsługi klienta <br>Program poprawy jakości (obsługi klienta CEIP) <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | Protokół HTTPS| 443 | Używany do gromadzenia wzorców użycia anonimowego i dzienników błędów <br><br>Używane do śledzenia problemów blokowanie interfejsu użytkownika|
| Tworzenie i<br>Zarządzanie <br>Zasoby platformy Azure | management.azure.com <br>management.core.windows.net   | Protokół HTTPS | 443 | Używane do tworzenia witryn sieci Web Azure lub innych zasobów do obsługi publikowania aplikacji sieci web, usługi Azure Functions lub zadań Webjob |
| Zaktualizowano sieci web publikowanie narzędzi <br>Sprawdzanie i rozszerzenia <br>Zalecenia  | marketplace.visualstudio.com  <br> visualstudiogallery.msdn.microsoft.com  | Protokół HTTPS | 443 | Używany do sprawdzania dostępności aktualizacji publikowania narzędzi. Wyłączenie potencjalne zalecane rozszerzenia na potrzeby publikowania w sieci web mogą nie być wyświetlane |
| Zaktualizowano zasobów platformy Azure <br>Informacji o tworzeniu punktu końcowego  | *.blob.core.windows.net | Protokół HTTPS | 443 | Używane do aktualizowania punktów końcowych używanych w celu utworzenia zasobów Azure dla niektórych usług Azure. Wyłączenie ostatniego pobraniem lub utworzony w lokalizacji są używane zamiast punktów końcowych |
| Debugowanie zdalne i <br>Profilowanie zdalne z <br>Witryn sieci Web Azure | &#42;.cloudapp.net <br> &#42;.azurewebsites.net | | 4022 | Używany do dołączania zdalnego debugera do witryny sieci Web Azure. Wyłączenie dołączanie debugera zdalnego do witryn sieci Web Azure nie będzie działać |
| Usługi Active Directory <br>Wykres | graph.windows.net | Protokół HTTPS | 443 | Użyć do udostępnienia nowej aplikacji usługi Azure Active Directory. Również używane przez dostawcę podłączonej usługi Office 365 MSGraph- |
| Środowisko Azure Functions <br>Aktualizacja interfejsu wiersza polecenia <br>Sprawdź | functionscdn.azureedge.net | Protokół HTTPS | 443 | Używany do sprawdzania zaktualizowane wersje interfejsu wiersza polecenia Azure funkcji. Wyłączenie pamięci podręcznej kopię (lub kopiowania przez składnik usługi Azure Functions) z poziomu interfejsu wiersza polecenia w zamian zostanie użyta |
| Cordova | npmjs.org<br>gradle.org | protokołu HTTP/s | 80/443 | Protokół HTTP jest używany do pobierania narzędzia Gradle podczas kompilacji; HTTPS jest używana do włączenia wtyczek oprogramowania Cordova w projektach|
| Eksplorator chmury | 1. &#60;clusterendpoint&#62; <br>Service Fabric <br>2. &#60;punkt końcowy zarządzania&#62;<br>Exp chmury ogólne <br>3. &#60;punktu końcowego programu graph&#62;<br>Exp chmury ogólne<br>4. &#60;punkt końcowy konta magazynu&#62;<br>Węzłów magazynu <br>5. &#60;portalu azure adresy URL&#62;<br>Exp chmury ogólne <br>6. &#60;klucza magazynu punkty końcowe&#62; <br>Węzły maszyny Wirtualnej platformy Azure Resource Manager<br>7. &#60;PublicIPAddressOfCluster&#62;<br>Usługa sieci szkieletowej zdalnego debugowania i śledzenia zdarzeń systemu Windows |   <br>1. https<br>2. https<br>3. https<br>4. https<br>5. https<br>6. https<br>7: tcp| 1. 19080<br>2. 443 <br>3. 443 <br>4. 443 <br>5. 443 <br>6. 443 <br>7. dynamic   | 1. Example: test12.eastus.cloudapp.com<br>2. Pobiera subskrypcje i pobiera/zarządza zasobów platformy Azure<br>3. Pobiera subskrypcji Azure stosu<br>4. Zarządza zasobami magazynu (przykład: mystorageaccount.blob.core.windows.net)<br>5. "Otwórz w portalu" opcji menu kontekstowe (otwiera zasobu w portalu Azure)<br>6. Tworzy i używa magazynów kluczy do debugowania maszyny Wirtualnej (przykład: myvault.vault.azure.net) <br><br>7. Dynamicznie przydziela blok portów na podstawie liczby węzłów w klastrze i dostępnych portów. <br><br>Blok portu spróbuje pobrać trzy razy liczba węzłów z co najmniej 10 portów.<br><br>Dla ślady przesyłania strumieniowego można pobrać z bloku portu z 810 podejmowana jest próba. Tego bloku port jest już używane, następnie podejmowana jest próba pobrania kolejnego bloku i tak dalej. (Usługa równoważenia obciążenia jest pusta, najprawdopodobniej będą używane porty 810) <br><br>Podobnie do debugowania, cztery zestawy bloków porty są zarezerwowane: <br>-connectorPort: 30398, <br>-forwarderPort: 31398, <br>-forwarderPortx86: 31399,<br>-fileUploadPort: 32398<br>|
| Usługi w chmurze | 1. RDP<br><br>2. core.windows.net <br><br>3.  management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;user's cloud service&#62;.cloudapp.net <br> &#60;user's VM&#62;.&#60;region&#62;.azure.com | 1. Protokół rdp <br><br> 2. https <br><br> 3. https <br><br> 4. https <br><br> 5. https <br><br>6. tcp | 1. 3389 <br><br> 2. 443 <br><br> 3. 443 <br><br>4. 443 <br><br>5. 443 <br><br> 6.) 30398 <br> 6. b) 30400 <br> 6. c) 31398 <br> 6. d) 31400 <br> 6. e) 32398 <br> 6. f) 32400 | 1.  Pulpit zdalny z usługami maszyny Wirtualnej w chmurze <br><br> 2.  Składnik konto magazynu diagnostyki prywatnej konfiguracji <br><br> 3.  Azure portal <br><br> 4. Eksplorator serwera - Azure Storage &#42; klienta nosi nazwę konta magazynu  <br><br> 5.  Łącza do Otwórz portal &#47; pobranie certyfikatu subskrypcji &#47; plik ustawień publikowania <br><br>6.) portu lokalnego łącznika do zdalnego debugowania dla usługi w chmurze i maszyn wirtualnych<br> 6. b) port publiczny łącznika do zdalnego debugowania dla usługi w chmurze i maszyn wirtualnych <br> port lokalny 6. c) usługa przesyłania dalej dla zdalnego debugowania dla usługi w chmurze i maszyn wirtualnych <br> 6. d) port publiczny usługi przesyłania dalej dla zdalnego debugowania dla usługi w chmurze i maszyn wirtualnych  <br> 6. e) pliku przekazujący portu lokalnego do zdalnego debugowania dla usługi w chmurze i maszyn wirtualnych <br> 6. f) pliku port publiczny moduł przesyłający dla zdalnego debugowania dla usługi w chmurze i maszyn wirtualnych |
| Service Fabric | 1. <br>ocs.Microsoft.com<br>aka.MS <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42; .vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42; .visualstudio.com | Protokół HTTPS | 443 | 1. Dokumentacja <br><br> 2. Tworzenie funkcji klastra <br><br>3. &#42; To nazwa magazynu kluczy Azure (przykład:-test11220180112110108.vault.azure.net  <br><br>  4. &#42; Jest dynamiczny (przykład: vsspsextprodch1su1.vsspsext.visualstudio.com) |
| Migawka <br>Debugger | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;azurewebsites.net <br> 4. &#42;scm.azurewebsites.net<br>5. api.nuget.org/v3/index.json <br>6. polecenie msvsmon | 1. https <br>2. https  <br>3. http <br>4. https <br>5. https <br>6. Concord <br> | 1. 443<br> 2. 443<br>3. 80  <br>4. 443<br> 5. 443<br> 6. 4022 (zależnych wersji programu visual Studio) | 1. Zapytanie pliku JSON, rozmiar jednostki SKU usługi aplikacji <br>2. Różnych wywołań Menedżera zasobów Azure <br>3. Wywołanie rozgrzewania lokacji za pomocą  <br>4. Odbiorcy przez docelowe punktu końcowego Kudu usługi aplikacji <br>5. Opublikowana wersja lokacji rozszerzenia zapytania w usłudze nuget.org <br>6. Kanału zdalnego debugowania |
|Azure Stream Analytics <br><br>HDInsight | Management.azure.com |Protokół HTTPS|443 |Używany do wyświetlania, przesłać, uruchamiania i zarządzać zadaniami ASA <br><br> Używane do przeglądania HDI klastrów i przesłanie, diagnozowanie i debugowanie zadań HDI |
| Azure Data Lake | &#42;.azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | Protokół HTTPS | 443 | Używana do kompilowania, przesłać, wyświetlanie, diagnozowanie i debugowanie zadań; Umożliwia przeglądanie plików z ADLS; używany do przekazywania i pobierania plików |
|Tworzenie pakietów usługi | [account].visualstudio.com <br/> [account].*.visualstudio.com <br/> *.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | Protokół HTTPS | 443 | *. Npmjs.org, *. nuget.org, i *. nodejs.org są tylko wymagane dla kompilacji niektórych scenariuszy zadań (np. Instalator narzędzie NuGet, węzła narzędzie Instalatora) lub jeśli zamierzasz używać publicznego upstreams ze źródła danych.  Trzy domeny są wymagane dla functinality podstawowe usługi Packaigng. |
|||||||


## <a name="troubleshoot-network-related-errors"></a>Rozwiązywanie problemów związanych z siecią
Czasami może być uruchamiany w błędy związane z siecią lub serwera proxy podczas instalowania lub użyć programu Visual Studio za zaporą lub serwer proxy. Aby uzyskać więcej informacji o rozwiązaniach takie komunikaty o błędach, zobacz [rozwiązywania problemów związanych z siecią, podczas instalowania lub użyć programu Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md) strony.

## <a name="get-support"></a>Uzyskaj pomoc techniczną
Poniżej przedstawiono kilka więcej opcji pomocy technicznej dla Ciebie:
* Problemy z produktu może raportować do nas za pomocą [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia, która pojawia się zarówno w Instalatorze programu Visual Studio, jak i w środowisku IDE programu Visual Studio.
* Można udostępniać sugestię produktu z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi.
* Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio).  (Ta opcja wymaga [GitHub](https://github.com/) konta.)

## <a name="see-also"></a>Zobacz także
* [Rozwiązywania problemów dotyczących sieci w programie Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Zainstaluj program Visual Studio 2017 r.](install-visual-studio.md)
