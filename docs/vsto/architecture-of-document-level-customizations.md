---
title: Architektura Dostosowywanie na poziomie dokumentu
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- formats [Office development in Visual Studio]
- file formats [Office development in Visual Studio]
- vstoee.dll
- managed code extensions [Office development in Visual Studio], definition
- document-level customizations [Office development in Visual Studio]
- AddInLoader.dll
- architecture [Office development in Visual Studio], document-level customizations
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 78a00b9d13d93f8ac0fa893e68ca379a7b5f7c3d
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="architecture-of-document-level-customizations"></a>Architektura Dostosowywanie na poziomie dokumentu
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] zawiera projekty do tworzenia dostosowań na poziomie dokumentu dla programu Microsoft Office Word i Microsoft Office Excel. W tym temacie opisano następujące aspekty dostosowań na poziome dokumentu:  
  
-   [Zrozumienie dostosowania](#UnderstandingCustomizations)  
  
-   [Składniki dostosowania](#Components)  
  
-   [Jak działają dostosowania z aplikacji Microsoft Office](#HowCustomizationsWork)  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Aby uzyskać ogólne informacje o tworzeniu dostosowań na poziome dokumentu, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md), [wprowadzenie do programowania dostosowań na poziome dokumentu dla programu Word](../vsto/getting-started-programming-document-level-customizations-for-word.md), i [wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md).  
  
##  <a name="UnderstandingCustomizations"></a> Zrozumienie dostosowania  
 Korzystając z narzędzia Office developer tools w programie Visual Studio do dostosowania na poziomie dokumentu kompilacji, możesz utworzyć zestawu zarządzanego kodu, który jest skojarzony z określonego dokumentu. Dokument lub skoroszyt z połączonego zestawu jest nazywany udało rozszerzenia kodu. Aby uzyskać więcej informacji, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).  
  
 Po otwarciu dokumentu zestaw jest ładowany przez aplikację Microsoft Office. Po zestaw jest ładowany, dostosowań można odpowiadanie na zdarzenia, gdy dokument jest otwarty. Dostosowanie także wywołać object model do automatyzacji i rozszerzenie aplikacji, podczas gdy dokument jest otwarty i może używać dowolnej klasy w [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
 Zestaw komunikuje się z aplikacji składników COM za pomocą podstawowego zestawu międzyoperacyjnego aplikacji. Aby uzyskać więcej informacji, zobacz [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md) i [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 Jeśli użytkownik otwiera wiele dostosowań na poziome dokumentu w tym samym czasie, każdy zestaw jest ładowany w domenie innej aplikacji. Oznacza to, że jedno rozwiązanie, która działa nieprawidłowo nie może spowodować niepowodzenie innych rozwiązaniach. Dostosowywanie na poziomie dokumentu zostały zaprojektowane do pracy z pojedynczego dokumentu w domenie pojedynczej aplikacji. Nie są one przeznaczone do komunikacji między dokumentu. Aby uzyskać więcej informacji o domenach aplikacji, zobacz [domen aplikacji](/dotnet/framework/app-domains/application-domains).  
  
> [!NOTE]  
>  Dostosowywanie na poziomie dokumentu, utworzonych przy użyciu programu Visual Studio Office developer tools są przeznaczone do użycia tylko wtedy, gdy aplikacja jest uruchomiona przez użytkownika końcowego. Jeśli aplikacja jest uruchomiona programowo, na przykład przy użyciu automatyzacji, dostosowań może nie działać zgodnie z oczekiwaniami.  
  
### <a name="design-time-and-run-time-experiences"></a>Podczas projektowania i środowiska wykonawczego  
 Zrozumienie architektury dostosowań na poziome dokumentu, ułatwia zrozumienie środowiska projektowania rozwiązania i systemem rozwiązania.  
  
#### <a name="design-time"></a>Czas projektowania  
 Środowisko czasu projektowania obejmuje następujące kroki:  
  
1.  Utworzenie przez dewelopera na poziomie dokumentu projekt w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Projekt zawiera dokument i zestawu, który jest uruchamiany za dokumentu. Dokument już istnieje (możliwe, że utworzony przez projektanta) lub wraz z projektu można utworzyć nowego dokumentu.  
  
2.  Projektant — albo projektanta, który tworzy projekt lub inna osoba — tworzy końcowego wyglądu i działania dokumentu dla użytkownika końcowego.  
  
#### <a name="runtime"></a>Środowisko uruchomieniowe  
 Środowisko wykonawcze obejmuje następujące kroki:  
  
1.  Użytkownik końcowy otworzy dokument lub skoroszytu, który zarządza rozszerzenia kodu.  
  
2.  Dokument lub skoroszyt ładuje skompilowanego zestawu.  
  
3.  Zestaw reaguje na zdarzenia, ponieważ użytkownik pracuje w dokumencie lub skoroszytu.  
  
#### <a name="developer-and-end-user-perspective-compared"></a>Perspektywy i deweloperów oraz użytkownika końcowego w porównaniu  
 Ponieważ dewelopera działa głównie w przypadku [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]oraz użytkownika końcowego programu Word czy Excel, istnieją dwa sposoby zrozumienia dostosowań na poziome dokumentu.  
  
|Perspektywa dewelopera|Perspektywy użytkownika końcowego|  
|-----------------------------|----------------------------|  
|Przy użyciu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], deweloper zajmują się pisaniem kodu, który jest dostępny dla programu Word i Excel.<br /><br /> Mimo że może wydawać się, że deweloper tworzy plik wykonywalny, który uruchamia Word czy Excel, proces odbywa się faktycznie odwrotnie. Ten dokument jest skojarzona z zestawem i zawiera wskaźnik do tego zestawu. Po otwarciu dokumentu, Word czy Excel lokalizuje zestaw i uruchamia kod w odpowiedzi na wszystkie zdarzenia obsłużone.|Osób, które używają rozwiązanie po prostu otworzyć dokument lub skoroszyt (lub Utwórz nowy dokument z szablonu) tylko będzie otwarciu dowolnego innego pliku Microsoft Office.<br /><br /> Zestaw zawiera dostosowania w dokumencie lub skoroszyt, takich jak automatyczne wypełnianie bieżącymi danymi lub przedstawiający okno dialogowe informacje.|  
  
### <a name="supported-document-formats-for-document-level-customizations"></a>Obsługiwane formaty dokumentu na poziomie dokumentu  
 Podczas tworzenia projektu dostosowania, można wybrać format dokumentu, który ma być używany w projekcie. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektach pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Poniższa tabela zawiera listę formatów dokumentu, z których można użyć w dostosowaniach na poziomie dokumentu dla programów Excel i Word.  
  
|Excel|Word|  
|-----------|----------|  
|Skoroszyt programu Excel (*xlsx*)<br /><br /> Skoroszyt programu Excel z włączoną obsługą makr (*xlsm*)<br /><br /> Binarny skoroszyt programu Excel (*xlsb*)<br /><br /> Skoroszyt programu Excel 97 – 2003 (*xls*)<br /><br /> Szablon programu Excel (*xltx*)<br /><br /> Szablon z obsługą makr programu Excel (*xltm*)<br /><br /> Szablon programu Excel 97 – 2003 (*xlt*)|Dokument programu Word (*.docx*)<br /><br /> Dokument programu Word z obsługą makr (*docm*)<br /><br /> Dokument programu Word 97-2003 (*doc*)<br /><br /> Szablon programu Word (*dotx*)<br /><br /> Szablon programu Word z obsługą makr (*dotm*)<br /><br /> Szablon programu Word 97-2003 (*dot*)|  
  
 Zalecane jest zaprojektowanie rozszerzenia kodu zarządzanego tylko dla dokumentów w obsługiwanych formatów. W przeciwnym razie określone zdarzenia nie może zostać wywołane, gdy dokument zostanie otwarty w aplikacji. Na przykład <xref:Microsoft.Office.Tools.Excel.Workbook.Open> zdarzenie nie jest wywoływane, gdy użytkownik korzysta z Skoroszyty zapisane w formacie arkusza kalkulacyjnego XML programu Excel lub na stronie sieci web rozszerzenia kodu zarządzanego (*.htm*; *.html*) format.  
  
### <a name="support-for-word-documents-that-have-xml-file-name-extensions"></a>Obsługa dokumentów programu Word, które mają rozszerzenia nazw plików XML  
 Szablony projektów na poziomie dokumentu nie pozwala na tworzenie projektów opartych na następujące formaty plików:  
  
-   Dokument XML programu Word (*\*xml*).  
  
-   Dokument XML programu Word 2003 (*\*xml*).  
  
 Aby użytkownicy końcowi użyj opcji dostosowania w tych formatach plików, tworzenie i wdrażanie dostosowania, które korzysta z jednego z obsługiwanych formatów plików określone w powyższej tabeli. Po zainstalowaniu dostosowań, użytkownicy końcowi mogą Zapisz dokument w dokumencie XML programu Word (*\*xml*) format lub dokument programu Word 2003 XML (*\*xml*) format, a Dostosowywanie będą w dalszym ciągu działać zgodnie z oczekiwaniami.  
  
##  <a name="Components"></a> Składniki dostosowania  
 Głównymi składnikami dostosowanie są dokumentu i zestawu. Oprócz tych składników istnieje kilka części, które odgrywa ważną rolę w sposób aplikacji Microsoft Office odnaleźć i załadować dostosowania.  
  
### <a name="deployment-manifest-and-application-manifest"></a>Manifest rozmieszczenia i manifest aplikacji  
 Dostosowania do identyfikowania i załadować najnowszej wersji zestawu dostosowania używają manifesty wdrożenia i manifestów aplikacji. Wdrożenie manifestu wskazuje bieżący manifest aplikacji. Aplikacja manifestu punktów do zestawu dostosowania i Określa wpis punktu klasy (lub klasy) można wykonać w zestawie. Aby uzyskać więcej informacji, zobacz [aplikacji i wdrażania manifesty w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
### <a name="visual-studio-tools-for-office-runtime"></a>Visual Studio Tools for Office Runtime  
 Aby uruchomić dostosowań na poziome dokumentu, które są tworzone za pomocą narzędzia Office developer tools w programie Visual Studio, użytkownik końcowy komputery muszą mieć [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zainstalowane. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Obejmuje niezarządzane składniki, które załadować zestawu dostosowania, a także zestaw zarządzanych zestawów. Te zarządzanych zestawów Podaj model obiektu, który używa Twój kod dostosowania do automatyzacji i rozszerzanie aplikacji hosta.  
  
 Aby uzyskać więcej informacji, zobacz [Visual Studio tools dla pakietu Office runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
##  <a name="HowCustomizationsWork"></a> Jak działają dostosowania z aplikacji Microsoft Office  
 Po otwarciu dokumentu, który jest częścią Dostosowywanie programu Microsoft Office, aplikacja używa manifest wdrażania połączonego z dokumentu do lokalizowania i ładowania najnowszej wersji zestawu dostosowania. Lokalizacja manifestu rozmieszczenia jest przechowywana w właściwości niestandardowego dokumentu o nazwie **AssemblyLocation**. Ciąg, który identyfikuje tej lokalizacji są wstawiane do właściwości podczas kompilowania rozwiązania.  
  
 Punkty manifestu wdrożenia do manifestu aplikacji, następnie wskazujący najbardziej bieżącego zestawu. Aby uzyskać więcej informacji, zobacz [aplikacji i wdrażania manifesty w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 Na poniższej ilustracji przedstawiono podstawowa Architektura dostosowywania na poziomie dokumentu.  
  
 ![Architektura dostosowywania pakietu office 2007](../vsto/media/office07-custom.png "Architektura dostosowywania pakietu Office 2007")  
  
> [!NOTE]  
>  W rozwiązaniach pakietu Office, które odnoszą się do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], rozwiązań wywołanie object model aplikacji hosta przez przy użyciu informacji o typie podstawowy zestaw międzyoperacyjny (PIA) osadzony w zestawie rozwiązania, zamiast wywoływać metodę do PIA bezpośrednio. Aby uzyskać więcej informacji, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="loading-process"></a>Proces ładowania  
 Po otwarciu dokumentu, który jest częścią rozwiązania Microsoft Office, wykonywane są następujące kroki.  
  
1.  Aplikacja Microsoft Office sprawdza właściwości niestandardowego dokumentu, aby sprawdzić, czy powiązany z dokumentem rozszerzenia kodu zarządzanego. Aby uzyskać więcej informacji, zobacz [Przegląd właściwości niestandardowego dokumentu](../vsto/custom-document-properties-overview.md).  
  
2.  W przypadku rozszerzenia kodu zarządzanego ładowania aplikacji *VSTOEE.dll*, których ładunki *VSTOLoader.dll*. Są to niezarządzanych bibliotek DLL, które są składnikami modułu ładującego dla Visual Studio 2010 Tools dla pakietu Office runtime. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools for Office runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
3.  *VSTOLoader.dll* ładuje [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] i uruchamia zarządzanych część [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
4.  Jeśli dokument zostanie otwarty z lokalizacji innych niż komputer lokalny, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] weryfikuje, czy lokalizacja dokumentu w **zaufanych lokalizacji** na liście **ustawienia Centrum zaufania** dla tej konkretnej aplikacji pakietu Office. Jeśli lokalizacja dokumentu nie jest w zaufanej lokalizacji, dostosowanie nie jest zaufany, a proces ładowania zatrzymuje się tutaj.  
  
5.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Instaluje rozwiązanie, jeśli go nie został jeszcze zainstalowany, pliki do pobrania najnowszych manifestów aplikacji i wdrażania i wykonuje szereg kontroli zabezpieczeń. Aby uzyskać więcej informacji, zobacz [rozwiązań Secure Office](../vsto/securing-office-solutions.md).  
  
6.  Jeśli dostosowań jest zaufany do uruchomienia, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] używa manifest wdrażania i manifest aplikacji do sprawdzania aktualizacji zestawu. Jeśli dostępna jest nowa wersja zestawu, środowisko uruchomieniowe pobiera nowej wersji zestawu do [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] pamięci podręcznej na komputerze klienckim. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).  
  
7.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Tworzy nową domenę aplikacji, w którym można załadować zestawu dostosowania.  
  
8.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Ładuje zestaw dostosowania do domeny aplikacji.  
  
9. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Wywołania **uruchamiania** obsługi zdarzeń w zestawie Twoje dostosowania. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md)  
  
## <a name="see-also"></a>Zobacz także  
 [Architektura rozwiązań pakietu Office w Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Visual Studio Tools for Office runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Przegląd właściwości niestandardowego dokumentu](../vsto/custom-document-properties-overview.md)   
 [Buforowane dane w dostosowaniach na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md)  
  
  