---
title: Model obiektu Outlook ― omówienie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.OutlookAddin
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], object model overview
- object models [Office development in Visual Studio], Office
- objects [Office development in Visual Studio], Office object models
- object models [Office development in Visual Studio], Outlook
- Office object models
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7e2d0141611a13e7b1ee9b20b8988466c92f3ce2
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693049"
---
# <a name="outlook-object-model-overview"></a>Model obiektu Outlook ― omówienie
  Umożliwiające tworzenie dodatków narzędzi VSTO dla programu Microsoft Office Outlook, mogą współdziałać z obiektami, które są udostępniane przez model obiektów programu Outlook. Model obiektów programu Outlook zawiera klasy i interfejsy, które reprezentują elementów interfejsu użytkownika. Na przykład <xref:Microsoft.Office.Interop.Outlook.Application> obiekt reprezentuje całej aplikacji <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> obiekt reprezentuje folder zawierający wiadomości e-mail lub innych elementów i <xref:Microsoft.Office.Interop.Outlook.MailItem> obiekt reprezentuje wiadomości e-mail.  
  
 Ten temat zawiera krótki przegląd niektórych obiektów głównych w modelu obiektów programu Outlook. Dla zasobów można znaleźć więcej informacji na temat całego modelu obiektów programu Outlook, zobacz [skorzystaj z dokumentacji modelu obiektów programu Outlook](#refdoc).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak I: Outlook używany do tworzenia raportu niestandardowego zadania?](http://go.microsoft.com/fwlink/?LinkID=130315).  
  
## <a name="access-objects-in-an-outlook-project"></a>Uzyskiwanie dostępu do obiektów w projekcie programu Outlook  
 Wiele obiektów, które mogą prowadzić interakcję w programie Outlook. Aby skutecznie użyć modelu obiektów, należy zapoznać się z następujących obiektów najwyższego poziomu:  
  
-   <xref:Microsoft.Office.Interop.Outlook.Application>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Explorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Inspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MailItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.TaskItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ContactItem>  
  
### <a name="application-object"></a>Obiekt aplikacji  
 <xref:Microsoft.Office.Interop.Outlook.Application> Obiekt reprezentuje aplikację Outlook i jest obiektu najwyższego poziomu w modelu obiektów programu Outlook. Oto niektóre z najważniejszych elementów członkowskich tego obiektu:  
  
-   [Createitem —](http://msdn.microsoft.com/en-us/771707fb-5f34-473d-9fdf-09a6a7f55ece) metodę, która umożliwia utworzenie nowego elementu, takie jak wiadomości e-mail, zadania lub terminu.  
  
-   <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> Właściwość, która umożliwia dostęp do systemu windows, które wyświetlanie zawartości folderu w interfejsie użytkownika (UI) programu Outlook.  
  
-   <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> Właściwość, która umożliwia dostęp do systemu windows, umożliwiające wyświetlanie zawartości pojedynczego elementu, takie jak wiadomości lub spotkania żądania poczty e-mail.  
  
 Aby uzyskać wystąpienia <xref:Microsoft.Office.Interop.Outlook.Application> obiektów, użyj pola aplikacji `ThisAddIn` klasy w projekcie. Aby uzyskać więcej informacji, zobacz [dodatków VSTO programu](../vsto/programming-vsto-add-ins.md).  
  
> [!NOTE]  
>  Aby uniknąć ostrzeżenia o zabezpieczeniach podczas korzystania z właściwości i metod, które są blokowane przez strażnik modelu obiektów programu Outlook, uzyskiwanie obiektów programu Outlook z pola aplikacji `ThisAddIn` klasy. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń określone dla rozwiązań pakietu Office](../vsto/specific-security-considerations-for-office-solutions.md).  
  
### <a name="explorer-object"></a>Eksplorator obiektów  
 <xref:Microsoft.Office.Interop.Outlook.Explorer> Obiekt reprezentuje okna, które wyświetla zawartość folderu, który zawiera elementy, takie jak wiadomości e-mail, zadania lub terminów. <xref:Microsoft.Office.Interop.Outlook.Explorer> Obiekt zawiera metody i właściwości, które służą do modyfikowania okna i zdarzenia, które są wywoływane, gdy zmienia się okna.  
  
 Aby uzyskać <xref:Microsoft.Office.Interop.Outlook.Explorer> obiektów, wykonaj jedną z następujących czynności:  
  
-   Użyj <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> właściwość <xref:Microsoft.Office.Interop.Outlook.Application> obiekt, aby uzyskać dostęp do wszystkich <xref:Microsoft.Office.Interop.Outlook.Explorer> obiektów w programie Outlook.  
  
-   Użyj <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> metody <xref:Microsoft.Office.Interop.Outlook.Application> obiekt, aby pobrać <xref:Microsoft.Office.Interop.Outlook.Explorer> czy aktualnie ma fokus.  
  
-   Użyj `GetExplorer` metody <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> obiekt, aby pobrać <xref:Microsoft.Office.Interop.Outlook.Explorer> dla bieżącego folderu.  
  
### <a name="inspector-object"></a>Obiekt Inspektora  
 <xref:Microsoft.Office.Interop.Outlook.Inspector> Obiekt reprezentuje okno wyświetla pojedynczy element, takie jak wiadomości e-mail, zadania lub terminu. <xref:Microsoft.Office.Interop.Outlook.Inspector> Obiekt zawiera metody i właściwości, które służą do modyfikowania okna i zdarzenia, które są wywoływane, gdy zmienia się okna.  
  
 Aby uzyskać <xref:Microsoft.Office.Interop.Outlook.Inspector> obiektów, wykonaj jedną z następujących czynności:  
  
-   Użyj <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> właściwość <xref:Microsoft.Office.Interop.Outlook.Application> obiekt, aby uzyskać dostęp do wszystkich <xref:Microsoft.Office.Interop.Outlook.Inspector> obiektów w programie Outlook.  
  
-   Użyj <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> metody <xref:Microsoft.Office.Interop.Outlook.Application> obiekt, aby pobrać <xref:Microsoft.Office.Interop.Outlook.Inspector> czy aktualnie ma fokus.  
  
-   Użyj `GetInspector` metody określonej pozycji, takich jak <xref:Microsoft.Office.Interop.Outlook.MailItem> lub <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>, aby pobrać inspektora, który jest skojarzony z nim.  
  
### <a name="mapifolder-object"></a>Obiekt MAPIFolder  
 <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> Obiekt reprezentuje folder zawierający wiadomości e-mail, kontakty, zadania i inne elementy. W programie Outlook 16 domyślne <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> obiektów.  
  
 Wartość domyślna <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> obiekty są definiowane przez <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> wartości wyliczenia. Na przykład  
  
 Odpowiada Microsoft.Office.Interop.Outlook.OlDefaultFolders.olFolderInbox **skrzynki odbiorczej** folderu w programie Outlook.  
  
 Na przykład pokazujący sposób uzyskać dostępu do domyślnego <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> i utworzyć nową <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>, zobacz [porady: programowane Tworzenie niestandardowych elementów folderu](../vsto/how-to-programmatically-create-custom-folder-items.md).  
  
### <a name="mailitem-object"></a>Obiekt MailItem  
 <xref:Microsoft.Office.Interop.Outlook.MailItem> Obiekt reprezentuje wiadomości e-mail. <xref:Microsoft.Office.Interop.Outlook.MailItem> obiekty są zwykle w folderach, takich jak **skrzynki odbiorczej**, **elementy wysłane**, i **skrzynki nadawczej**. <xref:Microsoft.Office.Interop.Outlook.MailItem> Udostępnia właściwości i metody, które mogą służyć do tworzenia i wysyłania wiadomości e-mail.  
  
 Na przykład, który pokazuje, jak utworzyć wiadomość e-mail, zobacz [porady: programowane Tworzenie elementu poczty e-mail](../vsto/how-to-programmatically-create-an-e-mail-item.md).  
  
### <a name="appointmentitem-object"></a>Obiekt AppointmentItem  
 <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> Obiekt reprezentuje spotkania, terminem jednorazowe lub terminu cyklicznego lub spotkania w **kalendarza** folderu. <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> Obiektu zawiera metody, które wykonuje działania takie jak odpowiada na żądania lub przekazywania wezwania na spotkanie i właściwości, które określają szczegółami, takie jak miejsce i czas.  
  
 Na przykład, który pokazuje, jak utworzyć termin, zobacz [porady: programowane Tworzenie wezwania na spotkanie](../vsto/how-to-programmatically-create-a-meeting-request.md).  
  
### <a name="taskitem-object"></a>Obiekt TaskItem  
 <xref:Microsoft.Office.Interop.Outlook.TaskItem> Obiekt reprezentuje zadania do wykonania w określonym przedziale czasu. <xref:Microsoft.Office.Interop.Outlook.TaskItem> obiekty znajdują się w **zadania** folderu.  
  
 Aby utworzyć zadanie, należy użyć [createitem —](http://msdn.microsoft.com/en-us/771707fb-5f34-473d-9fdf-09a6a7f55ece) metody <xref:Microsoft.Office.Interop.Outlook.Application> obiektu i przekaż wartość <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> dla parametru.  
  
### <a name="contactitem-object"></a>Obiekt ContactItem  
 <xref:Microsoft.Office.Interop.Outlook.ContactItem>Obiekt reprezentuje kontaktu w **kontaktów** folderu. <xref:Microsoft.Office.Interop.Outlook.ContactItem> obiekty zawierają szereg informacji kontaktowych dla osób, które reprezentują, takie jak adresy, adresy e-mail i numerów telefonów.  
  
 Aby uzyskać przykład przedstawia sposób tworzenia nowego kontaktu, zobacz [porady: programowane Dodawanie wpisu do kontaktów programu Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Na przykład pokazujący sposób wyszukiwania istniejącego zobacz [porady: programowane wyszukiwanie określonego kontaktu](../vsto/how-to-programmatically-search-for-a-specific-contact.md).  
  
##  <a name="refdoc"></a> Skorzystaj z dokumentacji modelu obiektów programu Outlook  
 Aby uzyskać pełne informacje o modelu obiektów programu Outlook mogą odwoływać się do odwołania podstawowego zestawu międzyoperacyjnego (PIA) programu Outlook i odwołanie modelu obiektu języka VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Odwołanie do podstawowego zestawu międzyoperacyjnego  
 Odwołania Outlook PIA dokumentów typów na podstawowe zestawy międzyoperacyjne dla programu Outlook 2010. Aby uzyskać więcej informacji, zobacz [odwołania podstawowego zestawu międzyoperacyjnego Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=189580).  
  
 Oprócz informacji dla wszystkich typów w PIAs, ta dokumentacja zawiera dodatkowe informacje na temat struktury PIAs i przykładów kodu dla typowych zadań automatyzacji programu Outlook.  
  
### <a name="vba-object-model-reference"></a>Odwołania do modelu obiektu VBA  
 Odwołania do modelu obiektu VBA dokumentów modelu obiektów programu Outlook, ponieważ jest narażony na język Visual Basic dla kodu aplikacji (VBA). Aby uzyskać więcej informacji, zobacz [odwołania do modelu obiektu Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=199769).  
  
 Wszystkie obiekty i elementów członkowskich w odwołania do modelu obiektu VBA odpowiadają typy i składniki w PIA programu Outlook. Na przykład obiekt inspektora odwołania do modelu obiektu VBA odpowiada <xref:Microsoft.Office.Interop.Outlook.Inspector> obiektu w PIA programu Outlook. Odwołania do modelu obiektu VBA zapewnia przykłady kodu dla większości właściwości, metod i zdarzeń, jednak należy translacji kod VBA w niniejszej dokumentacji Visual Basic lub Visual C#, jeśli chcesz używać ich w projekcie dodatku narzędzi VSTO programu Outlook utworzonego za pomocą Program Visual Studio.  
  
### <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Praca z elementami kontaktów](../vsto/working-with-contact-items.md)|Zawiera tematy, które pokazują, jak wykonać zadania z kontaktów.|  
|[Praca z elementami poczty](../vsto/working-with-mail-items.md)|Zawiera tematy, które pokazują, jak wykonać zadania z elementami poczty.|  
|[Praca z folderami](../vsto/working-with-folders.md)|Zawiera tematy, które pokazują, jak wykonać zadania z folderów.|  
|[Praca z elementami kalendarza](../vsto/working-with-calendar-items.md)|Zawiera tematy, które pokazują, jak wykonać zadania z elementami kalendarza.|  
|[Porady: programowane wyznaczanie bieżącego elementu programu Outlook](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Pokazuje, jak można wyświetlić nazwę bieżącego folderu i niektóre informacje na temat wybranego elementu.|  
  