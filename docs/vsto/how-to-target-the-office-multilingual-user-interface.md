---
title: "Porady: docelowa Office wielojęzyczny interfejs użytkownika | Dokumentacja firmy Microsoft"
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
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
ms.assetid: b1f03164-f0cf-42e3-942b-8cf90c242ffb
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3ee88cbcde2a25a13b4c4432afe5a5b1397ab727
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Porady: konfigurowanie pod kątem wielojęzykowego interfejsu użytkownika pakietu Office
  Wielojęzyczny interfejs użytkownika (MUI) to funkcja Microsoft Office, która umożliwia użytkownikowi końcowemu do zmiany języka interfejsu użytkownika (UI). Na przykład użytkownik końcowy pracy przy użyciu interfejsu użytkownika w języku angielskim, można zmienić język interfejsu użytkownika na język hiszpański.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Jeśli aplikacja będzie używany przez osoby korzystające z wielu języków pakietu Office, możesz dodać kod, aby automatycznie zmienić język z ciągów interfejsu użytkownika język używany przez pakiet Office na komputerze użytkownika (Jeśli użytkownik ma prawidłowe zasoby zainstalowany).  
  
### <a name="to-check-the-current-office-ui-setting"></a>Aby sprawdzić bieżące ustawienia interfejsu użytkownika pakietu Office  
  
1.  Użyj <xref:System.Threading.Thread.CurrentUICulture%2A> właściwości bieżącego wątku. Ustaw język z ciągów interfejsu użytkownika język używany przez wersję pakietu Office, aktualnie uruchomione na komputerze użytkownika.  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: docelowa aplikacji pakietu Office za pośrednictwem podstawowe zestawy międzyoperacyjne](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Późne wiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md)  
  
  