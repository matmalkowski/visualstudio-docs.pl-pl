---
title: 'Porady: programowane Włączanie ochrony arkuszy | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- protection, adding to worksheets
- documents [Office development in Visual Studio], document protection
- document protection, adding to worksheets
- worksheets, protecting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 23e0706f7436355e2308fbde8d945968da5348c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-protect-worksheets"></a>Porady: Programowane włączanie ochrony arkuszy
  Funkcja ochrony w programie Microsoft Office Excel uniemożliwia użytkownikom i kod modyfikowanie obiektów w arkuszu. Domyślnie wszystkie komórki są blokowane po włączeniu ochrony.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 W dostosowaniach na poziomie dokumentu arkuszy można chronić przy użyciu narzędzia Projektant programu Excel. Również chronić arkusz programowo w czasie wykonywania w typu projektu.  
  
> [!NOTE]  
>  Formanty formularzy systemu Windows nie można dodać do arkusza obszarów, które są chronione.  
  
## <a name="using-the-designer"></a>Przy użyciu narzędzia Projektant  
  
#### <a name="to-protect-a-worksheet-in-the-designer"></a>Aby chronić arkusz w Projektancie  
  
1.  W **zmiany** grupy **przeglądu** , kliknij pozycję **chronić arkusz**.  
  
     **Chronić arkusz** zostanie wyświetlone okno dialogowe. Można ustawić hasła i opcjonalnie określić pewne akcje, które użytkownicy mogą wykonać z arkusza, takie jak formatowanie komórek lub wstawić wierszy.  
  
 Można również zezwolić użytkownikom edytowanie określonych zakresów w arkuszach chronionych.  
  
#### <a name="to-allow-editing-in-specific-ranges"></a>Aby zezwolić na edycję w określonych zakresach  
  
1.  W **zmiany** grupy **przeglądu** , kliknij pozycję **Zezwalanie użytkownikom na edycję zakresów**.  
  
     **Zezwalanie użytkownikom na edycję zakresów** zostanie wyświetlone okno dialogowe. Można określić zakresy, które są odblokowane, przy użyciu hasła i użytkowników, którzy mogą edytować zakresy bez podania hasła.  
  
## <a name="using-code-at-run-time"></a>Przy użyciu kodu w czasie wykonywania  
 Poniższy kod ustawia hasło (przy użyciu zmiennej getPasswordFromUser, zawierającą uzyskanych od użytkownika hasła) i umożliwia sortowanie tylko.  
  
#### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>Aby chronić arkusz przy użyciu kodu w dostosowaniu poziomie dokumentu  
  
1.  Wywołanie <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> metody arkusza. W tym przykładzie założono, że korzystasz z arkusza o nazwie `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#27)]  
  
#### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>Aby chronić arkusz przy użyciu kodu w dodatku VSTO  
  
1.  Wywołanie <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> metody aktywnego arkusza.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#17)]  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Porady: programowane usuwanie ochrony z arkuszy](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)   
 [Porady: programowane Włączanie ochrony skoroszytów](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Porady: programowane ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Element hosta arkusza](../vsto/worksheet-host-item.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parametry opcjonalne w rozwiązaniach Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  