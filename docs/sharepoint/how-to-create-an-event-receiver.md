---
title: "Porady: tworzenie obsługiwanego odbiornika | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1b00d82679388c50d6d111209a9a206bd9587a3a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-an-event-receiver"></a>Porady: tworzenie obsługiwanego odbiornika
  Tworząc *odbiorcy zdarzeń*, mogą odpowiadać, gdy użytkownik korzysta z programu SharePoint elementy, takie jak listy lub elementów listy. Na przykład kod w odbiorcy zdarzeń mogą być wyzwalane, gdy użytkownik zmienia kalendarz lub usuwa nazwę z listy kontaktów. Wykonując w tym temacie nauczysz się, jak dodać odbiorca zdarzenia do wystąpienia listy.  
  
 Aby wykonać te kroki, należy zainstalować [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i obsługiwanych wersjach systemu Windows i programu SharePoint. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące opracowywania rozwiązań SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md). W tym przykładzie wymaga projektu SharePoint, dlatego też należy wykonać procedury w temacie [wskazówki: Tworzenie kolumny witryny, typu zawartości i listy dla SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).  
  
## <a name="adding-an-event-receiver"></a>Dodawanie odbiorcy zdarzeń  
 Projekt, który został utworzony w [wskazówki: Tworzenie kolumny witryny, typu zawartości i listy dla SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) zawiera kolumny niestandardowej witryny, listy niestandardowej i typu zawartości. W poniższej procedurze będzie Rozwiń ten projekt przez dodanie obsługi zdarzenia proste (odbiornik event) do wystąpienia listy pokazanie sposobu obsługi zdarzeń w elementach programu SharePoint, takie jak listy.  
  
#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Aby dodać odbiorca zdarzenia do wystąpienia listy  
  
1.  Otwórz projekt, który został utworzony w [wskazówki: Tworzenie kolumny witryny, typu zawartości i listy dla SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).  
  
2.  W **Eksploratora rozwiązań**, wybierz węzeł projektu programu SharePoint o nazwie **Clinic**.  
  
3.  Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
4.  Pod **Visual C#** lub **Visual Basic**, rozwiń węzeł **SharePoint** węzeł, a następnie wybierz pozycję **2010** elementu.  
  
5.  W **szablony** okienku wybierz **odbiorcy zdarzeń**, nadaj jej nazwę **TestEventReceiver1**, a następnie wybierz pozycję **OK** przycisku.  
  
     **Kreator dostosowania programu SharePoint** pojawi się.  
  
6.  W **odbiornika zdarzeń typ?** wybierz **zdarzenia elementu listy**.  
  
7.  W **elementu powinien być źródło zdarzenia?** wybierz **pacjentów (Clinic\Patients)**.  
  
8.  W **obsługi następujących zdarzeń** listy, zaznacz pole wyboru obok pozycji **element został dodany**, a następnie wybierz pozycję **Zakończ** przycisku.  
  
     Plik kodowy dla nowego odbiorcy zdarzeń zawiera jedną metodę o nazwie `ItemAdded`. W następnym kroku zostanie dodana kodu do tej metody, aby każdego kontakt będzie miała nazwę brązowy Scott domyślnie.  
  
9. Zastąp istniejącą `ItemAdded` metodę z następującym kodem, a następnie wybierz klawisz F5:  
  
     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]  
  
     Uruchamia kod, a witryna zostanie wyświetlona w przeglądarce sieci web programu SharePoint.  
  
10. Na pasek szybkiego uruchamiania wybierz **pacjentów** łącza, a następnie wybierz pozycję **Dodaj nowy element** łącza.  
  
     Zostanie otwarty formularz wpis dla nowych elementów.  
  
11. Wprowadź dane w polach, a następnie wybierz pozycję **zapisać** przycisku.  
  
     Po wybraniu **zapisać** przycisku **nazwa pacjenta** kolumny automatycznie aktualizuje nazwy brązowy Scott.  
  
## <a name="see-also"></a>Zobacz też  
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  