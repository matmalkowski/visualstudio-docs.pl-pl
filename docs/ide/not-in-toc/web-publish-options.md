---
title: Jakie opcje publikowania jest dla mnie odpowiednia?
ms.date: 03/09/2017
ms.reviewer: riande
ms.prod: visual-studio-dev15
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- ASP.NET, web applications, deployment, publishing
ms.assetid: 3A13F685-531C-457D-A98E-631888011E4B
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: acc136462f8905be924357399b644a05569258b1
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766184"
---
# Jakie opcje publikowania jest dla mnie odpowiednia?

Z poziomu programu Visual Studio, aplikacji sieci Web mogą być publikowane bezpośrednio do następujących celów:

- [Usługa aplikacji Azure](#azure-app-service)
- [Maszyny wirtualne platformy Azure](#azure-virtual-machines)
- [System plików](#file-system)
- [Niestandardowe elementy docelowe (usług IIS, FTP, itp.) ](#custom-targets), która obejmuje wszystkie serwery sieci web dowolnego.

Na **publikowania** kartę, wybierz istniejący profil publikowania, zaimportować istniejący lub Utwórz nową przy użyciu opcji opisanych w tym miejscu. Aby skorzystać z samouczka opcje publikowania w IDE dla różnych typów aplikacji, zobacz [Pierwsze spojrzenie na wdrożenie](../../deployment/deploying-applications-services-and-components.md).

## Aplikacje sieci Web usługi aplikacji Azure

[Azure App Service Web Apps](/azure/app-service/app-service-web-overview) (lub po prostu aplikacji sieci Web) ułatwia deweloperom szybkie tworzenie szerokiej gamy usług i aplikacji sieci web skalowalności bez obsługa infrastruktury.

Należy określić, ile obliczeniowych zasilania aplikacji sieci Web ma, wybierając [cen warstwy lub plan](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) zawierającego usługi aplikacji. Istnieje wiele aplikacji sieci Web (i inne typy aplikacji) udostępnić tę samą usługę aplikacji bez Zmiana warstwy cenowej. Na przykład może obsługiwać programowanie, tymczasowych i produkcyjnych aplikacji sieci Web razem na tej samej usługi aplikacji.

Uruchamia usługę aplikacji hostowanych w chmurze maszyn wirtualnych na platformie Azure, ale te maszyny wirtualne są zarządzane dla Ciebie. Każdej aplikacji sieci Web w usłudze App Service zostanie przypisany unikatowy \*. azurewebsites.net URL; wszystkie warstwy cenowe innych niż wolne umożliwia przypisywanie niestandardowych nazw domen do lokacji.

### Kiedy należy wybrać aplikacje sieci Web usługi aplikacji Azure

- Chcesz wdrożyć aplikacji sieci web, który jest dostępny za pośrednictwem Internetu.
- Użytkownik chce automatycznie skalować bez konieczności ponownego wdrażania aplikacji sieci web w zależności od potrzeb.
- Nie chcesz zachować infrastruktury serwera (w tym aktualizacji oprogramowania).
- Wszystkie dostosowania poziomu komputera, na serwerach, które host aplikacji sieci web nie jest konieczne.

> Jeśli chcesz używać usługi Azure App Service w własnego centrum danych lub innych komputerów lokalnych, możesz to zrobić za pomocą [stosu Azure](https://azure.microsoft.com/overview/azure-stack/).

Aby uzyskać więcej informacji na temat publikowania aplikacji platformy ASP.NET Core, zobacz [publikowania aplikacji sieci web platformy ASP.NET Core w usłudze Azure App Service przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## Maszyny wirtualne platformy Azure

[Maszyny wirtualne platformy Azure (maszyny wirtualne)](https://azure.microsoft.com/documentation/services/virtual-machines/) umożliwiają tworzenie i zarządzanie nimi dowolną liczbę zasobów obliczeniowych w chmurze. Przejmując odpowiedzialność za wszystkich aktualizacji oprogramowania i na maszynach wirtualnych, możesz dostosować je jako wymaganą zgodnie z wymaganiami aplikacji sieci web. Dostęp do maszyn wirtualnych bezpośrednio za pośrednictwem pulpitu zdalnego, a każda z nich będzie odpowiadać za utrzymanie przypisanego adresu IP tak długo, jak potrzeby.

Skalowanie aplikacji sieci web, w której znajduje się na maszynach wirtualnych obejmuje kręci się dodatkowe maszyny wirtualne w zależności od potrzeb, a następnie wdrażania niezbędne oprogramowanie. Ten dodatkowy poziom kontroli umożliwia skalowanie inaczej w różnych regionach globalnego. Na przykład aplikacji obsługujących pracowników w różnych oddziałów regionalnych można skalować zgodnie z liczbą pracowników w regionach, potencjalnie zmniejszenie kosztów maszyn wirtualnych.

Aby uzyskać dodatkowe informacje, zapoznaj się [szczegółowe porównanie](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) między usłudze Azure App Service, maszynach wirtualnych platformy Azure i innymi usługami Azure, których można użyć jako cel wdrożenia przy użyciu opcji niestandardowych w programie Visual Studio.

### Kiedy należy wybrać maszyny wirtualne aplikacji Azure

- Chcesz wdrożyć aplikacji sieci web, który jest dostępny za pośrednictwem Internetu, z pełną kontrolę nad okres istnienia przypisanych adresów IP.
- Należy Dostosowywanie na poziomie komputera na serwerach, które zawiera dodatkowe oprogramowanie, takie jak system specjalne bazy danych, określonej sieci konfiguracji, partycji i tak dalej.
- Chcesz przeprowadzać poziom kontroli nad skalowanie aplikacji sieci web.
- Należy bezpośredni dostęp do serwerów obsługujących aplikacji z innego powodu.

> Jeśli chcesz używać usługi Azure Virtual Machines w własnego centrum danych lub innych komputerów lokalnych, możesz to zrobić za pomocą [stosu Azure](https://azure.microsoft.com/overview/azure-stack/).


## System plików

Wdrażanie w systemie plików oznacza, że po prostu skopiuj pliki aplikacji sieci web do konkretnego folderu na swoim komputerze. To jest najczęściej do celów testowych lub aby wdrożyć aplikację na potrzeby używania przez ograniczoną liczbę osób, jeśli na komputerze jest zainstalowany także serwer sieci web. Jeśli folder docelowy jest udostępniony w sieci, następnie wdrażania w systemie plików można udostępnić sieci web plików aplikacji do innych użytkowników, którzy mogą następnie wdrożyć je do określonych serwerów.

Wszystkie lokalne maszyny, które są uruchomione serwera sieci web można udostępnić aplikacji za pośrednictwem Internetu lub sieci Intranet w zależności od sposobu skonfigurowania i sieci, z którymi jest połączony. (W przypadku podłączenia komputera bezpośrednio do Internetu, można zachować szczególną ostrożność ochrony przed zagrożeniami bezpieczeństwa zewnętrznych.) Ponieważ zarządzanie tymi komputerami, możesz w pełną kontrolę nad konfiguracjach sprzętu i oprogramowania.

Należy pamiętać, że jeśli z jakiegokolwiek powodu (na przykład dostęp do komputera) nie jest możliwe do używania usługi w chmurze Azure App Service lub maszynach wirtualnych platformy Azure, można użyć [stosu Azure](https://azure.microsoft.com/overview/azure-stack/) we własnym centrum danych. Stos Azure umożliwia zarządzanie i użycie zasobów obliczeniowych, przy użyciu usługi Azure App Service i maszyny wirtualne Azure mając jeszcze wszystko lokalnymi.

### Kiedy należy wybrać wdrożenie systemu plików

- Tylko należy wdrożyć aplikację do udziału plików, z którego innym będzie wdrożyć go na różnych serwerach.
- Należy tylko wdrożenia lokalnego testu.
- Chcesz zbadać i potencjalnie niezależnie modyfikować pliki aplikacji przed ich wysłaniem do innego cel wdrożenia.

Aby uzyskać więcej informacji na temat wdrażania aplikacji .NET Core, zobacz [wdrażanie .NET Core aplikacji za pomocą programu Visual Studio](/dotnet/core/deploying/deploy-with-vs).

## Niestandardowe elementy docelowe (usług IIS, FTP)

Niestandardowe docelowej umożliwia wdrażanie aplikacji sieci web do elementu docelowego innego niż Azure App Service, maszynach wirtualnych platformy Azure lub lokalnego systemu plików. System plików lub dowolnego innego serwera (w Internecie lub intranecie) do których masz dostęp, łącznie z dotyczącymi innych usług w chmurze można wdrożyć. Może współpracować z sieci web wdrażanie (plików lub. ZIP) i FTP.

Podczas wybierania docelowego niestandardowych, Visual Studio monituje o nazwa profilu, a następnie zbieranie dodatkowych **połączenia** informacje w tym serwera docelowego lub lokalizacji, nazwa witryny i poświadczenia. Można kontrolować następujące zachowania na **ustawienia** karty:

- Konfigurację, którą chcesz wdrożyć.
- Czy chcesz usunąć istniejące pliki z serwerem docelowym.
- Określa, czy wstępna kompilacja podczas publikowania.
- Określa, czy wykluczyć pliki w folderze App_Data z wdrożenia.

Można utworzyć dowolną liczbę niestandardowych wdrażania profilów w programie Visual Studio, co umożliwia zarządzanie profilami z innymi ustawieniami.

### Kiedy należy wybrać niestandardowe wdrożenie

- Usługi w chmurze jest używana dla dostawcy innego niż Azure, który jest możliwy za pośrednictwem adresów URL.
- Chcesz wdrożyć przy użyciu poświadczeń innych niż te, które można używać w programie Visual Studio lub te bezpośrednio powiązane konta platformy Azure.
- Chcesz usunąć pliki z docelowej każdym wdrożeniu.

Aby uzyskać więcej informacji dotyczących publikowania w usługach IIS, zobacz [IIS 8.0 przy użyciu programu ASP.NET 3.5 i ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)
