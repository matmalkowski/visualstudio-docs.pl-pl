---
title: 'Porady: tworzenie obsługi zdarzeń w projektach pakietu Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8b7e55ee7f094ad104d9c8eb6ef3057621bcccee
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254247"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Porady: tworzenie obsługi zdarzeń w projektach pakietu Office
  Istnieje kilka sposobów, aby utworzyć procedury obsługi zdarzeń w Visual Basic i C#. W widoku Projekt, można utworzyć domyślnie obsługi zdarzeń dla formantów przez dwukrotne kliknięcie formantu, lub za pomocą okienka zdarzenia z **właściwości** okna, aby utworzyć programy obsługi dla dowolnego zdarzenia w formancie. Jednak jeśli jesteś w widoku kodu, nie możesz przełączyć do widoku projektu, aby utworzyć program obsługi zdarzeń.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-an-event-handler-in-visual-basic"></a>Aby utworzyć program obsługi zdarzeń w języku Visual Basic  
  
1.  Z **Nazwa klasy** listy rozwijanej na górze edytora kodu, wybierz obiekt, który chcesz utworzyć program obsługi zdarzeń dla.  
  
    > [!NOTE]  
    >  Jeśli chcesz utworzyć obsługi zdarzeń `ThisDocument` lub `ThisWorkbook`, musisz wybrać **(ThisDocument zdarzeń)** lub **(ThisWorkbook zdarzeń)** w **Nazwa klasy**listy rozwijanej  
  
2.  Z **nazwę metody** listy rozwijanej na górze edytora kodu, wybierz zdarzenie.  
  
     Visual Studio tworzy program obsługi zdarzeń i przenosi punkt wstawiania do obsługi zdarzeń nowo utworzony. Jeśli program obsługi zdarzeń już istnieje, punkt wstawiania zostanie przeniesiony do istniejącego programu obsługi zdarzeń.  
  
### <a name="to-create-an-event-handler-in-c"></a>Aby utworzyć program obsługi zdarzeń w języku C#  
  
1.  Utworzyć delegata zdarzenia w **uruchamiania** zdarzeń klasy, wpisując nazwę kwalifikowaną zdarzenia spację, a następnie wpisując **+=** później bez spacji. Na przykład:  
  
     `this.<object name>.<event name> +=`  
  
2.  Na koniec wiersza kodu dwukrotnie naciśnij klawisz TAB.  
  
     Visual Studio automatycznie zakończeniu wiersza kodu, tworzy program obsługi zdarzeń i przenosi punkt wstawiania do obsługi zdarzeń nowo utworzony.  
  
## <a name="see-also"></a>Zobacz także  
 [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)   
 [Wskazówki: Program w odniesieniu do zdarzeń formantu NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)  
  
  