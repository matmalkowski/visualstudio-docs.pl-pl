---
title: Tworzenie definicji witryny dla SharePoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0e43cfa7c9fa78722639053c572280cbaad912bf
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325345"
---
# <a name="create-site-definitions-for-sharepoint"></a>Tworzenie definicji witryny dla SharePoint
  Projektu definicji witryny programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] umożliwia tworzenie *definicji witryny*, która stanowi podstawę dla nowej witryny programu SharePoint. Te definicje nie tylko określić wygląd i zachowanie witryny programu SharePoint, ale także jego zawartości domyślnej i funkcji. W definicji możesz umieścić listy wstępnie skonfigurowane, typów zawartości, odbiorcy zdarzeń, obrazy i inne elementy. SharePoint obejmuje niektóre definicje witryn, takie jak BLOG, na przykład. Podczas tworzenia witryny na podstawie definicji witryny BLOGU lokacji zawiera listy, części sieci Web i innych elementów, które wymaga lokacji obsługi blogów.  
  
 Aby uzyskać więcej informacji na temat definicje witryny, zobacz [szablony witryn i definicje](http://go.microsoft.com/fwlink/?LinkId=179134).  
  
## <a name="site-definition-projects"></a>Projekty definicji witryny
 Projekty definicji w lokacji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Podaj tylko podstawowe pliki, które wymaga witryny programu SharePoint; nie udostępniają one wszystkie funkcje domyślne. Należy dodać pliki i zawartość w celu zapewnienia funkcji, które mają. Można tworzyć ręcznie, witryny, tworzenie i dodawanie potrzebne pliki.  
  
## <a name="feature-stapling"></a>Obsługa zszywania funkcji
 Tworzenie definicji witryny w korzyścią [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] one automatycznie korzystać ze *zszywania funkcji*. Funkcja zszywanie dołącza funkcji do definicji witryny, zamiast osadzania ich jego funkcje w samej definicji witryny. W ten sposób pozwala dodać funkcję do żadnej lokacji utworzone za pomocą definicji witryny bez modyfikowania oryginalnej definicji witryny. Aby uzyskać więcej informacji, zobacz [zszywania funkcji](http://go.microsoft.com/fwlink/?LinkID=119283).  
  
## <a name="site-definition-project-components"></a>Składniki projektu definicji witryny
 Po utworzeniu rozwiązania definicji witryny następujące domyślne pliki są dodawane do jej **SiteDefinition** węzła.  
  
|Nazwa pliku|Opis|  
|---------------|-----------------|  
|*default.aspx*|Domyślną stronę główną ASPX dla nowej witryny programu SharePoint.|  
|*onet.XML*|Określa konfiguracji nowej lokacji, składniki szablonu definicji witryny i zachowanie domyślne. Te ustawienia mogą obejmować atrybuty takie jak typy zawartości, które są włączone, listę widoki, pliki szablonów dokumentów i składnikami Web Part dołączone do lokacji. Domyślnie `Modules` sekcja zawiera listę plików, które mają zostać dodane do witryny programu SharePoint i sposobu ich konfiguracji.|  
|*webtemp_\<SiteDefinitionName > .xml*|Określa konfiguracje definicji lokacji, które pojawia się w **Wybieranie szablonu** sekcji **nową witrynę programu SharePoint** strony.|  
  
 Domyślnie wszystkie definicje lokacji są przechowywane w  *\<dysk: > \Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* folderu. Każdej definicji lokacji ma własną podfolderu.  
  
## <a name="related-topics"></a>Tematy pokrewne
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przewodnik: Tworzenie podstawowego projektu definicji witryny](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Zawiera instrukcje dotyczące tworzenia podstawowego projektu definicji witryny w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Porady: Tworzenie definicji witryny niestandardowych i konfiguracji](http://go.microsoft.com/fwlink/?LinkId=183309)|Opisuje sposób tworzenia definicji niestandardowej witryny w programie SharePoint, kopiując istniejącej definicji witryny, a następnie modyfikując kopię.|  
|[*WebTemp.xml*](http://go.microsoft.com/fwlink/?LinkId=183310)|W tym artykule opisano dla oryginalnego pliku, który określa definicje lokacji dostępne w **Wybieranie szablonu** sekcji **nową witrynę programu SharePoint** strony.|  
|[Lokalizowanie rozwiązań SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Opisuje sposób przygotowania rozwiązań programu SharePoint do użytku globalnego.|  
|[Tworzenie składników web Part dla SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Opisuje sposób tworzenia części strony programu SharePoint, które użytkownicy mogą modyfikować.|  
|[Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Opisuje sposób tworzenia formantów wielokrotnych uruchamianych w stron aplikacji i składników Web Part.|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|Informacje dotyczące używania projektanta, który pojawia się po otwarciu strony sieci Web w projekcie.|  
|[Omówienie stron sieci Web programu ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178726)|Zawiera ogólne informacje o strukturze [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] strony sieci Web, w jaki strony są przetwarzane przez [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]i w jaki sposób [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] strony są wyświetlane znaczników, który jest zgodny ze standardami XHTML.|  
|[Składnia strony sieci Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178727)|W tym artykule opisano elementy znaczników, które składają się na stronie platformy ASP.NET.|  
|[Programowanie strony sieci Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178728)|Zawiera informacje o sposobie tworzenia obsługi zdarzeń w [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] stron oraz sposób pracy z skrypt po stronie klienta.|  
|[Programowanie w programie Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=178729)|Informacje dotyczące używania modelu obiektu zarządzanego, który znajduje się w [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie rozwiązań programu SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
 
