---
title: "Porady: tworzenie obsługi zdarzeń w projektach pakietu Office | Dokumentacja firmy Microsoft"
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
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
ms.assetid: 2cfd6a45-4c25-4431-b4fc-e0f2c0a72e54
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 151648a6c12e2c28d912be3b75c51b438ae5ee13
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
1.  Utworzyć delegata zdarzenia w **uruchamiania** zdarzeń klasy, wpisując nazwę kwalifikowaną zdarzenia spację, a następnie wpisując  **+=**  później bez spacji. Na przykład:  
  
     `this.<object name>.<event name> +=`  
  
2.  Na koniec wiersza kodu dwukrotnie naciśnij klawisz TAB.  
  
     Visual Studio automatycznie zakończeniu wiersza kodu, tworzy program obsługi zdarzeń i przenosi punkt wstawiania do obsługi zdarzeń nowo utworzony.  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie kodu dla rozwiązań pakietu Office](../vsto/writing-code-in-office-solutions.md)   
 [Wskazówki: Programowanie w odniesieniu do zdarzeń formantu NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Kompilowanie rozwiązań pakietu Office](../vsto/building-office-solutions.md)  
  
  