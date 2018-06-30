---
title: 'Wskazówki: Dodawanie przyszłych obsługiwanych odbiorników | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4881aba0f8ac1ea0f634491d6549c72de74bf67a
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120301"
---
# <a name="walkthrough-add-feature-event-receivers"></a>Wskazówki: Dodawanie odbiorców zdarzeń funkcji
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
  
-   Obsługiwane wersje systemu Microsoft Windows i programu SharePoint. Aby uzyskać więcej informacji, zobacz [wymagania związane z opracowywaniem rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Program Visual Studio.  
  
## <a name="create-a-feature-event-receiver-project"></a>Tworzenie projektu odbiorcy zdarzeń funkcji
 Najpierw utwórz projekt zawiera odbiorcy zdarzeń funkcji.  
  
#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Aby utworzyć projekt z odbiornikiem zdarzeń funkcji  
  
1.  Na pasku menu wybierz **pliku** > **nowy** > **projektu** do wyświetlenia **nowy projekt** okno dialogowe.  
  
2.  Rozwiń węzeł **SharePoint** węźle albo **Visual C#** lub **Visual Basic**, a następnie wybierz pozycję **2010** węzła.  
  
3.  W **szablony** okienku wybierz **projektu programu SharePoint 2010** szablonu.  
  
     Dla przyszłych obsługiwanych odbiorników będą używać tego typu projektu, ponieważ mają one żaden szablon projektu.  
  
4.  W **nazwa** wprowadź **FeatureEvtTest**, a następnie wybierz pozycję **OK** przycisk, aby wyświetlić **Kreator dostosowania programu SharePoint**.  
  
5.  Na **określić poziom lokacji i zabezpieczeń dla debugowania** strony, wprowadź adres URL witryny programu SharePoint server do której chcesz dodać nowy element niestandardowego pola lub użyj domyślnej lokalizacji (http://\<*systemu Nazwa*> /).  
  
6.  W **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji.  
  
     Aby uzyskać więcej informacji na temat rozwiązania piaskownicy w porównaniu z rozwiązaniami farmy, zobacz [zagadnienia dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Wybierz **Zakończ** przycisk i zwróć uwagę, że funkcja o nazwie Feature1 jest wyświetlany w obszarze **funkcje** węzła.  
  
## <a name="add-an-event-receiver-to-the-feature"></a>Dodaj odbiorcy zdarzeń funkcji
 Następnie dodaj odbiorcy zdarzeń funkcji i Dodaj kod, który wykonuje się, gdy funkcja jest dezaktywowana.  
  
#### <a name="to-add-an-event-receiver-to-the-feature"></a>Aby dodać odbiorcy zdarzeń funkcji  
  
1.  Otwórz menu skrótów węzła funkcje, a następnie wybierz pozycję **dodać funkcję** można utworzyć funkcji.  
  
2.  W obszarze **funkcje** węzła, otwórz menu skrótów **Feature1**, a następnie wybierz **dodać odbiorcy zdarzeń** do dodania obsługiwanego odbiornika dla funkcji.  
  
     Spowoduje to dodanie pliku kodu, w obszarze Feature1. W takim przypadku nosić nazwę albo *Feature1.EventReceiver.cs* lub *Feature1.EventReceiver.vb*w zależności od języka programowania projektu.  
  
3.  Jeśli projekt został napisany w [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], Dodaj następujący kod w górnej części odbiorcy zdarzeń, jeśli nie jest już istnieje:  
  
     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]  
  
4.  Klasy odbiorcy zdarzeń zawiera kilka metod poza komentarzem, które działają jako zdarzenia. Zastąp **FeatureDeactivating** metody z następujących czynności:  
  
     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]  
  
## <a name="test-the-feature-event-receiver"></a>Testowanie odbiorcy zdarzeń funkcji
 Następnie należy zdezaktywować funkcję do testowania czy **FeatureDeactivating** metoda generuje powiadomienia na liście anonsów programu SharePoint.  
  
#### <a name="to-test-the-feature-event-receiver"></a>Aby przetestować odbiorcy zdarzeń funkcji  
  
1.  Ustaw wartość projektu **aktywnej konfiguracji wdrożenia** właściwości **aktywacji nie**.  
  
     Ustawienie tej właściwości uniemożliwia funkcję aktywacji w programie SharePoint i umożliwia debugowanie odbiorcy zdarzeń funkcji. Aby uzyskać więcej informacji, zobacz [rozwiązań SharePoint debugowania](../sharepoint/debugging-sharepoint-solutions.md).  
  
2.  Wybierz **F5** klawisz, aby uruchomić projekt, a następnie wdrożyć go w programie SharePoint.  
  
3.  W górnej części strony sieci Web programu SharePoint, należy otworzyć **Akcje witryny** menu, a następnie wybierz pozycję **ustawienia lokacji**.  
  
4.  W obszarze **Akcje witryny** sekcji **ustawienia lokacji** wybierz pozycję **Zarządzanie funkcjami witryny** łącza.  
  
5.  Na **funkcje** wybierz pozycję **Aktywuj** znajdujący się obok **FeatureEvtTest Feature1** funkcji.  
  
6.  Na **funkcje** wybierz pozycję **Dezaktywuj** znajdujący się obok **FeatureEvtTest Feature1** funkcji, a następnie wybierz pozycję **Dezaktywuj tę funkcję**  potwierdzenie łącze, aby zdezaktywować funkcję.  
  
7.  Wybierz **Home** przycisku.  
  
     Należy zauważyć, że powiadomienia są wyświetlane w **anonsów** listy po dezaktywacji funkcję.  
  
## <a name="see-also"></a>Zobacz także
 [Porady: tworzenie obsługiwanego odbiornika](../sharepoint/how-to-create-an-event-receiver.md)   
 [Tworzenie rozwiązań programu SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
