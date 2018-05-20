---
title: Dostęp do regionów formularzy w czasie wykonywania
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at runtime
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c0cdea460b2a50819aff3c300b8510ffd577c8f6
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="access-a-form-region-at-runtime"></a>Dostęp do regionów formularzy w czasie wykonywania

|Informacje zawarte w tym artykule dotyczą|  
|----------------|  
|Informacje przedstawione w tym temacie mają zastosowane tylko do poniższych typów projektów i wersji pakietu Microsoft Office. Aby uzyskać więcej informacji, zobacz [funkcje dostępne w typu aplikacji i projektów pakietu Office](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Typ projektu**<br /><br /> — Projektów dodatku VSTO<br /><br /> **Wersja programu Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|  

 Użyj `Globals` klasy do regionów formularzy dostęp z dowolnego miejsca w projekcie programu Outlook. Aby uzyskać więcej informacji na temat `Globals` , zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).  

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Regionów formularzy dostępu, które pojawiają się w określonym oknie inspektora programu Outlook  
 Aby uzyskać dostęp do wszystkich regionów formularzy, które pojawiają się w określonym inspektora programu Outlook, należy wywołać `FormRegions` właściwość `Globals` klasy i podaj <xref:Microsoft.Office.Interop.Outlook.Inspector> obiekt, który reprezentuje kontroler.  

 Poniższy przykład pobiera kolekcję regionów formularzy, które są widoczne w inspektora, który aktualnie ma fokus. W tym przykładzie następnie uzyskuje dostęp do regionów formularzy w kolekcji o nazwie `formRegion1` i ustawia tekst wyświetlany w polu tekstowym do `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#2)]
 [!code-csharp[Trin_Outlook_FR_Access#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#2)]  

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Regionów formularzy dostępu, które pojawiają się w określonym oknie Eksploratora programu Outlook  
 Aby uzyskać dostęp do wszystkich regionów formularzy pojawiające się w określonym Explorer programu Outlook, należy wywołać `FormRegions` właściwość `Globals` klasy i podaj <xref:Microsoft.Office.Interop.Outlook.Explorer> obiekt, który reprezentuje Eksploratora.  

 Poniższy przykład pobiera kolekcję regionów formularzy, które są wyświetlane w Eksploratorze, który aktualnie ma fokus. W tym przykładzie następnie uzyskuje dostęp do regionów formularzy w kolekcji o nazwie `formRegion1` i ustawia tekst wyświetlany w polu tekstowym do `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#3)]
 [!code-csharp[Trin_Outlook_FR_Access#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#3)]  

## <a name="access-all-form-regions"></a>Dostęp do wszystkich regionów formularzy  
 Aby uzyskać dostęp do wszystkich regionów formularzy wyświetlanych w programie wszystkich inspektorzy i eksploratorów wszystkie, należy wywołać `FormRegions` właściwość `Globals` klasy.  

 Poniższy przykład pobiera kolekcję regionów formularza, które są wyświetlane w wszystkich inspektorzy i eksploratorów wszystkie. W tym przykładzie następnie uzyskuje dostęp do regionu formularza o nazwie `formRegion1` i ustawia tekst wyświetlany w polu tekstowym do `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Access#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#1)]  

## <a name="access-controls-on-a-form-region"></a>Kontroli dostępu do regionów formularzy  
 Do kontroli dostępu do regionów formularzy przy użyciu `Globals` klasy, należy formanty dostępne dla kodu poza plik kodu regionu formularza.  

### <a name="form-regions-designed-in-the-form-region-designer"></a>Regiony formularzy zaprojektowanych w projektanta regionów formularza  
 Język C# Zmień modyfikator każdego formantu, który chcesz uzyskać dostęp. Aby to zrobić, wybierz każdego formantu w projektanta regionów formularza i zmień **Modyfikatory** właściwości **wewnętrzne** lub **publicznego** w **właściwości** okna. Na przykład, jeśli zmienisz **modyfikator** właściwość `textBox1` do **wewnętrzne**, można uzyskać dostępu do `textBox1` , wpisując `Globals.FormRegions.FormRegion1.textBox1`.  

 W języku Visual Basic nie trzeba zmienić modyfikator.  

### <a name="imported-form-regions"></a>Regiony formularzy zaimportowany  
 Po zaimportowaniu regionu formularza, który został zaprojektowany w programie Outlook modyfikator dostępu elementu każdego formantu w regionu formularza staje się prywatne. Ponieważ nie może używać Projektanta regionów formularza, aby zmodyfikować regionu formularza zaimportowane, nie istnieje sposób zmiany modyfikator formantu w **właściwości** okna.  

 Aby włączyć dostęp do formantu z poza plik kodu regionu formularza, należy utworzyć właściwość w pliku kodu regionu formularza do zwrócenia tego formantu.  

 Aby uzyskać więcej informacji na temat tworzenia właściwości w języku C#, zobacz [porady: deklarowanie i użycie odczytu zapisu właściwości &#40;C&#35; Podręcznik programowania&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties).  

 Aby uzyskać więcej informacji na temat tworzenia właściwości w języku Visual Basic, zobacz [porady: Tworzenie właściwości (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property).  

## <a name="see-also"></a>Zobacz także  
 [Wytyczne tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Wskazówki: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Porady: dodawanie regionu formularza do projektu dodatek programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Niestandardowe akcje w regionach formularzy programu Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Wskazówki: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Porady: ochrona programu Outlook przed wyświetlaniem regionów formularzy](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)   
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Dostęp do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)  
