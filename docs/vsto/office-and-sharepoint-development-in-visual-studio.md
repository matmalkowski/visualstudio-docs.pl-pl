---
title: Pakietu Office i programowanie SharePoint w Visual Studio | Dokumentacja firmy Microsoft
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
- Office applications [Office development in Visual Studio], about developing applications
- Office development in Visual Studio
- Office projects
- Visual Studio Tools for Office, see Office development in Visual Studio
- Office applications [Office development in Visual Studio]
- Office Business Applications
- applications [Office development in Visual Studio]
- programming [Office development in Visual Studio]
- VSTO, see Office development in Visual Studio
- Office, development with Visual Studio
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b0692b0320a8741351391f82b694089910bae4f8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="office-and-sharepoint-development-in-visual-studio"></a>Tworzenie aplikacji pakietu Office i programu SharePoint w programie Visual Studio
  Można rozszerzać przez tworzenie lekkie aplikacji Microsoft Office i programu SharePoint lub dodatek czy użytkownicy mogą pobierać z [sklep Office](https://store.office.com/) lub organizacji w katalogu lub tworząc przez użytkowników rozwiązanie oparte na programie .NET Framework należy zainstalować na komputer.  
  
 W tym temacie:  
  
-   [Tworzenie dodatków dla pakietu Office i programu SharePoint](#Apps)  
  
-   [Tworzenie dodatków narzędzi VSTO](#Add-ins)  
  
-   [Tworzenie rozwiązań programu SharePoint](#Solutions)  
  
##  <a name="Apps"></a>Tworzenie dodatków dla pakietu Office i programu SharePoint  
 Pakiet Office 2013 i programu SharePoint 2013 wprowadzenie nowego dodatku modelu, który ułatwia tworzenie, rozpowszechnianie i sprzedawać dodatków rozszerzających pakietu Office i programu SharePoint.  Tych dodatków można uruchomić w Office lub SharePoint Online, a użytkownicy mogą pracować z nimi z wielu urządzeń.  
  
 Dowiedz się, jak korzystać z nowych [modelu dodatku pakietu Office](https://msdn.microsoft.com/library/office/jj220082.aspx) rozszerzyć możliwości pakietu Office dla użytkowników.  
  
 Te dodatki mają udzielaniu bardzo małe w porównaniu do dodatków VSTO i rozwiązań i można ich tworzyć przy użyciu prawie każdego technologii, takich jak HTML5, CSS3, JavaScript i XML programowanie dla sieci web.  Aby rozpocząć pracę, użyj narzędzia Office Developer Tools w programie Visual Studio lub LDS opartych na sieci web narzędzie nazwę kodową Napa Office 365 programowanie narzędzia, która pozwala na tworzenie projektów, pisania kodu i uruchomić dodatki w przeglądarce sieci.  
  
 ![Aplikacje pakietu Office i programu SharePoint modelu koncepcyjnego](../vsto/media/officeandsharepointapps2015.png "aplikacji dla pakietu Office i programu SharePoint model koncepcyjny")  
  
 **Dowiedz się więcej**  
  
|Do|Zobacz|  
|--------|---------|  
|Dowiedz się więcej na temat narzędzia do programowania Napa Office 365.|[Narzędzia deweloperskie Napa usługi Office 365](https://msdn.microsoft.com/library/dn974046.aspx)|  
  
### <a name="build-an-office-add-in"></a>Tworzenie dodatku pakietu Office  
 Aby rozszerzyć funkcjonalność programu Office, kompilacji dodatku pakietu Office. Jest zasadniczo strony sieci Web, która jest obsługiwana w aplikacji pakietu Office, takich jak program Excel, Word, Outlook i PowerPoint. Aplikację można dodać funkcje do dokumenty, arkusze wiadomości e-mail, terminy, prezentacji i projektów.  
  
 Możesz sprzedać aplikacji w sklepie Office.  [Sklep Office](https://store.office.com/) ułatwia sprzedawać dodatki, zarządzanie aktualizacjami i śledzenia telemetrii. Można również opublikować aplikacji użytkownikom za pośrednictwem katalogu aplikacji w programie SharePoint lub na serwerze Exchange.  
  
 Następujące aplikacja dla pakietu Office zawiera dane arkusza w mapy Bing.  
  
 ![Aplikacja zawartości dla pakietu Office](../vsto/media/appforoffice.png "aplikacji zawartości dla pakietu Office")  
  
 **Dowiedz się więcej**  
  
|Do|Zobacz|  
|--------|---------|  
|Dowiedz się więcej na temat dodatków pakietu Office, a następnie utworzyć.|[Dodatków pakietu Office](http://msdn.microsoft.com/office/dn448457)|  
|Porównaj różne sposoby, w którym można rozszerzać pakietu Office i zdecyduj, czy należy użyć aplikacji lub dodatek pakietu Office.|[Plan dla dodatków pakietu Office, VSTO i VBA](http://blogs.msdn.com/b/officeapps/archive/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba.aspx)|  
|Dowiedz się więcej na temat narzędzia do programowania Napa Office 365.|[Narzędzia deweloperskie Napa usługi Office 365](https://msdn.microsoft.com/library/dn974046.aspx)|  
  
### <a name="build-a-sharepoint-add-in"></a>Tworzenie dodatku programu SharePoint  
 Aby rozszerzyć programu SharePoint dla użytkowników, tworzenia dodatku programu SharePoint. Zasadniczo jest mały, łatwy w użyciu, autonomicznej aplikacji, która rozwiązuje potrzeby użytkowników lub business.  
  
 Możesz sprzedać aplikacji programu SharePoint w [sklep Office](https://store.office.com/). Można również opublikować dodatek do użytkowników za pomocą wykazu Dodaj w programie SharePoint.  Właściciele witryn można zainstalować, uaktualnić i odinstalować dodatek w swoich witrynach programu SharePoint bez pomocy serwera farmy lub administratorem zbioru witryn.  
  
 Oto przykład aplikacji dla programu SharePoint, która umożliwia użytkownikom zarządzanie kontaktów biznesowych.  
  
 ![Aplikacja biznesowa kontaktów Menedżerze dla programu SharePoint](../vsto/media/appforsharepoint.png "firm kontaktów Menedżerze aplikacji dla programu SharePoint")  
  
 **Dowiedz się więcej**  
  
|Do|Zobacz|  
|--------|---------|  
|Dowiedz się więcej na temat dodatków programu SharePoint, a następnie utworzyć.|[Dodatki programu SharePoint](https://msdn.microsoft.com/library/office/fp179930.aspx)|  
|Porównaj dodatków dla programu SharePoint z tradycyjnych rozwiązań programu SharePoint.|[SharePoint dodatków w porównaniu z rozwiązaniami SharePoint](http://msdn.microsoft.com/library/office/jj163114.aspx)|  
|Określ, czy do tworzenia dodatku programu SharePoint lub rozwiązania programu SharePoint.|[Przy wyborze między dodatków programu SharePoint oraz rozwiązań programu SharePoint](https://msdn.microsoft.com/library/office/jj163114.aspx)|  
|Dowiedz się więcej na temat narzędzia do programowania Napa Office 365.|[Narzędzia deweloperskie Napa usługi Office 365](https://msdn.microsoft.com/library/dn974046.aspx)|  
  
##  <a name="Add-ins"></a>Tworzenie dodatków narzędzi VSTO  
 Utwórz dodatku narzędzi VSTO pod kątem pakietu Office 2007 lub Office 2010 lub przekracza możliwości programu Office dodatków pakietu Office 2013 i Office 2016. Dodatków VSTO uruchamiać tylko na komputerze. Użytkownicy muszą zainstalować dodatków VSTO, dzięki czemu są zwykle trudniejsze do wdrożenia i pomocy technicznej.  Jednak z dodatku VSTO można zintegrować dokładniejsze z pakietu Office. Na przykład go dodać kart i kontrolek do wstążki pakietu Office i wykonywanie zaawansowanych automatyzacji zadań, takich jak scalanie dokumentów lub modyfikowania wykresów. Można korzystać z programu .NET Framework i użyć C# i Visual Basic do interakcji z obiektów pakietu Office.  
  
 Oto przykład jakie dodatku narzędzi VSTO zrobić. Ten dodatek VSTO dodaje formantów wstążki, niestandardowego okienka zadań i okno dialogowe do programu PowerPoint.  
  
 ![PowerPoint dodatku rozwiązania](../vsto/media/powerpointaddin.png "rozwiązania dodatku programu PowerPoint")  
  
 **Dowiedz się więcej**  
  
|Do|Odczyt|  
|--------|----------|  
|Porównaj różne sposoby, w którym można rozszerzać pakietu Office i zdecyduj, czy należy użyć dodatku narzędzi VSTO lub dodatek pakietu Office.|[Plan dla dodatków pakietu Office, VSTO i VBA](http://blogs.msdn.com/b/officeapps/archive/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba.aspx)|  
|Tworzenie dodatku VSTO.|[Tworzenie dodatków narzędzi VSTO z programem Visual Studio](https://msdn.microsoft.com/library/jj620922.aspx)|  
  
##  <a name="Solutions"></a>Tworzenie rozwiązań programu SharePoint  
 Tworzenie rozwiązań programu SharePoint pod kątem programu SharePoint Foundation 2010 i SharePoint Server 2010 lub rozszerzyć programu SharePoint 2013 i programu SharePoint 2016 w sposób poza co to jest możliwe za pomocą dodatku programu SharePoint.  
  
 Rozwiązania programu SharePoint wymagają lokalnych serwerów farmy programu SharePoint. Administratorzy muszą zainstalować je, a ponieważ rozwiązań w programie SharePoint, mogą one wpłynąć na wydajność serwera. Jednak rozwiązań zapewnia lepszy dostęp do obiektów programu SharePoint. Ponadto podczas kompilowania rozwiązania programu SharePoint, można korzystać z programu .NET Framework i korzystać C# i Visual Basic do interakcji z obiektami programu SharePoint.  
  
 **Dowiedz się więcej**  
  
|Do|Zobacz|  
|--------|---------|  
|Porównanie rozwiązań programu SharePoint z dodatków programu SharePoint.|[SharePoint dodatków w porównaniu z rozwiązaniami SharePoint](http://msdn.microsoft.com/library/office/jj163114.aspx)|  
|Tworzenie rozwiązań programu SharePoint.|[Tworzenie rozwiązań SharePoint](../sharepoint/create-sharepoint-solutions.md)|  
  
  