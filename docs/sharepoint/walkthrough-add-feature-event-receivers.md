---
title: "Wskazówki: Dodawanie przyszłych obsługiwanych odbiorników | Dokumentacja firmy Microsoft"
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
ms.assetid: fbd44c33-2c27-4d57-abca-21cddc16fbc3
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 27d565a51c026a6e143e18f122039d90627f55ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-add-feature-event-receivers"></a>Wskazówki: dodawanie odbiorców zdarzeń funkcji
  Odbiorcy zdarzeń funkcji metodami wykonania, gdy wystąpi jedno z następujących zdarzeń związanych z funkcji w programie SharePoint:  
  
-   Funkcja zostanie zainstalowana.  
  
-   Funkcja została aktywowana.  
  
-   Funkcja jest dezaktywowana.  
  
-   Funkcja zostanie usunięta.  
  
 W tym przewodniku przedstawiono sposób dodawania odbiorcy zdarzeń funkcji w projekcie programu SharePoint. Przedstawia on następujące zadania:  
  
-   Tworzenie pustego projektu z odbiornikiem zdarzeń funkcji.  
  
-   Obsługa **FeatureDeactivating** metody.  
  
-   Za pomocą modelu obiektów programu SharePoint projektu do dodania do listy Anonsy anonsu.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje systemu Microsoft Windows i programu SharePoint. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Program Visual Studio.  
  
## <a name="creating-a-feature-event-receiver-project"></a>Tworzenie projektu odbiorcy zdarzeń funkcji  
 Najpierw utwórz projekt zawiera odbiorcy zdarzeń funkcji.  
  
#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Aby utworzyć projekt z odbiornikiem zdarzeń funkcji  
  
1.  Na pasku menu wybierz **pliku**, **nowy**, **projektu** do wyświetlenia **nowy projekt** okno dialogowe.  
  
2.  Rozwiń węzeł **SharePoint** węźle albo **Visual C#** lub **Visual Basic**, a następnie wybierz pozycję **2010** węzła.  
  
3.  W **szablony** okienku wybierz **projektu programu SharePoint 2010** szablonu.  
  
     Dla przyszłych obsługiwanych odbiorników będą używać tego typu projektu, ponieważ mają one żaden szablon projektu.  
  
4.  W **nazwa** wprowadź **FeatureEvtTest**, a następnie wybierz pozycję **OK** przycisk, aby wyświetlić **Kreator dostosowania programu SharePoint**.  
  
5.  Na **określić poziom lokacji i zabezpieczeń dla debugowania** strony, wprowadź adres URL witryny programu SharePoint server do której chcesz dodać nowy element niestandardowego pola lub użyj domyślnej lokalizacji (http://\<*systemu Nazwa*> /).  
  
6.  W **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji.  
  
     Aby uzyskać więcej informacji na temat rozwiązania piaskownicy w porównaniu z rozwiązaniami farmy, zobacz [uwagi dotyczące rozwiązania piaskownicy](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Wybierz **Zakończ** przycisk i zwróć uwagę, że funkcja o nazwie Feature1 jest wyświetlany w obszarze **funkcje** węzła.  
  
## <a name="adding-an-event-receiver-to-the-feature"></a>Dodawanie odbiorcy zdarzeń funkcji  
 Następnie dodaj odbiorcy zdarzeń funkcji i Dodaj kod, który wykonuje się, gdy funkcja jest dezaktywowana.  
  
#### <a name="to-add-an-event-receiver-to-the-feature"></a>Aby dodać odbiorcy zdarzeń funkcji  
  
1.  Otwórz menu skrótów węzła funkcje, a następnie wybierz pozycję **dodać funkcję** można utworzyć funkcji.  
  
2.  W obszarze **funkcje** węzła, otwórz menu skrótów **Feature1**, a następnie wybierz **dodać odbiorcy zdarzeń** do dodania obsługiwanego odbiornika dla funkcji.  
  
     Spowoduje to dodanie pliku kodu, w obszarze Feature1. W takim przypadku go nosi nazwę Feature1.EventReceiver.cs lub Feature1.EventReceiver.vb, w zależności od języka programowania projektu.  
  
3.  Jeśli projekt został napisany w [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], Dodaj następujący kod w górnej części odbiorcy zdarzeń, jeśli nie jest już istnieje:  
  
     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]  
  
4.  Klasy odbiorcy zdarzeń zawiera kilka metod poza komentarzem, które działają jako zdarzenia. Zastąp **FeatureDeactivating** metody z następujących czynności:  
  
     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]  
  
## <a name="testing-the-feature-event-receiver"></a>Testowanie odbiorcy zdarzeń funkcji  
 Następnie należy zdezaktywować funkcję do testowania czy **FeatureDeactivating** metoda generuje powiadomienia na liście anonsów programu SharePoint.  
  
#### <a name="to-test-the-feature-event-receiver"></a>Aby przetestować odbiorcy zdarzeń funkcji  
  
1.  Ustaw wartość projektu **aktywnej konfiguracji wdrożenia** właściwości **aktywacji nie**.  
  
     Ustawienie tej właściwości uniemożliwia funkcję aktywacji w programie SharePoint i umożliwia debugowanie odbiorcy zdarzeń funkcji. Aby uzyskać więcej informacji, zobacz [debugowanie rozwiązań SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
2.  Wybierz **F5** klawisz, aby uruchomić projekt, a następnie wdrożyć go w programie SharePoint.  
  
3.  W górnej części strony sieci Web programu SharePoint, należy otworzyć **Akcje witryny** menu, a następnie wybierz pozycję **ustawienia lokacji**.  
  
4.  W obszarze **Akcje witryny** sekcji **ustawienia lokacji** wybierz pozycję **Zarządzanie funkcjami witryny** łącza.  
  
5.  Na **funkcje** wybierz pozycję **Aktywuj** znajdujący się obok **FeatureEvtTest Feature1** funkcji.  
  
6.  Na **funkcje** wybierz pozycję **Dezaktywuj** znajdujący się obok **FeatureEvtTest Feature1** funkcji, a następnie wybierz pozycję **Dezaktywuj tę funkcję**  potwierdzenie łącze, aby zdezaktywować funkcję.  
  
7.  Wybierz **Home** przycisku.  
  
     Należy zauważyć, że powiadomienia są wyświetlane w **anonsów** listy po dezaktywacji funkcję.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: tworzenie obsługiwanego odbiornika](../sharepoint/how-to-create-an-event-receiver.md)   
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  