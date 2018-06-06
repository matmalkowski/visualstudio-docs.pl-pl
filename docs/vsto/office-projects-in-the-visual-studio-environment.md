---
title: Projekty pakietu Office w środowisku Visual Studio
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.WordDocument
- VST.ProjectItem.ExcelWorkbook
- VST.ProjectItem.ExcelTemplate
- VST.ProjectItem.ExcelSheet
- VST.ProjectItem.BlueprintCode
- VST.ProjectItem.Word
- VST.ProjectItem.Excel
- VST.ProjectItem.AddinProject
- Designer_Microsoft.VisualStudio.OfficeTools.Excel.Design.WorksheetDesigner
- VST.ProjectItem.ExtendedBluePrint
- VST.ProjectItem.WordTemplate
- Designer_Microsoft.VisualStudio.OfficeTools.Word.Design.DocumentDesigner
- VST.Designer.ExcelVST.Designer.Word
- VST.ProjectItem.ExtendedBlueprintCode
- VST.ProjectItem.BluePrint
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- hidden files [Office development in Visual Studio]
- project files [Office development in Visual Studio], hidden
- Office development in Visual Studio, documents in Visual Studio
- design view, Excel
- designers, Office development in Visual Studio
- Office documents [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], about documents in Visual Studio
- designers [Office development in Visual Studio]
- Word designer
- Word [Office development in Visual Studio], Word designer
- Visual Studio, Office documents in
- worksheets [Office development in Visual Studio]
- VST.Designer.ExcelVST.Designer.Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b85bbf5ac3507d9a65c8c2b3f0b71dbe61c1752
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693289"
---
# <a name="office-projects-in-the-visual-studio-environment"></a>Projekty pakietu Office w środowisku Visual Studio
  Dla projektów pakietu Microsoft Office przygotowano środowisko programistyczne podobne jak do innych typów projektów w programie, np. projektów interfejsu Windows Forms. Podczas tworzenia lub otwierania projektu pakietu Office, elementy projektu są wyświetlane w **Eksploratora rozwiązań**. W projektach na poziomie dokumentu dokument (tzn. dokument programu Word lub skoroszyt programu Excel) jest otwierany w programie Visual Studio i zachowuje się jak projektant wizualny.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="project-items-in-solution-explorer"></a>Elementy projektu w Eksploratorze rozwiązań  
 W projekcie poziomie dokumentu **Eksploratora rozwiązań** wyświetla następujące elementy domyślne:  
  
-   Węzły dla dokumentu, skoroszytu i arkuszy, które są dostosowywane przez projekt. Węzły te pełnią rolę kontenerów na pliki kodu skojarzone z dokumentem, skoroszytem i arkuszami.  
  
-   Pliki kodu skojarzone z dokumentem, skoroszytem i arkuszami, które są dostosowywane przez projekt. W projektach programu Word pliki kodu są powiązane z dokumentem lub szablonem programu Word. W projektach programu Excel pliki kodu są skojarzone ze skoroszytem lub szablonem programu Excel oraz z każdym arkuszem i arkuszem wykresu w skoroszycie lub szablonie.  
  
-   Ukryte pliki projektu, które nie są przeznaczone do bezpośredniej edycji. Aby uzyskać więcej informacji, zobacz [ukryte pliki projektu](#hiddenfiles).  
  
 W projekcie dodatku narzędzi VSTO **Eksploratora rozwiązań** wyświetla następujące elementy domyślne:  
  
-   Węzeł aplikacji. Ten węzeł ma taką samą nazwę jak aplikacja hosta **Word**, **Excel**, lub **Outlook**. Węzeł aplikacji zawiera plik kodu ThisAddIn. Zapewnia także **Namespace elementu hosta** właściwości. Aby uzyskać więcej informacji na temat tej właściwości, zobacz [właściwości w projektach pakietu Office](../vsto/properties-in-office-projects.md).  
  
-   Plik kodu ThisAddIn. Ten plik zawiera wygenerowane `ThisAddIn` klasy użytkownika dodatku VSTO. Aby uzyskać więcej informacji na temat tej klasy, zobacz [dodatków VSTO programu](../vsto/programming-vsto-add-ins.md).  
  
-   Ukryte pliki projektu, które nie są przeznaczone do bezpośredniej edycji. Aby uzyskać więcej informacji, zobacz [ukryte pliki projektu](#hiddenfiles).  
  
### <a name="temporary-certificates"></a>Tymczasowe certyfikaty  
 Projekty Office również obejmować tymczasowy certyfikat o nazwie *Nazwa projektu*_TemporaryKey.pfx. Certyfikat służy do podpisywania manifestów aplikacji i wdrażania projektu w trakcie programowania. Aby uzyskać więcej informacji, zobacz [przyznać zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md) i [rozwiązań Secure Office](../vsto/securing-office-solutions.md).  
  
###  <a name="hiddenfiles"></a> Pliki ukryte projektu  
 Niektóre pliki projektu są domyślnie ukryte. Pliki te są generowane przez program Visual Studio i różnią się w zależności od typu projektu. Aby wyświetlić ukryte pliki, kliknij przycisk **Pokaż wszystkie pliki** w **Eksploratora rozwiązań**.  
  
 Nie wolno modyfikować ukrytych plików projektu. Bezpośrednia edycja tych plików nie jest obsługiwana i może spowodować uszkodzenie projektu. Ukryte pliki projektu są generowane każdorazowo po wprowadzeniu pewnych zmian w dokumencie. Ręczna modyfikacja ukrytego pliku projektu spowoduje utratę tych zmian podczas ponownego generowania pliku.  
  
## <a name="document-designer-in-document-level-projects"></a>Dokument projektanta w projektach na poziomie dokumentu  
 W projektach na poziomie dokumentu dla programów Excel i Word jest dostępny projektant, który hostuje dokument skojarzony z projektem w programie Visual Studio. Projektant umożliwia modyfikowanie dokumentu bez konieczności wychodzenia poza środowisko Visual Studio.  
  
 Aby otworzyć dokument w projektancie, kliknij dwukrotnie plik kodu w **Eksploratora rozwiązań** skojarzonego z dokumentu. Na przykład, aby otworzyć arkusz **Sheet1 —** w Projektancie projektu programu Excel, kliknij dwukrotnie **Sheet1 —** pliku kodu.  
  
 Podczas modyfikowania dokumentu w projektancie można wykorzystać macierzystą funkcjonalność aplikacji pakietu Office. Na przykład można wpisać tekst w dokumencie lub arkuszu albo za pomocą Wstążki wykonać zadania takie jak dodanie tabeli lub wykresu. Domyślnie mapowania skrótów klawiaturowych są takie same jak w programie Visual Studio. Do używania pakietu Office odwzorowania skrótów klawiaturowych, Zmień ustawienia w obszarze **ustawienia klawiatury Microsoft Office** w węźle **opcje** okno dialogowe na **narzędzia** menu .  
  
### <a name="controls-on-documents"></a>Formanty w dokumentach  
 Możesz przeciągnąć *hostowania formantów* i formanty formularzy systemu Windows z programu Visual Studio **przybornika** na powierzchnię projektu dokumentu. Formanty hosta to specjalistyczne wersje obiektów pakietu Office, takie jak formanty zawartości programu Word i zakresy programu Excel, których można używać w projektach pakietu Office utworzonych przy użyciu programu Visual Studio. Formanty hosta mają dodatkowe funkcje nieobecne w odnośnych obiektach pakietu Office, np. tworzenie powiązań danych czy większy zbiór zdarzeń.  
  
 Aby uzyskać więcej informacji, zobacz [elementów, a informacje o formantach](../vsto/host-items-and-host-controls-overview.md) i [formanty formularzy Windows w przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
### <a name="excel-worksheets-and-workbooks-in-the-designer"></a>Arkusze programu Excel i skoroszytów w Projektancie  
 Po otwarciu arkusza w projektancie można go modyfikować tak samo, jak po otwarciu bezpośrednio w programie Excel. Dwukrotne kliknięcie komórki spowoduje przełączenie jej do trybu edycji. Po dwukrotnym kliknięciu komórki zawierającej formanty hosta, zostanie otwarty w edytorze kodu i Visual Studio generuje domyślny program obsługi zdarzeń dla formantu. Aby przechodzić do innych arkuszy, możesz klikać karty arkuszy u dołu projektanta.  
  
 Po otwarciu skoroszytu w projektancie nie widać żadnej powierzchni projektowej. Widok projektu skoroszytu to duży zasobnik elementów, który wypełnia projektanta.  
  
 Skoroszyt i każdy arkusz w skoroszycie mają powiązane pliki kodu. Każdy plik kodu zawiera wygenerowanego *element hosta* klasa, która reprezentuje skoroszytu lub arkusza. Aby uzyskać więcej informacji, zobacz [automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md).  
  
### <a name="word-documents-in-the-designer"></a>Dokumenty programu Word w Projektancie  
 Po otwarciu dokumentu w projektancie można go modyfikować tak samo, jak po otwarciu bezpośrednio w programie Word. Dwukrotne kliknięcie wyrazu w dokumencie spowoduje jego zaznaczenie. Jeśli jednak wyraz znajduje się wewnątrz formantu hosta, zostanie otwarty edytor kodu, a program Visual Studio wygeneruje domyślny program obsługi zdarzeń dla formantu.  
  
 Dokument ma skojarzony plik kodu. Plik kodu zawiera wygenerowanego *element hosta* klasa, która reprezentuje dokumentu. Aby uzyskać więcej informacji, zobacz [element hosta dokumentu](../vsto/document-host-item.md).  
  
### <a name="design-mode-vs-runtime-mode"></a>Tryb projektowania, a tryb środowiska uruchomieniowego  
 Gdy dokument jest otwarty w środowisku Visual Studio, jest zawsze w *tryb projektowania*. Niektóre zadania, takie jak przeciągnięcie formantu hosta na powierzchnię dokumentu, można wykonywać tylko w trybie projektowania.  
  
 Aby wyświetlić dokument w *trybie wykonywania*, należy otworzyć aplikacji i zarządzania dokumentami poza programem Visual Studio. Można również skompilować i uruchomić projekt. Wtedy dokument i aplikacja będą automatycznie otwierane poza środowiskiem Visual Studio.  
  
## <a name="code-editor"></a>Edytor kodu  
 Edytor kodu umożliwia wyświetlanie i modyfikowanie widocznych plików kodu w rozwiązaniu. Pliki te zawierają kod, który definiuje zachowanie rozwiązania.  
  
 Aby uzyskać więcej informacji na temat edytora kodu, zobacz [pisania kodu w edytorze kodu i tekstu](/visualstudio/ide/writing-code-in-the-code-and-text-editor). Aby uzyskać więcej informacji na temat pisania kodu w projektach pakietu Office, zobacz [napisać kod w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="properties-window"></a>Okno właściwości  
 **Właściwości** okno wyświetla właściwości dla elementów projektu, które są wybrane w **Eksploratora rozwiązań**oraz do elementów interfejsu użytkownika, które są wybrane w projektancie, takie jak formanty lub dokument w Projekt na poziomie dokumentu. Niektóre właściwości są specyficzne dla aplikacji i dokumentu, a inne takie same we wszystkich projektach.  
  
## <a name="data-sources-window"></a>Data Sources — Okno  
 Można użyć **źródeł danych** okna w projektach pakietu Office poziomie dokumentu przeciągnij źródła danych na dokumencie i utworzyć formant, który jest powiązany ze źródłem danych. Aby uzyskać więcej informacji, zobacz [powiązywanie formantów z danymi w Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).  
  
## <a name="see-also"></a>Zobacz także  
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Przegląd szablonów projektu pakietu Office](../vsto/office-project-templates-overview.md)   
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Właściwości w projektach pakietu Office](../vsto/properties-in-office-projects.md)  
  
  