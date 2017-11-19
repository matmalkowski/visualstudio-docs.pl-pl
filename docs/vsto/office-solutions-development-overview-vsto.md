---
title: "Rozwiązań Office Development ― omówienie (środowisko VSTO) | Dokumentacja firmy Microsoft"
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
- primary interop assemblies, Office
- Office development in Visual Studio, about developing solutions
ms.assetid: 5dfc519f-a851-4661-8d2b-47e0d221e10e
caps.latest.revision: "69"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1c35be3e79aea37b82e9ae46463582a0874e51a4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="office-solutions-development-overview-vsto"></a>Rozwój rozwiązań Office ― omówienie (środowisko VSTO)
  Przy użyciu programu Microsoft Office jako fronton dla rozwiązania, możesz można korzystać z znanych narzędzi, takich jak funkcje edytora tekstów, Word, funkcji analizy programu Excel i funkcje zarządzania pocztą e-mail programu Outlook i Microsoft Office interfejsy użytkownika . Można tworzyć rozwiązania programu Visual Studio, aby dostosować aplikacje pakietu Office i dodać konkretne funkcje niezbędne do procesów biznesowych. Na przykład można przekształcić Word generator kontraktu, który składana kontrakty się już istniejących części, których może być utworzona, można edytować lub nie można edytować. Przy użyciu programu Excel można utworzyć arkusz automatycznych budżetu dostosowanych do różnych projektów. Użytkownicy mogą również czerpać rozwiązań pakietu office w trybie offline, dzięki czemu częściej niż użycie architektury usługi sieci web złożonych rozwiązań.  
  
 Ten temat zawiera omówienie typów rozwiązań pakietu Office, które możesz utworzyć za pomocą programu Visual Studio Tools dla pakietu Office (środowisko VSTO) szablonów dostępnych Office developer Tools w programie Visual Studio. Aby uzyskać ogólne informacje o tym, jak tworzyć aplikacje za pomocą pakietu Office, zobacz [Office Developer Center](https://dev.office.com/).  
  
## <a name="choosing-an-office-project-type"></a>Wybieranie typu projektu pakietu Office  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Programowanie Office na podstawie VSTO zawiera następujące typy szablonów projektu:  
  
-   **Dostosowywanie na poziomie dokumentu** są skojarzone z określonego dokumentu.  
  
-   **Dodatków VSTO** są skojarzone z samej aplikacji.  
  
 Aby zdecydować, które z tych typów projektów jest najlepsze dla rozwiązania, pomyśl o czy ma swój kod, aby uruchomić tylko wtedy, gdy określony dokument jest otwarty, lub czy kod, który ma być dostępny zawsze, gdy aplikacja jest uruchomiona. Aby uzyskać więcej informacji na temat szablonów projektu, zobacz [Omówienie szablonów programu Office Project](../vsto/office-project-templates-overview.md).  
  
 Zależą od typów projektów, które można utworzyć, na których aplikacje pakietu Office został zainstalowany na komputerze dewelopera. Aby uzyskać więcej informacji, zobacz [dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).  
  
### <a name="document-level-customizations"></a>Dostosowania na poziomie dokumentów  
 Dostosowywanie na poziomie dokumentu składają się z zestawu, który jest skojarzony z pojedynczego dokumentu, skoroszytu lub szablonu w programie Microsoft Office Word i Microsoft Office Excel. Zestaw został załadowany po otwarciu skojarzonego dokumentu. Funkcje utworzone dostosowania są dostępne tylko wtedy, gdy jest otwarty skojarzonego dokumentu. Dostosowania nie można wprowadzić zmian na poziomie aplikacji, takich jak wyświetlanie nową kartę element lub wstążki menu po otwarciu dokumentu.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]oferuje narzędzia ułatwiające tworzenie dostosowań na poziome dokumentu. Dokument, który można dostosować, jest hostowany jako powierzchnię projektu w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], co umożliwia projektowanie dokumentu przez przeciąganie i upuszczanie formantów na niego. Wiele innych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] funkcje są dostępne w projektach na poziomie dokumentu, takich jak formantów formularzy systemu Windows, powiązanie przeciągania i upuszczania danych i zintegrowane debugera.  
  
 Aby uzyskać więcej informacji o dostosowywaniu zobacz następujące tematy:  
  
-   [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)  
  
-   [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)  
  
-   [Architektura Dostosowywanie na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)  
  
### <a name="vsto-add-ins"></a>Dodatków VSTO  
 Dodatków VSTO składają się z zestawu, który jest skojarzony z aplikacją Microsoft Office. Zazwyczaj dodatku VSTO uruchamiane po skojarzona aplikacja jest uruchomiona, mimo że użytkownicy mogą również ładować dodatków VSTO po aplikacja jest już uruchomiona. Funkcje dodatków VSTO, tworzone są dostępne dla aplikacji, niezależnie od tego, które są otwarte dokumenty.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]obejmuje narzędzia umożliwiające tworzenie dodatków narzędzi VSTO. Dodatek projekty obejmują automatycznie wygenerowane klasy, która reprezentuje dodatku VSTO. Ta klasa udostępnia właściwości i zdarzenia, których można uzyskiwać dostęp do modelu obiektów w aplikacji hosta i uruchomienia kodu po dodatku VSTO jest załadowany i zamknąć. Wiele innych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] funkcje są dostępne w dodatku VSTO projektach, takich jak formularzy systemu Windows i zintegrowane debugera.  
  
 Aby uzyskać więcej informacji na temat dodatków VSTO zobacz następujące tematy:  
  
-   [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
-   [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)  
  
## <a name="automating-office-applications-by-using-primary-interop-assemblies"></a>Automatyzowanie aplikacji pakietu Office przy użyciu podstawowe zestawy międzyoperacyjne  
 Można programowo włączenie funkcji aplikacji pakietu Office do rozwiązania, przez pisania kodu, który uzyskuje dostęp do modelu obiektu aplikacji. Modele obiektów są układ klasy, które udostępniają funkcje za pośrednictwem różnych właściwości i metod. Model obiektów dla każdej aplikacji pakietu Office różni się.  
  
 Aby użyć modelu obiektów z rozwiązania utworzone przy użyciu narzędzia Office development w aplikacji pakietu Office [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], należy użyć podstawowy zestaw międzyoperacyjny (PIA) dla aplikacji. PIA umożliwia kodu zarządzanego w rozwiązaniu do interakcji z aplikacji pakietu Office oparte na modelu COM obiektu modelu.  
  
 Musi mieć PIAs Office zainstalowanych i zarejestrowanych w globalnej pamięci podręcznej zestawów na komputerze deweloperskim do wykonywania większości zadań programowania. Aby uzyskać więcej informacji, zobacz [Konfigurowanie komputera na potrzeby programowania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md). PIAs pakietu Office nie są wymagane na komputerach użytkowników końcowych do uruchamiania rozwiązań pakietu Office VSTO. Aby uzyskać więcej informacji, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).  
  
 Aby uzyskać więcej informacji na temat używania PIAs w rozwiązaniach pakietu Office VSTO zobacz następujące tematy:  
  
-   [Pisanie kodu dla rozwiązań pakietu Office](../vsto/writing-code-in-office-solutions.md)  
  
-   [Podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md)  
  
## <a name="running-microsoft-vsto-office-solutions-on-end-user-computers"></a>Uruchamianie rozwiązań pakietu Office VSTO firmy Microsoft na komputerach użytkowników końcowych  
 Podczas tworzenia rozwiązań VSTO Office należy wziąć pod uwagę jak wymagań związanych z wdrażaniem mogą wpłynąć na programowanie wybranych opcji.  
  
### <a name="deployment-options"></a>Opcje wdrażania  
 Użyj ClickOnce lub Instalatora systemu Windows do wdrożenia rozwiązania, które są tworzone przy użyciu narzędzia Office development w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Wdrożenie ClickOnce umożliwia utworzenie samoaktualizacji rozwiązania, które można instalować i uruchamiać z minimalnym interakcji. Pliki Instalatora Windows (msi) mogą być łatwo dystrybuowane do komputerów użytkownika końcowego lub dystrybuowane za pomocą Systems Management Server (SMS). Aby uzyskać więcej informacji na temat wdrażania rozwiązań pakietu Office VSTO, zobacz [wdrażania rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
### <a name="installing-prerequisites"></a>Instalowanie wymagań wstępnych  
 Zanim użytkownicy końcowi uruchomione rozwiązanie tworzenia za pomocą narzędzia Office development w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ich komputery muszą mieć określone wymagania wstępne zainstalowane. Rozwiązanie w przypadku wdrożenia przy użyciu technologii ClickOnce lub tworząc plik Instalatora Windows, można zainstalować te wymagania wstępne, wraz z rozwiązaniem. Aby uzyskać więcej informacji, zobacz [Office rozwiązania z wymagań wstępnych dotyczących wdrażania](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e) i [porady: Instalowanie wymagań wstępnych na komputerach użytkowników końcowych do uruchamiania rozwiązań pakietu Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
### <a name="security"></a>Zabezpieczenia  
 Zabezpieczenia dla rozwiązań pakietu Office VSTO jest wymuszana przez szereg sprawdza, czy [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sprawia, że podczas instalacji i ładuje rozwiązania. Kontrole te obejmują sprawdzania, czy lokalizacja manifestu rozmieszczenia jest zaufany lub określa, czy certyfikat używany do podpisywania manifest rozmieszczenia jest zaufany. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie &#40; programowanie Office w Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Architektura Dostosowywanie na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)   
 [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)   
 [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  