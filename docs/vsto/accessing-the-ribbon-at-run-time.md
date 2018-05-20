---
title: Dostęp do wstążki w czasie wykonywania
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Globals class, Ribbon
- Ribbon [Office development in Visual Studio], accessing
- RibbonManager class
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: abeffdbc61861aae3c0c9c53cb07d597abaa31c9
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="access-the-ribbon-at-runtime"></a>Dostęp do wstążki w czasie wykonywania
  Można napisać kod, aby pokazać, Ukryj i modyfikowanie wstążki, a użytkownicy mogą uruchomić kod z kontrolek w niestandardowego okienka zadań, w okienku Akcje lub regionów formularzy programu Outlook.  

 Dostęp do wstążki za pomocą `Globals` klasy. Dla projektów programu Outlook są dostępne wstążek, pojawiające się w określonym oknie inspektora programu Outlook lub w Eksploratorze programu Outlook.  

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  

## <a name="access-the-ribbon-by-using-the-globals-class"></a>Dostęp do wstążki przy użyciu klasy globalne  
 Można użyć `Globals` klasę, aby uzyskać dostęp do wstążki w projektach na poziomie dokumentu i projektów dodatku VSTO z dowolnego miejsca w projekcie.  

 Aby uzyskać więcej informacji na temat `Globals` , zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).  

 W poniższym przykładzie użyto `Globals` klasa niestandardowa Wstążka o nazwie dostępu do `Ribbon1` i Ustaw tekst wyświetlany w polu kombi na Wstążce, aby `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#4)]
 [!code-csharp[Trin_Outlook_FR_Access#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#4)]  

## <a name="access-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Dostęp do kolekcji taśmy, które pojawiają się w określonym oknie inspektora programu Outlook  
 Dostęp można uzyskać kolekcję taśmy, które są wyświetlane w programie Outlook *inspektorzy*. Inspektora jest oknem, który zostanie otwarty w programie Outlook użytkownicy wykonywania niektórych zadań, takich jak tworzenie wiadomości e-mail. Aby uzyskać dostęp do okna inspektora na Wstążce, należy wywołać `Ribbons` właściwość `Globals` klasy i podaj <xref:Microsoft.Office.Interop.Outlook.Inspector> obiekt, który reprezentuje kontroler.  

 Poniższy przykład pobiera kolekcję wstążki inspektora, który aktualnie ma fokus. W tym przykładzie następnie uzyskuje dostęp do wstążki o nazwie `Ribbon1` i ustawia tekst wyświetlany w polu kombi na Wstążce, aby `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#5)]
 [!code-csharp[Trin_Outlook_FR_Access#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#5)]  

## <a name="access-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Dostęp do kolekcji taśmy, które są wyświetlane dla określonego programu Outlook Explorer  
 Dostęp można uzyskać kolekcję taśmy, które są wyświetlane w programie Outlook *Explorer*. Eksplorator jest aplikacji głównej interfejsu użytkownika (UI) dla wystąpienia programu Outlook. Aby uzyskać dostęp do wstążki okno Eksploratora, należy wywołać `Ribbons` właściwość `Globals` klasy i podaj <xref:Microsoft.Office.Interop.Outlook.Explorer> obiekt, który reprezentuje Eksploratora.  

 Poniższy przykład pobiera kolekcję wstążki Eksploratora, który aktualnie ma fokus. W tym przykładzie następnie uzyskuje dostęp do wstążki o nazwie `Ribbon1` i ustawia tekst wyświetlany w polu kombi na Wstążce, aby `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#6](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#6)]
 [!code-csharp[Trin_Outlook_FR_Access#6](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#6)]  

## <a name="see-also"></a>Zobacz także  
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [XML wstążki](../vsto/ribbon-xml.md)   
 [Model obiektu Wstążka ― omówienie](../vsto/ribbon-object-model-overview.md)   
 [Wskazówki: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Wskazówki: Aktualizowanie formantów na Wstążce w czasie wykonywania](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Dostosowywanie wstążki do programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Dostęp do regionów formularzy w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)  
