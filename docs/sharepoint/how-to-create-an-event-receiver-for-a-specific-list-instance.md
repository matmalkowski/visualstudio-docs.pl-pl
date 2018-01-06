---
title: "Porady: tworzenie obsługiwanego odbiornika dla wystąpienia określonej listy | Dokumentacja firmy Microsoft"
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
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
ms.assetid: 4b4b3564-161a-4327-8963-50896c084ac2
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a820bc1a29db10fa5f65f1781c30218c62c2ee08
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Porady: tworzenie obsługiwanego odbiornika dla określonej listy formularzy
  Odbiornik zdarzeń wystąpienia listy reaguje na zdarzenia występujące w żadnym wystąpieniu definicji listy. Mimo że szablonu odbiorcy zdarzeń nie obsługuje wartości docelowej określonej listy formularzy, można zmodyfikować odbiorcy zdarzeń, które są ograniczone do definicji listy w celu reagowania na zdarzenia w wystąpieniu określonej listy.  
  
 Pod kątem określonej listy formularzy w Elements.xml odbiornika zdarzeń, Zastąp `ListTemplateId` z `ListUrl` i Dodaj adres URL wystąpienia listy.  
  
## <a name="creating-a-list-instance-event-receiver"></a>Tworzenie odbiornika zdarzeń wystąpienia listy  
 Poniższe kroki przedstawiają sposób zmodyfikować odbiornik zdarzeń elementu listy, aby odpowiadać tylko na zdarzenia występujące w wystąpieniu niestandardowe listy anonsów.  
  
#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>Aby zmodyfikować obsługiwanego odbiornika odpowiedzieć na określonej listy formularzy  
  
1.  W przeglądarce otwórz witrynę programu SharePoint.  
  
2.  W okienku nawigacji **wymieniono** łącza.  
  
3.  W **całą zawartość lokacji** wybierz pozycję **Utwórz** łącza.  
  
4.  W **Utwórz** okna dialogowego wybierz **anonsów** typu, nazwy anonsu **TestAnnouncements**, a następnie wybierz pozycję **Utwórz**przycisku.  
  
5.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Utwórz projekt odbiorcy zdarzeń.  
  
6.  W **odbiornika zdarzeń typ?** wybierz **zdarzenia elementu listy**.  
  
    > [!NOTE]  
    >  Możesz też wybrać inny rodzaj odbiornik zdarzeń zakresów do definicji listy, na przykład **listy zdarzeń E-mail** lub **listy zdarzeń przepływu pracy**.  
  
7.  W **elementu powinien być źródło zdarzenia?** wybierz **anonsów**.  
  
8.  W **obsługi następujących zdarzeń** listy, wybierz **jest dodawany element** pole wyboru, a następnie wybierz pozycję **Zakończ** przycisku.  
  
9. W **Eksploratora rozwiązań**, w obszarze EventReceiver1, otwórz Elements.xml.  
  
     Odbiorcy zdarzeń obecnie odwołuje się do definicji listy anonsów przy użyciu następującego wiersza:  
  
    ```  
    <Receivers ListTemplateId="104">  
    ```  
  
     Zmień ten wiersz na następujący tekst:  
  
    ```  
    <Receivers ListUrl="Lists/TestAnnouncements">  
    ```  
  
     Dzięki temu odbiornik zdarzeń, aby odpowiadać tylko na zdarzenia występujące w nowym **TestAnnouncements** listy anonsów, który został właśnie utworzony. Możesz zmienić `ListURL` atrybutów ma dotyczyć odwołanie wystąpienie listy na serwerze programu SharePoint.  
  
10. Otwórz plik kodu dla odbiornika zdarzeń i umieść punkt przerwania w metodzie ItemAdding.  
  
11. Wybierz klawisz F5, aby skompilować i uruchomić rozwiązanie.  
  
12. W programie SharePoint, wybierz **TestAnnouncements** łącze w okienku nawigacji.  
  
13. Wybierz **Dodaj nowy anons** łącza.  
  
14. Wprowadź tytuł powiadomienia, a następnie wybierz pozycję **zapisać** przycisku.  
  
     Zwróć uwagę, że punkt przerwania zostaje trafiony po dodaniu nowego elementu do listy niestandardowe anonsów.  
  
15. Wybierz klawisz F5, aby wznowić.  
  
16. W okienku nawigacji wybierz **wymieniono** łącza, a następnie wybierz pozycję **anonsów** łącza.  
  
17. Dodaj nowe powiadomienie.  
  
     Należy zauważyć, że odbiorcy zdarzeń nie spowoduje wyzwolenia na nowy anons, ponieważ odbiornika jest skonfigurowany do odpowiadać tylko na zdarzenia w wystąpienia listy niestandardowe anons, **TestAnnouncements**.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: tworzenie obsługiwanego odbiornika](../sharepoint/how-to-create-an-event-receiver.md)   
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  