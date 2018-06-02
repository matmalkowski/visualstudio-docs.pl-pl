---
title: Dostosowywanie interfejsu użytkownika pakietu Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- menus [Office development in Visual Studio], customizing
- actions panes [Office development in Visual Studio], creating
- WPF [Office development in Visual Studio]
- toolbars [Office development in Visual Studio], customizing
- Office applications [Office development in Visual Studio], UI customization
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0152fea139d6351c947412260247c47f79bb6b66
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692463"
---
# <a name="office-ui-customization"></a>Dostosowywanie interfejsu użytkownika pakietu Office
  Interfejs użytkownika (UI) można dostosować aplikacji pakietu Microsoft Office, przy użyciu narzędzia Office developer tools w programie Visual Studio. W tym temacie opisano funkcje interfejsu użytkownika, które można dostosować w następujących sekcjach:  
  
-   [Porównanie funkcji interfejsu użytkownika](#Comparison)  
  
-   [Okienka akcji i niestandardowych okienek zadań](#Actions)  
  
-   [Niestandardowa Wstążka interfejsu użytkownika](#Ribbon)  
  
-   [Widoku zakulisowego](#Backstage)  
  
-   [Regiony formularzy programu Outlook](#FormRegion)  
  
-   [Formanty w dokumentach](#Controls)  
  
-   [Menu skrótów](#Shortcut)  
  
##  <a name="Comparison"></a> Porównanie funkcji interfejsu użytkownika  
 W poniższej tabeli porównano najważniejszych funkcji interfejsu użytkownika, które można dostosować w projektach Microsoft Office.  
  
|Funkcja|Typy obsługiwane projektów|Obsługiwane aplikacje Microsoft Office|  
|-------------|-----------------------------|---------------------------------------------|  
|W okienku Akcje|Dostosowania na poziomie dokumentów|Excel<br /><br /> Word|  
|Niestandardowe okienka zadań|Dodatków VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word<br /><br /> Excel|  
|Niestandardowa Wstążka interfejsu użytkownika|Dostosowania na poziomie dokumentów<br /><br /> Dodatków VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Word<br /><br /> Visio|  
|Widoku zakulisowego|Dostosowania na poziomie dokumentów<br /><br /> Dodatków VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)].<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Word<br /><br /> Visio|  
|Regiony formularzy programu Outlook|Dodatków VSTO|Outlook|  
|Formanty w dokumentach|Dostosowania na poziomie dokumentów<br /><br /> Dodatków VSTO|Excel<br /><br /> Word|  
|Menu skrótów|Dostosowania na poziomie dokumentów<br /><br /> Dodatków VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Word<br /><br /> Visio<br /><br /> Excel|  
  
##  <a name="Actions"></a> Okienka akcji i niestandardowych okienek zadań  
 Okienka zadań są panele interfejsu użytkownika, które są zazwyczaj zadokowane po jednej stronie okna w aplikacji pakietu Microsoft Office. Prawie wszystkie aplikacje Microsoft Office obejmują okienka zadań wbudowanych. Przykład okienka zadań to pomocy okienka zadań w programie Word.  
  
 Narzędzia Office development w Visual Studio zawierają dwa różne sposoby dostosowywania okienka zadań:  
  
-   Okienko akcji można dodać do dostosowania poziomie dokumentu. Domyślnie w okienku Akcje jest wyświetlana po prawej stronie aplikacji, z prawej strony z dokumentu. Jednak w okienku Akcje mogą być wyświetlane do lewej, top lub bottom dokumentu.  
  
-   Można dodać niestandardowego okienka zadań do dodatku VSTO. Użytkownicy mogą dock niestandardowych okienek zadań na różnych stronach w oknie aplikacji lub ich przeciągnij niestandardowych okienek zadań w dowolnej lokalizacji w oknie.  
  
 Okienka akcji i niestandardowych okienek zadań udostępniają funkcje, udostępniając szerokiej gamy kontrolek, aby ułatwić użytkownikom wykonywanie zadań takich jak wprowadzania danych. W porównaniu do grupy wstążek, okienka akcji i niestandardowych okienek zadań zapewnia znacznie większe obszaru tekstu i kontrolek.  
  
 Aby uzyskać więcej informacji na temat okienka akcji, zobacz [okienko akcji ― omówienie](../vsto/actions-pane-overview.md). Aby uzyskać więcej informacji o niestandardowych okienkach zadań, zobacz [niestandardowego okienka zadań](../vsto/custom-task-panes.md).  
  
##  <a name="Ribbon"></a> Niestandardowa Wstążka interfejsu użytkownika  
 Interfejs użytkownika wstążki do udostępnienia funkcji, które można dodać do aplikacji pakietu Office można dostosować. Wstążka jest sposób organizowania pokrewnych poleceń (w postaci formantów), dzięki czemu są one łatwiej znaleźć. Można tworzyć własne karty Wstążki i grupy, aby umożliwić użytkownikom dostęp do funkcji, które zapewniają w rozwiązaniu. Większość funkcji, które były dostępne za pośrednictwem menu i pasków zadań w starszych wersjach systemu Microsoft Office teraz są dostępne za pomocą wstążki.  
  
 Aby uzyskać więcej informacji, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).  
  
##  <a name="Backstage"></a> Widoku zakulisowego  
 W aplikacjach pakietu Office, klikając polecenie **pliku** kartę otwiera widok Backstage. Widok Backstage udostępnia interfejs użytkownika, który łączy zadań na poziomie plików i działań i zastępuje podobne funkcje dostępne w menu Microsoft Office System Microsoft Office 2007. Widok Backstage jest całkowicie rozszerzalny za pomocą XML.  
  
 Program Visual Studio nie zawiera projektanta lub interfejsów API dostosowywania widoku Backstage. Jednak jeśli dodasz **wstążki (XML)** elementu XML do projektu pakietu Office, można dodać do pliku XML wstążki, aby dostosować widok Backstage. Aby uzyskać więcej informacji na temat **wstążki (XML)** elementów, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).  
  
 Aby uzyskać więcej informacji dotyczących dostosowywania widoku Backstage, zobacz [wprowadzenie do pakietu Office 2010 Backstage widoku dla deweloperów](http://go.microsoft.com/fwlink/?LinkId=182189) i [dostosować widok pakietu Office 2010 Backstage dla deweloperów](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
##  <a name="FormRegion"></a> Regiony formularzy programu Outlook  
 Użyj regionów formularzy w celu dodania funkcji niestandardowych do standardowego formularzy programu Microsoft Office Outlook. Można utworzyć regionów formularzy w rozszerzających dowolnego istniejącego formularza z dodatkowych pól lub kontrolki. Jeśli tworzysz nowy region formularza za pomocą narzędzi programowania pakietu Office w Visual Studio, można użyć tylko formanty formularzy systemu Windows na regionu formularza. W przypadku zaimportowania regionu formularza, który został zaprojektowany w programie Outlook, można użyć tylko kontrolki natywne programu Outlook.  
  
 Można utworzyć regionów formularzy, które zajmują różnych obszarów interfejsu użytkownika programu Outlook. Na przykład sąsiadujących regionów formularzy są wyświetlane w dolnej części formularza na pierwszej stronie, a każdy sąsiadujących region formularza jest zwijany. Można także dodać regionów formularzy w oddzielnych która jest wyświetlana jako stronę pełnych dodatkowego formularza i które są wyświetlane na żadnych istniejących formularza standardowych lub niestandardowych.  
  
 Aby uzyskać więcej informacji, zobacz [regionów formularzy Outlook utwórz](../vsto/creating-outlook-form-regions.md).  
  
##  <a name="Controls"></a> Formanty w dokumentach  
 Można dodać wiele dokumenty programu Word i arkusze programu Excel. Na przykład można dodać formant wyboru daty do dokumentu, dlatego użytkownik wpisz daty w formacie, lub umieść przycisku w arkuszach wysyłać dane do bazy danych.  
  
 Podczas opracowywania projektów na poziomie dokumentu dla programu Excel lub Word, Projektant Visual Studio umożliwia dodawanie formantów do dokumentu lub skoroszytu w projekcie w czasie projektowania lub programowo można dodawać formanty w czasie wykonywania. Podczas opracowywania projektów dodatku VSTO dla programu Excel lub Word, można programowo dodawanie formantów do dowolnego otwartego dokumentu lub skoroszyt w czasie wykonywania.  
  
 Aby uzyskać więcej informacji, zobacz [elementów, a informacje o formantach](../vsto/host-items-and-host-controls-overview.md) i [formanty formularzy Windows w przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
##  <a name="Shortcut"></a> Menu skrótów  
 Menu skrótów pojawia się po kliknięciu prawym przyciskiem myszy w oknie aplikacji lub dokumentu. Można ustawić menu skrótów po wystąpieniu zdarzenia, takie jak kiedy użytkownik kliknie prawym przyciskiem myszy dokument, skoroszyt lub kontroli hosta. Liczba różnych menu poleceń lub kontrolek można dodać do menu skrótów. Tworzenie menu skrótów za pomocą XML. Jeśli dodasz **wstążki (XML)** elementu XML do projektu pakietu Office, można dodać do pliku XML wstążki, aby utworzyć menu skrótów. Aby uzyskać więcej informacji na temat Tworzenie menu skrótów za pomocą XML, zobacz [porady: Dodawanie poleceń do menu skrótów](../vsto/how-to-add-commands-to-shortcut-menus.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [Formanty formularzy Windows w przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)   
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)   
 [Użyj formantów WPF w rozwiązaniach pakietu Office](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Porady: pokazywanie karty dewelopera na Wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)   
 [Porady: dodatek Pokaż błędy interfejsu użytkownika](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Wskazówki: Zbieranie danych za pomocą formularza systemu Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)  
  
  