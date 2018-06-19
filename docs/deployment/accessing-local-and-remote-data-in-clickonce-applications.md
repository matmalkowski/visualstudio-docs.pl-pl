---
title: Uzyskiwanie dostępu do danych lokalnych i zdalnych w aplikacjach ClickOnce | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- data access, ClickOnce applications
ms.assetid: be5cbe12-6cb6-49c9-aa59-a1624e1eef3d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df2652a2da7abd0536c3e5cb60c7d36842b5430a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31562757"
---
# <a name="accessing-local-and-remote-data-in-clickonce-applications"></a>Uzyskiwanie dostępu do danych lokalnych i zdalnych w aplikacjach ClickOnce
Większość aplikacji używają lub wyprodukować danych. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zapewnia różne opcje do odczytywania i zapisywania danych, zarówno lokalnie, jak i zdalnie.  
  
## <a name="local-data"></a>Dane lokalne  
 Z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], można załadować i przechowywać dane lokalnie, używając jednej z następujących metod:  
  
-   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Katalog danych  
  
-   Izolowany magazyn  
  
-   Innych plików lokalnych  
  
### <a name="clickonce-data-directory"></a>Katalog danych ClickOnce  
 Każdy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji zainstalowanej na komputerze lokalnym jest katalogiem dane przechowywane w folderze dokumenty i ustawienia użytkownika. Każdy plik zawarte w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji i oznaczony jako plik "dane" jest kopiowany do tego katalogu, gdy aplikacja jest zainstalowana. Pliki danych mogą być dowolnego typu, najczęściej używane są text, XML i pliki bazy danych, takich jak pliki .mdb programu Microsoft Access.  
  
 Katalog danych jest przeznaczony dla danych zarządzanych aplikacji, co aplikacja jawnie przechowuje i przechowuje dane. Wszystkie statyczne nondependency pliki nie są oznaczone jako "dane" w manifeście aplikacji będzie zamiast tego znajdują się w katalogu aplikacji. Jest to katalog, gdzie znajdują się pliki wykonywalne (.exe) i zestawów aplikacji.  
  
> [!NOTE]
>  Gdy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja zostanie odinstalowana, jego katalogu danych zostaną również usunięte. Nigdy nie używaj katalogu danych do przechowywania danych zarządzanych użytkownika końcowego, takich jak dokumenty.  
  
#### <a name="marking-data-files-in-a-clickonce-distribution"></a>Oznaczenie danych plików w dystrybucji ClickOnce  
 Aby umieścić istniejący plik w katalogu danych, należy oznaczyć istniejący plik jako plik danych w sieci [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pliku manifestu aplikacji aplikacji. Aby uzyskać więcej informacji, zobacz [porady: uwzględnianie pliku danych w aplikacji ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
#### <a name="reading-from-and-writing-to-the-data-directory"></a>Odczytywanie z oraz zapisywanie do katalogu danych  
 Odczytu z katalogu danych wymaga, aby Twoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] żądań aplikacji uprawnienia do odczytu; podobnie zapisu do katalogu wymaga uprawnień do zapisu. Aplikacja automatycznie ma to uprawnienie, jeśli został on skonfigurowany do uruchamiania z pełnego zaufania. Aby uzyskać więcej informacji o uprawnieniach wzrasta aplikacji przy użyciu podniesienia uprawnień lub zaufanych wdrożenia aplikacji, zobacz [zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
>  Jeśli Twoja organizacja nie korzysta z zaufanych wdrożenia aplikacji i wyłączył podniesienia uprawnień, zostanie uprawnienia zakończy się niepowodzeniem.  
  
 Po aplikacji ma te uprawnienia, on uzyskać dostępu do katalogu danych przy użyciu wywołania metody na klas w ramach <xref:System.IO>. Ścieżka katalogu danych w formularzach systemu Windows można uzyskać [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji za pomocą <xref:System.Deployment.Application.ApplicationDeployment.DataDirectory%2A> właściwość zdefiniowaną w <xref:System.Deployment.Application.ApplicationDeployment.CurrentDeployment%2A> właściwość <xref:System.Deployment.Application.ApplicationDeployment>. Jest to najbardziej wygodne i zalecany sposób dostępu do danych. Poniższy przykład kodu pokazuje, jak to zrobić w plik tekstowy o nazwie CSV.txt, które zostały uwzględnione w danym wdrożeniu jako plik danych.  
  
 [!code-csharp[ClickOnce.OpenDataFile#1](../deployment/codesnippet/CSharp/accessing-local-and-remote-data-in-clickonce-applications_1.cs)]
 [!code-vb[ClickOnce.OpenDataFile#1](../deployment/codesnippet/VisualBasic/accessing-local-and-remote-data-in-clickonce-applications_1.vb)]  
  
 Aby uzyskać więcej informacji na oznaczenie plików w danym wdrożeniu jako pliki danych, zobacz [porady: uwzględnianie pliku danych w aplikacji ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
 Możesz również uzyskać ścieżki katalogu danych przy użyciu odpowiednich zmienne na <xref:System.Windows.Forms.Application> klas, takich jak <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A>.  
  
 Manipulowanie innych typów plików może wymagać dodatkowych uprawnień. Na przykład, jeśli chcesz użyć pliku bazy danych (.mdb) dostęp do aplikacji musi assert pełne zaufanie Aby użyć odpowiedniego <xref:System.Data> klasy.  
  
#### <a name="data-directory-and-application-versions"></a>Katalog danych i wersji aplikacji  
 Każda wersja programu aplikacji ma własny katalog danych, która jest odizolowana od innych wersji. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tworzy ten katalog, niezależnie od tego, czy wszystkie pliki danych są uwzględnione we wdrożeniu, aby aplikacja ma lokalizacji do tworzenia nowych plików danych w czasie wykonywania. Po zainstalowaniu nowej wersji aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] skopiuje wszystkie istniejące pliki danych z poprzedniej wersji danych katalogu w katalogu danych nowej wersji — określa, czy zostały uwzględnione w oryginalnej wdrożenia lub utworzone przez aplikacja.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] spowoduje zastąpienie starszych wersji pliku z nowszej wersji serwera, jeśli plik danych ma wartość inną skrótu w starej wersji aplikacji w nowej wersji. Ponadto jeśli starszą wersję aplikacji utworzony nowy plik, który ma taką samą nazwę jako plik uwzględnione we wdrożeniu nowej wersji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] spowoduje zastąpienie pliku starą wersję nowy plik. W obu przypadkach stare pliki mają być uwzględnieni w podkatalogu w katalogu danych o nazwie `.pre`, dzięki czemu aplikacja nadal może uzyskać dostępu do starych danych dla celów migracji.  
  
 Jeśli potrzebujesz bardziej precyzyjną dopasowanymi migracji danych, możesz użyć [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrażania interfejsu API, aby przeprowadzić migrację niestandardowych z katalogu danych starego do nowego katalogu danych. Konieczne będzie test do pobrania dostępnych przy użyciu <xref:System.Deployment.Application.ApplicationDeployment.IsFirstRun%2A>, pobrać za pomocą aktualizacji <xref:System.Deployment.Application.ApplicationDeployment.Update%2A> lub <xref:System.Deployment.Application.ApplicationDeployment.UpdateAsync%2A>, i wykonaj niestandardowe migracji danych działają w własne po aktualizacji zostało zakończone.  
  
### <a name="isolated-storage"></a>Izolowany magazyn  
 Izolowany magazyn udostępnia interfejs API do tworzenia i uzyskiwania dostępu do plików przy użyciu prostego interfejsu API. Rzeczywistej lokalizacji przechowywanych plików jest ukryta zarówno dewelopera, jak i użytkownika.  
  
 Izolowany magazyn działa we wszystkich wersjach [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Izolowany magazyn działa również w częściowo zaufane aplikacje bez potrzeby przyznaje dodatkowych uprawnień. Jeśli aplikacja muszą działać w częściowej relacji zaufania, ale musi przechowywać dane specyficzne dla aplikacji należy używać izolowanego magazynu.  
  
 Aby uzyskać więcej informacji, zobacz [izolowanych magazynów](/dotnet/standard/io/isolated-storage).  
  
### <a name="other-local-files"></a>Innych plików lokalnych  
 Jeśli aplikacja musi działać z lub zapisać dane użytkownika końcowego, takie jak raporty, obrazy, muzyka i tak dalej, aplikacja będzie wymagać <xref:System.Security.Permissions.FileIOPermission> do odczytywania i zapisywania danych do lokalnego systemu plików.  
  
## <a name="remote-data"></a>Dane zdalne  
 W pewnym momencie aplikacji prawdopodobnie trzeba pobrać informacje ze zdalnej witryny sieci Web, takich jak informacje o danych lub rynku klienta. W tej sekcji omówiono najbardziej typowe techniki pobierania zdalnych danych.  
  
### <a name="accessing-files-by-using-http"></a>Uzyskiwanie dostępu do plików przy użyciu protokołu HTTP  
 Dostępne dane z serwera sieci Web przy użyciu <xref:System.Net.WebClient> lub <xref:System.Net.HttpWebRequest> klasy w <xref:System.Net> przestrzeni nazw. Dane mogą być albo plików statycznych lub [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacje, które zwracają tekst raw lub danych XML. Jeśli dane są w formacie XML, najszybszym sposobem na pobranie danych polega na użyciu <xref:System.Xml.XmlDocument> klasy, których <xref:System.Xml.XmlDocument.Load%2A> metoda pobiera adres URL jako argument. Na przykład zobacz [odczytywanie dokumentu XML do modelu DOM](/dotnet/standard/data/xml/reading-an-xml-document-into-the-dom).  
  
 Należy wziąć pod uwagę zabezpieczeń, gdy aplikacja uzyskuje dostęp do danych zdalnych za pośrednictwem protokołu HTTP. Domyślnie Twoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji dostęp do zasobów sieciowych może być ograniczona, w zależności od tego, jak aplikacja została wdrożona. Te ograniczenia są stosowane w celu zapobiegania złośliwych programów, uzyskiwanie dostępu do uprzywilejowanych danych zdalnych lub przy użyciu użytkownika komputera na ataki z innych komputerów w sieci.  
  
 W poniższej tabeli wymieniono strategii wdrażania, których może używać i ich domyślnych uprawnień sieci Web.  
  
|Typ wdrożenia|Domyślne uprawnienia sieciowe|  
|---------------------|---------------------------------|  
|Zainstaluj w sieci Web|Tylko dostęp do serwera sieci Web, w którym aplikacja została zainstalowana|  
|Instalowanie udziału plików|Nie można uzyskać dostępu do żadnych serwerów sieci Web|  
|Zainstaluj CD-ROM|Można uzyskać dostępu do żadnych serwerów sieci Web|  
  
 Jeśli Twoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji nie może uzyskać dostęp do serwera sieci Web z powodu ograniczeń zabezpieczeń, aplikacja musi assert <xref:System.Net.WebPermission> dla tej witryny sieci Web. Aby uzyskać więcej informacji o zwiększenie uprawnień zabezpieczeń dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, zobacz [zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md).  
  
### <a name="accessing-data-through-an-xml-web-service"></a>Uzyskiwanie dostępu do danych za pośrednictwem usługi sieci Web XML  
 Jeśli udostępnianie danych jako usługi XML sieci Web, ma dostęp do danych za pomocą serwera proxy usługi XML sieci Web. Serwer proxy jest [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] utworzyć za pomocą klasy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Operacje usługi XML sieci Web, takich jak pobieranie klientów, zamówienia wprowadzanie i tak dalej — są widoczne jako metody na serwerze proxy. Dzięki temu można łatwiej niż raw tekstu lub plików XML korzystanie z usług sieci Web.  
  
 Jeśli usługi XML sieci Web działa za pośrednictwem protokołu HTTP, usługa zostanie powiązany przez te same ograniczenia zabezpieczeń jako <xref:System.Net.WebClient> i <xref:System.Net.HttpWebRequest> klasy.  
  
### <a name="accessing-a-database-directly"></a>Bezpośrednie uzyskiwanie dostępu do bazy danych  
 Korzystając z klas w ramach <xref:System.Data> przestrzeni nazw do nawiązywania bezpośredniego połączenia z serwerem bazy danych, takich jak SQL Server w sieci, ale muszą uwzględniać problemy z zabezpieczeniami. W przeciwieństwie do żądań HTTP żądania połączenia bazy danych są zawsze dostęp zabroniony domyślnie w częściowej relacji zaufania; będziesz korzystać tylko z takich uprawnień domyślnie po zainstalowaniu programu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji z dysku CD. Dzięki temu pełne zaufanie Twojej aplikacji. Aby włączyć dostęp do określonej bazy danych programu SQL Server, należy zażądać aplikacji <xref:System.Data.SqlClient.SqlClientPermission> do niego; Aby włączyć dostęp do bazy danych innych niż SQL Server, należy zażądać <xref:System.Data.OleDb.OleDbPermission>.  
  
 W większości przypadków, użytkownik nie ma dostępu do bazy danych bezpośrednio, ale zostanie do niego dostęp zamiast za pośrednictwem aplikacji serwera sieci Web napisany w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] lub usługi XML sieci Web. Uzyskiwanie dostępu do bazy danych w ten sposób jest często najlepszą metodę Jeśli Twoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja jest wdrażana z serwera sieci Web. Można uzyskiwać dostęp do serwera w częściowej relacji zaufania bez podnoszenia uprawnień aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: uwzględnianie pliku danych w aplikacji ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)