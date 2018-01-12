---
title: "Przegląd szablonów projektu pakietu Office | Dokumentacja firmy Microsoft"
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
- templates [Office development in Visual Studio], about project templates
- Excel Workbook project template
- Word Template project template
- Excel [Office development in Visual Studio], project templates
- Project [Office development in Visual Studio], project templates
- project templates [Office development in Visual Studio]
- project templates, Word
- InfoPath [Office development in Visual Studio], project templates
- Excel Template project template
- project templates, 2007 Microsoft Office system
- project templates, Excel
- PowerPoint [Office development in Visual Studio], project templates
- Word [Office development in Visual Studio], Word project templates
- Office projects [Office development in Visual Studio], templates
- Excel projects in Visual Studio
- Word Document project template
- Visio [Office development in Visual Studio], project templates
- Word projects in Visual Studio
- Outlook [Office development in Visual Studio], project templates
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 634ebd13d214f2d354e150b47f9dd50757bd2817
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="office-project-templates-overview"></a>Szablony projektów pakietu Office ― Omówienie
  Microsoft Office developer tools w programie Visual Studio obejmują szablony projektów do tworzenia następujących typów rozwiązań pakietu Office:  
  
-   [Dostosowywanie na poziomie dokumentu](#DocLevel)  
  
-   [Dodatków VSTO](#AppLevel)  
  
 Aby uzyskać szczegółowe porównanie tych typów rozwiązań pakietu Office, zobacz [rozwój rozwiązań Office ― omówienie &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 Szablony projektów pakietu Office są dostępne w **nowy projekt** okna dialogowego, w obszarze **Office** węzła **Visual C#** i **Visual Basic**języka węzłów. Każdy szablon generuje projekt o konfiguracji odpowiedniej dla aplikacji docelowej, razem z odwołaniami do zestawów i ustawieniami debugowania.  
  
 Każdy projekt zawiera pliki i kod źródłowy niezbędne do rozpoczęcia tworzenia określonego typu rozwiązania. Kod generowany dla każdego projektu obejmuje programy obsługi zdarzeń uruchamiania i zamykania. Do programów obsługi można dodać kod, który będzie inicjował rozwiązanie podczas jego ładowania, a czyścił je podczas usuwania z pamięci. Aby uzyskać więcej informacji, zobacz [projekty pakietu Office w Visual Studio środowiska](../vsto/office-projects-in-the-visual-studio-environment.md) i [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).  
  
> [!NOTE]  
>  Narzędzia programistyczne pakietu Office są dołączane do niektórych wydań programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Konfigurowanie komputera na potrzeby programowania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
##  <a name="DocLevel"></a>Dostosowywanie na poziomie dokumentu  
 **Office** w węźle **nowy projekt** okno dialogowe zawiera następujące szablony projektów ułatwiające rozpoczęcie pracy dostosowań na poziomie dokumentu dla programu Word i Excel:  
  
-   **Dokument 2016 VSTO i programu Word 2013**  
  
-   **Word 2013 i 2016 szablon VSTO**  
  
-   **Program Excel 2013 i 2016 skoroszyt VSTO**  
  
-   **Program Excel 2013 i 2016 szablon VSTO**  
  
-   **Dokument VSTO programu Word 2010**  
  
-   **Szablon VSTO programu Word 2010**  
  
-   **Skoroszyt VSTO programu Excel 2010**  
  
-   **Szablon VSTO programu Excel 2010**  
  
 Szablony projektów dokumentów programu Word i skoroszytów programu Excel zawierają kod źródłowy, który pomoże rozpocząć tworzenie rozwiązania opartego na konkretnym dokumencie lub skoroszycie. W tego typu rozwiązaniach kod działa tylko wtedy, gdy powiązany dokument zostanie otwarty w programie Word lub Excel.  
  
 Szablony projektów programów Word i Excel zachowują się identycznie jak szablony projektów dokumentów programu Word i skoroszytów programów Excel. Jednak szablony projektów programów Word i Excel bardzo ułatwiają użytkownikom tworzenie nowych spersonalizowanych lokalnych kopii dokumentów lub skoroszytów w rozwiązaniu. Funkcje w rozwiązaniu są dostępne z nowego dokumentu, który użytkownik utworzył na podstawie szablonu.  
  
> [!NOTE]  
>  Szablony, które odwołują się do rozszerzenia kodu zarządzanego nie można użyć jako globalny dodatków VSTO. Wywołanie zestawu nie następuje, jeśli szablon jest ładowany z katalogu Startup programu Word. Aby uzyskać więcej informacji, zobacz [ograniczenia Szablony globalne i dodatki programu Excel (xla plików)](#Limitations)  
  
 Informacje na temat rozpoczynania pracy z tego typu projektami znajdują się w następujących tematach:  
  
-   [Programowanie dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)  
  
-   [Rozwiązania programu Word](../vsto/word-solutions.md)  
  
-   [Rozwiązania programu Excel](../vsto/excel-solutions.md)  
  
-   [Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
-   [Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)  
  
##  <a name="AppLevel"></a>Dodatków VSTO  
 **Office i SharePoint** w węźle **nowy projekt** okno dialogowe zawiera następujące szablony projektów ułatwiające rozpoczęcie pracy Tworzenie dodatków narzędzi VSTO.  
  
-   **Dodatku narzędzi VSTO programu Excel 2013 i 2016**  
  
-   **InfoPath 2013 dodatku narzędzi VSTO**  
  
-   **Dodatku narzędzi VSTO programu Outlook 2013 i 2016**  
  
-   **Dodatek programu PowerPoint 2013 i 2016**  
  
-   **Projekt 2013 i 2016 Add-in**  
  
-   **Dodatek Visio 2013 i 2016**  
  
-   **Dodatek programu Word 2013 i 2016**  
  
-   **Dodatek programu Excel 2010**  
  
-   **Dodatek programu InfoPath 2010**  
  
-   **Dodatek programu Outlook 2010**  
  
-   **Dodatek programu PowerPoint 2010**  
  
-   **Dodatek Project 2010**  
  
-   **Dodatek Visio 2010**  
  
-   **Dodatek programu Word 2010**  
  
 W projekcie opartym na jednym z tych szablonów projektu kod w rozwiązaniu jest uruchamiany po otwarciu powiązanej aplikacji. W przeciwieństwie do projektów na poziomie dokumentu kod nie jest kojarzony z jednym dokumentem.  
  
 Więcej informacji na temat rozpoczynania pracy z tego typu projektami znajdują się w następujących tematach:  
  
-   [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
-   [Programowanie dodatków VSTO](../vsto/programming-vsto-add-ins.md)  
  
-   [Przewodnik: Tworzenie pierwszego dodatku VSTO dla programu Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
## <a name="document-vs-template-solutions"></a>Dokument programu vs. Szablon rozwiązania  
 Projektując rozwiązanie w oparciu o dokument programu Word lub skoroszyt programu Excel, należy wybrać najlepszy sposób udostępnienia tego dokumentu użytkownikom.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Czasami trzeba dać każdemu użytkownikowi osobną kopię. W takich przypadkach należy utworzyć rozwiązanie na bazie projektu dokumentu programu Excel lub Word.  
  
 Innym razem lepiej udostępnić szablon na serwerze, tak aby każdy użytkownik mógł otworzyć szablon i zapisać lokalną kopię jako dokument. W takich przypadkach należy utworzyć rozwiązanie na bazie projektu szablonu programu Excel lub Word.  
  
## <a name="comparison"></a>Porównanie  
 W poniższej tabeli przedstawiono różnice między dokumentami a szablonami.  
  
|Dokumenty|Szablony|  
|---------------|---------------|  
|Użytkownicy mogą otwierać i modyfikować dokument, chyba że ma on ustawiony atrybut tylko do odczytu. Wszelkie zapisane zmiany są przechowywane w oryginale.|Użytkownicy mogą otworzyć szablon, aby utworzyć kopię lokalną jako nowy dokument. Nie mogą oni modyfikować oryginału, chyba że otrzymają specjalne uprawnienia.|  
|Po otwarciu dokumentu zgłasza <xref:Microsoft.Office.Tools.Word.Document.Open> zdarzeń.|Po otwarciu szablonu zgłasza <xref:Microsoft.Office.Tools.Word.Document.New> zdarzeń.|  
  
##  <a name="Limitations"></a>Ograniczenia Szablony globalne i dodatki programu Excel (xla plików)  
 Dokumentów, skoroszytów i szablony może nie działać poprawnie jako szablony globalne lub dodatków VSTO programu Excel (xla plików).  
  
## <a name="word-templates"></a>Szablony programu Word  
 Jeśli szablon programu Microsoft Office Word zawiera rozszerzenia kodu zarządzanego, a szablon jest dołączony jako szablon globalny lub ładowany z katalogu Startup programu Word, nie dochodzi do wywołania zestawu projektu. Ponadto dokument nie rozpoznaje formatu szablonu będącego częścią rozwiązania utworzonego dla pakietu Office.  
  
## <a name="excel-add-ins-xla-files"></a>Dodatki programu Excel (pliki .xla)  
 Brak projektów pakietu Office do tworzenia dodatku VSTO programu Excel (plik xla). Istnieje możliwość zapisania skoroszytu jako pliku .xla, jednak operacja ta nie jest obsługiwana i jej nie zalecamy. Jeśli zapiszesz skoroszytu, który zarządza rozszerzenia kodu jako **dodatek Microsoft Excel pakietu Office (\*xla)** plików, można ją wybrać w **Add-Ins** okno dialogowe, aby zastosować do innego skoroszytu. W niektórych przypadkach kod działa w skoroszycie docelowym dodatku VSTO jest stosowana, ale takie użycie rozwiązania pakietu Office nie jest obsługiwane.  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Tworzenie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)   
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)   
 [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)   
 [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  