---
title: "Uzyskiwanie dostępu do wstążki w czasie wykonywania | Dokumentacja firmy Microsoft"
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
- Globals class, Ribbon
- Ribbon [Office development in Visual Studio], accessing
- RibbonManager class
ms.assetid: 8a7c7c6d-1a18-4d6b-98ee-e483d41f0cd8
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f69818d2e7c1b6ef2babd651247fe81709b80097
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="accessing-the-ribbon-at-run-time"></a>Uzyskiwanie dostępu do wstążki w czasie wykonywania
  Można napisać kod, aby pokazać, Ukryj i modyfikowanie wstążki, a użytkownicy mogą uruchomić kod z kontrolek w niestandardowego okienka zadań, w okienku Akcje lub regionów formularzy programu Outlook.  
  
 Dostęp do wstążki za pomocą `Globals` klasy. Dla projektów programu Outlook są dostępne wstążek, pojawiające się w określonym oknie inspektora programu Outlook lub w Eksploratorze programu Outlook.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="accessing-the-ribbon-by-using-the-globals-class"></a>Uzyskiwanie dostępu do wstążki za pomocą klasy globalne  
 Można użyć `Globals` klasę, aby uzyskać dostęp do wstążki w projektach na poziomie dokumentu i projektów dodatku VSTO z dowolnego miejsca w projekcie.  
  
 Aby uzyskać więcej informacji na temat `Globals` , zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 W poniższym przykładzie użyto `Globals` klasa niestandardowa Wstążka o nazwie dostępu do `Ribbon1` i Ustaw tekst wyświetlany w polu kombi na Wstążce, aby `Hello World`.  
  
 [!code-vb[Trin_Outlook_FR_Access#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#4)]
 [!code-csharp[Trin_Outlook_FR_Access#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#4)]  
  
## <a name="accessing-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Uzyskiwanie dostępu do kolekcji wstążki wyświetlanych w oknie Inspektora określonego programu Outlook  
 Dostęp można uzyskać kolekcję taśmy, które są wyświetlane w programie Outlook *inspektorzy*. Inspektora jest oknem, który zostanie otwarty w programie Outlook użytkownicy wykonywania niektórych zadań, takich jak tworzenie wiadomości e-mail. Aby uzyskać dostęp do okna inspektora na Wstążce, należy wywołać `Ribbons` właściwość `Globals` klasy i podaj <xref:Microsoft.Office.Interop.Outlook.Inspector> obiekt, który reprezentuje kontroler.  
  
 Poniższy przykład pobiera kolekcję wstążki inspektora, który aktualnie ma fokus. W tym przykładzie następnie uzyskuje dostęp do wstążki o nazwie `Ribbon1` i ustawia tekst wyświetlany w polu kombi na Wstążce, aby `Hello World`.  
  
 [!code-vb[Trin_Outlook_FR_Access#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#5)]
 [!code-csharp[Trin_Outlook_FR_Access#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#5)]  
  
## <a name="accessing-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Uzyskiwanie dostępu do kolekcji z taśmy, które pojawiają się w Eksploratorze określonego programu Outlook  
 Dostęp można uzyskać kolekcję taśmy, które są wyświetlane w programie Outlook *Explorer*. Eksplorator jest aplikacji głównej interfejsu użytkownika (UI) dla wystąpienia programu Outlook. Aby uzyskać dostęp do wstążki okno Eksploratora, należy wywołać `Ribbons` właściwość `Globals` klasy i podaj <xref:Microsoft.Office.Interop.Outlook.Explorer> obiekt, który reprezentuje Eksploratora.  
  
 Poniższy przykład pobiera kolekcję wstążki Eksploratora, który aktualnie ma fokus. W tym przykładzie następnie uzyskuje dostęp do wstążki o nazwie `Ribbon1` i ustawia tekst wyświetlany w polu kombi na Wstążce, aby `Hello World`.  
  
 [!code-vb[Trin_Outlook_FR_Access#6](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#6)]
 [!code-csharp[Trin_Outlook_FR_Access#6](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#6)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [XML wstążki](../vsto/ribbon-xml.md)   
 [Model obiektu Wstążka ― omówienie](../vsto/ribbon-object-model-overview.md)   
 [Wskazówki: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Wskazówki: Aktualizowanie formantów na Wstążce w czasie wykonywania](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Dostosowywanie wstążki do programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Uzyskiwanie dostępu do regionów formularzy w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)  
  
  