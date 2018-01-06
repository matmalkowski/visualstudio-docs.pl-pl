---
title: "Dostosowywanie wstążki do programu Outlook | Dokumentacja firmy Microsoft"
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
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
ms.assetid: 11d10e72-806d-4d5e-b080-139bd8633eaa
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f44d1d8c2982e23995a3625205eaa0bddf7adc4e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-a-ribbon-for-outlook"></a>Dostosowywanie Wstążki do programu Outlook
  Podczas dostosowywania wstążki w programie Microsoft Office Outlook, należy rozważyć, gdy Twoje niestandardowa Wstążka będą wyświetlane w aplikacji. Program Outlook wyświetli wstążki w interfejsie użytkownika aplikacji głównej (UI) i w systemie windows, które otwierają użytkowników wykonywania niektórych zadań, takich jak tworzenie wiadomości e-mail. Inspektorzy noszą nazwy tych aplikacji systemu windows.  
  
 ![łącze do wideo](../vsto/media/playvideo.gif "łącze do wideo") dla powiązanych pokaz wideo, zobacz [jak I: Użyj projektanta wstążki do dostosowywania wstążki w programie Outlook?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="adding-a-custom-ribbon-to-the-main-application-ui"></a>Dodawanie niestandardowych wstążki do aplikacji głównej interfejsu użytkownika  
 Aplikacji głównej interfejsu użytkownika w programie Outlook jest nazywany Eksploratora. Jeśli używasz **wstążki (projektanta wizualnego)** elementu, można dodać wstążki do Eksploratora, klikając **RibbonType** właściwości wstążki w **właściwości** okna a następnie wybierając **Microsoft.Outlook.Explorer**.  
  
## <a name="assigning-a-ribbon-to-an-inspector"></a>Przypisywanie wstążki do Inspektora  
 Należy określić kontroler, który chcesz dostosować, określając typ Wstążka umożliwiająca klasy wiadomości, aby inspektor.  
  
 Jeśli używasz **wstążki (projektanta wizualnego)** element, kliknij przycisk **RibbonType** właściwości wstążki w **właściwości** okna, a następnie wybierz co najmniej jedną identyfikatory z wstążki Lista wartości.  
  
 Można dodać więcej niż jeden wstążki do projektu. Jeśli kilka wstążce udostępnia identyfikator wstążki, Zastąp metodę CreateRibbonExtensibilityObject w `ThisAddin` klasy z projektem, aby określić, które wstążki do wyświetlenia w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md). Aby uzyskać więcej informacji na temat poszczególnych typów wstążki, zobacz artykuł techniczne [Dostosowywanie Wstążki w programie Outlook 2007](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
## <a name="specifying-the-ribbon-type-by-using-ribbon-xml"></a>Określanie typu wstążki za pomocą XML wstążki  
 Jeśli używasz **wstążki (XML)** element, należy sprawdzić wartość *ribbonID* parametru w <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> — metoda i przywracać odpowiednie wstążki.  
  
 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> Metody jest generowana automatycznie przez program Visual Studio w pliku kodu wstążki. *RibbonID* parametru jest ciągiem, który identyfikuje Eksploratora lub Inspektora określonego typu. Aby uzyskać pełną listę możliwych wartości *ribbonID* parametru, zapoznaj się z artykułem techniczne [Dostosowywanie Wstążki w programie Outlook 2007](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
 Poniższy przykład kodu pokazuje sposób wyświetlania niestandardowego wstążki tylko w `Microsoft.Outlook.Mail.Compose` inspektora. Jest to kontroler, który zostanie otwarty, gdy użytkownik tworzy nową wiadomość e-mail. Na Wstążce, aby wyświetlić została określona w `GetResourceText()` metodę, która jest generowana w **wstążki** klasy. Aby uzyskać więcej informacji na temat **wstążki** , zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [XML — wstążka](../vsto/ribbon-xml.md)  
  
  