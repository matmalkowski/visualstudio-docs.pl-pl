---
title: Niestandardowe akcje w regionach formularzy programu Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ec4c6a0ce361102ab216bc0c9f460a0bdd7a4a0d
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="custom-actions-in-outlook-form-regions"></a>Niestandardowe akcje w regionach formularzy programu Outlook
  Akcje wyświetlanie przycisków, które umożliwiają użytkownikom odpowiedzieć na element programu Microsoft Office Outlook. Na przykład, aby odpowiedzieć elementu poczty, kliknięciu **odpowiedzi**, **Odpowiedz wszystkim**, lub **do przodu** przycisków akcji. Każdy z tych akcji tworzy nowy element poczty i wypełnienie pól elementów przy użyciu informacji z oryginalnego elementu.  
  
 Można utworzyć akcji niestandardowej, która otwiera dowolny rodzaj elementu programu Outlook. Na przykład można dodać akcji niestandardowej, który zostanie otwarty nowy element terminu lub zadania. Ustaw właściwości niestandardowej akcji lub użyć niestandardowego kodu, aby wypełnić pola nowy element. Akcje niestandardowe są wyświetlane w **akcje niestandardowe** listy rozwijanej elementu, który jest otwarty w oknie inspektora programu Outlook.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="add-custom-actions-to-a-form-region"></a>Dodaj niestandardowe akcje do regionu formularza  
 Aby dodać akcję niestandardową do regionu formularza, użyj **akcje niestandardowe** okno dialogowe. Możesz otworzyć **akcje niestandardowe** okno dialogowe w **Eksploratora rozwiązań** rozwijając **manifestu** węzła, wybierając **CustomActions**właściwości, a następnie klikając przycisk wielokropka (![ASP.NET przenośnych elipsy projektanta](../sharepoint/media/mwellipsis.gif "elipsy ASP.NET Mobile Designer")).  
  
 Można użyć **akcje niestandardowe** okno dialogowe, aby określić *docelowe formularza*. Formularz docelowy jest formularz, który jest wyświetlany, gdy użytkownik wykonuje akcji niestandardowej.  
  
 Można również użyć **akcje niestandardowe** okno dialogowe, aby określić sposób informacje z oryginalnego elementu mają być widoczne w formularzu docelowym.  
  
 W poniższej tabeli opisano właściwości, które są dostępne w **akcje niestandardowe** okno dialogowe.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**AddressLike**|Określa, jak formularz docelowy zostaną rozwiązane.|  
|**Body**|Określa, jak treść elementu jest dołączany do formularza docelowego.|  
|**włączone**|Wskazuje, czy włączono akcji niestandardowej. Jeśli ta właściwość jest ustawiona na **false**, akcji niestandardowej jest wyłączona.|  
|**— Metoda**|Określa typ odpowiedzi dostępne podczas wykonywania akcji niestandardowej. Akcja niestandardowa można wysyłać formularza, otwórz formularz lub Monituj użytkownika, czy chcą wysłać lub otworzyć formularz.|  
|**Nazwa**|Określa nazwę wewnętrzny, który służy do akcji niestandardowej w kodzie odwołania.|  
|**ShowOnRibbon**|Wskazuje, czy mają być wyświetlane na Wstążce oryginalnego elementu akcji niestandardowej.|  
|**SubjectPrefix**|Określa tekst, który dodaje się na początku wiersza tematu formularza docelowego.|  
|**TargetForm**|Określa nazwę klasy wiadomości w postaci docelowej. Na przykład wpisz **IPM. Zadanie** aby otworzyć formularz zadania.|  
|**Tytuł**|Określa etykietę przycisku akcji niestandardowej.|  
  
## <a name="customize-a-custom-action-at-runtime"></a>Dostosowywanie akcji niestandardowej w czasie wykonywania  
 Można również dodać zachowanie do akcji niestandardowej przy użyciu kodu. Na przykład można dodać kod, który przyjmuje nazwy adresatów wiadomości e-mail i dodaje te nazwy jako uczestnicy nowego elementu terminu. W tym celu należy obsługiwać [Akcja niestandardowa](http://msdn.microsoft.com/library/office/ff862186.aspx) zdarzenie [MailItem obiektu](http://msdn.microsoft.com/library/office/ff861332.aspx).  
  
## <a name="see-also"></a>Zobacz także  
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Wskazówki: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  