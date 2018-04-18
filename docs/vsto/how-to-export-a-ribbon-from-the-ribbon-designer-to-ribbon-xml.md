---
title: 'Porady: eksportowanie wstążki z projektanta wstążki do XML wstążki | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- Ribbon [Office development in Visual Studio], exporting
- XML [Office development in Visual Studio], Ribbon
- Ribbon Designer [Office development in Visual Studio]
- exporting Ribbon
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7aff56d1d7ee3533a83ef3edbdd8ba9271efd862
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Porady: eksportowanie wstążki z Projektanta wstążki do XML wstążki
  **Wstążki (projektanta wizualnego)** element nie obsługuje wszystkich możliwych typów dostosowywania wstążki. Aby dostosować wstążki w sposób zaawansowane, można eksportowanie wstążki z projektanta do pliku XML Wstążki i bezpośredniego edytowania pliku XML.  
  
> [!NOTE]  
>  Nie wszystkie wartości właściwości są wyświetlane w pliku XML wstążki. Aby uzyskać więcej informacji, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Aby eksportowanie wstążki z projektanta wstążki do XML wstążki  
  
1.  Kliknij prawym przyciskiem myszy plik kodu wstążki w **Eksploratora rozwiązań**, a następnie kliknij przycisk **Widok projektanta**.  
  
2.  Kliknij prawym przyciskiem myszy projektanta wstążki, a następnie kliknij przycisk **eksportowanie wstążki do XML**.  
  
     Visual Studio dodanie pliku XML Wstążki i pliku kodu XML wstążki do projektu.  
  
3.  W klasie kodu wstążki zlokalizować komentarze, które zaczynają się `TODO:`.  
  
4.  Skopiuj blok kodu w komentarze do **thisaddin —**, **ThisWorkbook**, lub **ThisDocument** klasy, w zależności od typu rozwiązanie tworzysz.  
  
     Ten kod umożliwia aplikacji Microsoft Office odnaleźć i załadować Twojego niestandardowa Wstążka. Aby uzyskać więcej informacji, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).  
  
5.  W **thisaddin —**, **ThisWorkbook**, lub **ThisDocument** klasy, usuń znaczniki komentarza bloku kodu.  
  
     Po usuń znaczniki komentarza kodu, powinien on przypominać poniższym przykładzie. W tym przykładzie klasa wstążki jest nazywana `MyRibbon`.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  Przełącz się do pliku kodu XML Wstążki i Znajdź `Ribbon Callbacks` regionu.  
  
     Jest to, w którym można zapisywać metody wywołania zwrotnego do obsługi akcje użytkownika, takie jak kliknięcie przycisku.  
  
7.  Utwórz metody wywołania zwrotnego dla każdego programu obsługi zdarzeń, która zarejestrowała w kodzie projektanta wstążki.  
  
8.  Przenieś wszystkie swój kod obsługi zdarzenia z obsługi zdarzeń do metod wywołania zwrotnego i zmodyfikuj kod do pracy z modelu programowania rozszerzalności wstążki (RibbonX).  
  
     Informacje o Pisanie metod wywołania zwrotnego i za pomocą modelu programowania RibbonX, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [XML wstążki](../vsto/ribbon-xml.md)   
 [Wskazówki: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Przewodnik: Tworzenie kart niestandardowych za pomocą XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  