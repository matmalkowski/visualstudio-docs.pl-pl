---
title: Omówienie wdrażania — Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: overview
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7346de998052ba68dfadf74a09fe0d4339be1614
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757165"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Omówienie wdrażania w programie Visual Studio

Wdrażanie aplikacji, usług i składników to rozpowszechnianie ich w celu instalacji na innych komputerach, urządzeniach, serwerach lub w chmurze. W programie Visual Studio możesz wybrać odpowiednią metodę w zależności od typu wdrożenia, jakiego potrzebujesz.

Dla wielu popularnych typów aplikacji można wdrożyć bezpośrednio z aplikacji w Eksploratorze rozwiązań w programie Visual Studio. Aby uzyskać szybki przegląd tej funkcji, zobacz [Pierwsze spojrzenie na wdrożenie](../deployment/deploying-applications-services-and-components.md).

![Wybierz jedną z opcji publikowania](../deployment/media/quickstart-publish-azure.png)

## <a name="what-publishing-options-are-right-for-me"></a>Jakie opcje publikowania jest dla mnie odpowiednia?

Z poziomu programu Visual Studio, aplikacje mogą być publikowane bezpośrednio do następujących celów:

- [Usługa aplikacji Azure](#azure-app-service)
- [Maszyny wirtualne platformy Azure](#azure-virtual-machines)
- [System plików](#file-system)
- [Niestandardowe elementy docelowe (usług IIS, FTP, itp.) ](#custom-targets), która obejmuje wszystkie serwery sieci web dowolnego.

Na **publikowania** kartę, wybierz istniejący profil publikowania, zaimportować istniejący lub Utwórz nową przy użyciu opcji opisanych w tym miejscu. Aby skorzystać z samouczka opcje publikowania w IDE dla różnych typów aplikacji, zobacz [Pierwsze spojrzenie na wdrożenie](../deployment/deploying-applications-services-and-components.md).

## <a name="azure-app-service"></a>Usługa aplikacji Azure

[Usługa aplikacji Azure](/azure/app-service/app-service-web-overview) ułatwia deweloperom szybkie tworzenie szerokiej gamy usług i aplikacji sieci web skalowalności bez obsługa infrastruktury.

Należy określić, ile obliczeniowych zasilania usługę aplikacji ma, wybierając [cen warstwy lub plan](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) zawierającego usługi aplikacji. Może mieć wiele sieci Web aplikacji (i inne typy aplikacji) udostępnić tę samą usługę aplikacji bez Zmiana warstwy cenowej. Na przykład może obsługiwać aplikacje sieci Web development, tymczasowych i produkcyjnych razem na tej samej usługi aplikacji.

Uruchamia usługę aplikacji hostowanych w chmurze maszyn wirtualnych na platformie Azure, ale te maszyny wirtualne są zarządzane dla Ciebie. Każdej aplikacji w usłudze App Service zostanie przypisany unikatowy \*. azurewebsites.net URL; wszystkie warstwy cenowe innych niż wolne umożliwia przypisywanie niestandardowych nazw domen do lokacji.

### <a name="when-to-choose-azure-app-service"></a>Kiedy należy wybrać usługi aplikacji Azure

- Chcesz wdrożyć aplikacji sieci web, który jest dostępny za pośrednictwem Internetu.
- Użytkownik chce automatycznie skalować bez konieczności ponownego wdrażania aplikacji sieci web w zależności od potrzeb.
- Nie chcesz zachować infrastruktury serwera (w tym aktualizacji oprogramowania).
- Wszystkie dostosowania poziomu komputera, na serwerach, które host aplikacji sieci web nie jest konieczne.

> Jeśli chcesz używać usługi Azure App Service w własnego centrum danych lub innych komputerów lokalnych, możesz to zrobić za pomocą [stosu Azure](https://azure.microsoft.com/overview/azure-stack/).

Aby uzyskać więcej informacji dotyczących publikowania w usłudze App Service, zobacz [Szybki Start - publikowania w usłudze Azure App Service](quickstart-deploy-to-azure.md).

## <a name="azure-virtual-machines"></a>Maszyny wirtualne platformy Azure

[Maszyny wirtualne platformy Azure (maszyny wirtualne)](https://azure.microsoft.com/documentation/services/virtual-machines/) umożliwiają tworzenie i zarządzanie nimi dowolną liczbę zasobów obliczeniowych w chmurze. Przejmując odpowiedzialność za wszystkich aktualizacji oprogramowania i na maszynach wirtualnych, możesz dostosować je jako wymaganą zgodnie z wymaganiami aplikacji. Dostęp do maszyn wirtualnych bezpośrednio za pośrednictwem pulpitu zdalnego, a każda z nich będzie odpowiadać za utrzymanie przypisanego adresu IP tak długo, jak potrzeby.

Skalowanie aplikacji, która jest obsługiwana na maszynach wirtualnych obejmuje kręci się dodatkowe maszyny wirtualne w zależności od potrzeb, a następnie wdrażania niezbędne oprogramowanie. Ten dodatkowy poziom kontroli umożliwia skalowanie inaczej w różnych regionach globalnego. Na przykład aplikacji obsługujących pracowników w różnych oddziałów regionalnych można skalować zgodnie z liczbą pracowników w regionach, potencjalnie zmniejszenie kosztów maszyn wirtualnych.

Aby uzyskać dodatkowe informacje, zapoznaj się [szczegółowe porównanie](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) między usłudze Azure App Service, maszynach wirtualnych platformy Azure i innymi usługami Azure, których można użyć jako cel wdrożenia przy użyciu opcji niestandardowych w programie Visual Studio.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Kiedy należy wybrać maszyny wirtualne aplikacji Azure

- Chcesz wdrożyć aplikacji sieci web, który jest dostępny za pośrednictwem Internetu, z pełną kontrolę nad okres istnienia przypisanych adresów IP.
- Należy Dostosowywanie na poziomie komputera na serwerach, które zawiera dodatkowe oprogramowanie, takie jak system specjalne bazy danych, określonej sieci konfiguracji, partycji i tak dalej.
- Chcesz przeprowadzać poziom kontroli nad skalowanie aplikacji sieci web.
- Należy bezpośredni dostęp do serwerów obsługujących aplikacji z innego powodu.

> Jeśli chcesz używać usługi Azure Virtual Machines w własnego centrum danych lub innych komputerów lokalnych, możesz to zrobić za pomocą [stosu Azure](https://azure.microsoft.com/overview/azure-stack/).

## <a name="file-system"></a>System plików

Wdrażanie w systemie plików oznacza, że po prostu skopiuj pliki aplikacji do konkretnego folderu na swoim komputerze. To jest najczęściej do celów testowych lub aby wdrożyć aplikację na potrzeby używania przez ograniczoną liczbę osób, jeśli na komputerze jest zainstalowany także serwer. Jeśli folder docelowy jest udostępniony w sieci, następnie wdrażania w systemie plików można udostępnić sieci web plików aplikacji do innych użytkowników, którzy mogą następnie wdrożyć je do określonych serwerów.

Wszystkie lokalne maszyny, które są uruchomione serwera można udostępnić aplikacji za pośrednictwem Internetu lub sieci Intranet w zależności od sposobu skonfigurowania i sieci, z którymi jest połączony. (W przypadku podłączenia komputera bezpośrednio do Internetu, można zachować szczególną ostrożność ochrony przed zagrożeniami bezpieczeństwa zewnętrznych.) Ponieważ zarządzanie tymi komputerami, możesz w pełną kontrolę nad konfiguracjach sprzętu i oprogramowania.

Należy pamiętać, że jeśli z jakiegokolwiek powodu (na przykład dostęp do komputera) nie jest możliwe do używania usługi w chmurze Azure App Service lub maszynach wirtualnych platformy Azure, można użyć [stosu Azure](https://azure.microsoft.com/overview/azure-stack/) we własnym centrum danych. Stos Azure umożliwia zarządzanie i użycie zasobów obliczeniowych, przy użyciu usługi Azure App Service i maszyny wirtualne Azure mając jeszcze wszystko lokalnymi.

### <a name="when-to-choose-file-system-deployment"></a>Kiedy należy wybrać wdrożenie systemu plików

- Tylko należy wdrożyć aplikację do udziału plików, z którego innym będzie wdrożyć go na różnych serwerach.
- Należy tylko wdrożenia lokalnego testu.
- Chcesz zbadać i potencjalnie niezależnie modyfikować pliki aplikacji przed ich wysłaniem do innego cel wdrożenia.

Aby uzyskać więcej informacji, zobacz [Szybki Start - wdrażanie na folder lokalny](quickstart-deploy-to-local-folder.md)

## <a name="custom-targets-iis-ftp"></a>Niestandardowe elementy docelowe (usług IIS, FTP)

Niestandardowe docelowej umożliwia wdrażanie aplikacji do elementu docelowego innego niż Azure App Service, maszynach wirtualnych platformy Azure lub lokalnego systemu plików. System plików lub dowolnego innego serwera (w Internecie lub intranecie) do których masz dostęp, łącznie z dotyczącymi innych usług w chmurze można wdrożyć. Może współpracować z sieci web wdrażanie (plików lub. ZIP) i FTP.

Podczas wybierania docelowego niestandardowych, Visual Studio monituje o nazwa profilu, a następnie zbieranie dodatkowych **połączenia** informacje w tym serwera docelowego lub lokalizacji, nazwa witryny i poświadczenia. Można kontrolować następujące zachowania na **ustawienia** karty:

- Konfigurację, którą chcesz wdrożyć.
- Czy chcesz usunąć istniejące pliki z serwerem docelowym.
- Określa, czy wstępna kompilacja podczas publikowania.
- Określa, czy wykluczyć pliki w folderze App_Data z wdrożenia.

Można utworzyć dowolną liczbę niestandardowych wdrażania profilów w programie Visual Studio, co umożliwia zarządzanie profilami z innymi ustawieniami.

### <a name="when-to-choose-custom-deployment"></a>Kiedy należy wybrać niestandardowe wdrożenie

- Usługi w chmurze jest używana dla dostawcy innego niż Azure, który jest możliwy za pośrednictwem adresów URL.
- Chcesz wdrożyć przy użyciu poświadczeń innych niż te, które można używać w programie Visual Studio lub te bezpośrednio powiązane konta platformy Azure.
- Chcesz usunąć pliki z docelowej każdym wdrożeniu.

Aby uzyskać więcej informacji, zobacz [Szybki Start - wdrażanie w witrynie sieci web](quickstart-deploy-to-a-web-site.md)

## <a name="next-steps"></a>Następne kroki

Samouczki:

- [Wdrażanie aplikacji .NET Core za pomocą narzędzia publikowania](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji platformy ASP.NET core na platformie Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Wdrażanie w Visual C++](/cpp/ide/deployment-in-visual-cpp)
- [Wdrażanie aplikacji platformy uniwersalnej systemu Windows](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji Node.js na platformie Azure przy użyciu narzędzia Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji Python usługi aplikacji Azure](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
