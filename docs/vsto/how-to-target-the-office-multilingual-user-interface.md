---
title: 'Porady: docelowa Office wielojęzyczny interfejs użytkownika'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1b917479598b73f71a0f3092c874276a700717d6
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262036"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Porady: docelowa Office wielojęzyczny interfejs użytkownika
  Wielojęzyczny interfejs użytkownika (MUI) to funkcja Microsoft Office, która umożliwia użytkownikowi końcowemu do zmiany języka interfejsu użytkownika (UI). Na przykład użytkownik końcowy pracy przy użyciu interfejsu użytkownika w języku angielskim, można zmienić język interfejsu użytkownika na język hiszpański.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Jeśli aplikacja będzie używany przez osoby korzystające z wielu języków pakietu Office, możesz dodać kod, aby automatycznie zmienić język z ciągów interfejsu użytkownika język używany przez pakiet Office na komputerze użytkownika (Jeśli użytkownik ma prawidłowe zasoby zainstalowany).  
  
## <a name="to-check-the-current-office-ui-setting"></a>Aby sprawdzić bieżące ustawienia interfejsu użytkownika pakietu Office  
  
1.  Użyj <xref:System.Threading.Thread.CurrentUICulture%2A> właściwości bieżącego wątku. Ustaw język z ciągów interfejsu użytkownika język wersji pakietu Office, które obecnie działają na komputerze użytkownika.  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: aplikacje pakietu Office docelowym za pośrednictwem podstawowe zestawy międzyoperacyjne](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Późne wiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md)  
  
  