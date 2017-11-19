---
title: "Akcje niestandardowe w programie Outlook tworzą regionów | Dokumentacja firmy Microsoft"
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
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
ms.assetid: 583fd5f0-aafa-4858-9c54-38a9fdf3bede
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74c688d0430b95c54f1f871ad6f82fde6fa781ac
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="custom-actions-in-outlook-form-regions"></a>Niestandardowe akcje w regionach formularzy programu Outlook
  Akcje wyświetlanie przycisków, które umożliwiają użytkownikom odpowiedzieć na element programu Microsoft Office Outlook. Na przykład, aby odpowiedzieć elementu poczty, kliknięciu **odpowiedzi**, **Odpowiedz wszystkim**, lub **do przodu** przycisków akcji. Każdy z tych akcji tworzy nowy element poczty i wypełnienie pól elementów przy użyciu informacji z oryginalnego elementu.  
  
 Można utworzyć akcji niestandardowej, która otwiera dowolny rodzaj elementu programu Outlook. Na przykład można dodać akcji niestandardowej, który zostanie otwarty nowy element terminu lub zadania. Ustaw właściwości niestandardowej akcji lub użyć niestandardowego kodu, aby wypełnić pola nowy element. Akcje niestandardowe są wyświetlane w **akcje niestandardowe** listy rozwijanej elementu, który jest otwarty w oknie inspektora programu Outlook.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="adding-custom-actions-to-a-form-region"></a>Dodawanie działań niestandardowych do regionu formularza  
 Aby dodać akcję niestandardową do regionu formularza, użyj **akcje niestandardowe** okno dialogowe. Możesz otworzyć **akcje niestandardowe** okno dialogowe w **Eksploratora rozwiązań** rozwijając **manifestu** węzła, wybierając **CustomActions**właściwości, a następnie klikając przycisk wielokropka (![elipsy ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipsy ASP.NET Mobile Designer")).  
  
 Można użyć **akcje niestandardowe** okno dialogowe, aby określić *docelowe formularza*. Formularz docelowy jest formularz, który jest wyświetlany, gdy użytkownik wykonuje akcji niestandardowej.  
  
 Można również użyć **akcje niestandardowe** okno dialogowe, aby określić sposób informacje z oryginalnego elementu mają być widoczne w formularzu docelowym.  
  
 W poniższej tabeli opisano właściwości, które są dostępne w **akcje niestandardowe** okno dialogowe.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**AddressLike**|Określa, jak formularz docelowy zostaną rozwiązane.|  
|**Treści**|Określa, jak treść elementu jest dołączany do formularza docelowego.|  
|**Włączone**|Wskazuje, czy włączono akcji niestandardowej. Jeśli ta właściwość jest ustawiona na **false**, akcji niestandardowej jest wyłączona.|  
|**— Metoda**|Określa typ odpowiedzi dostępne podczas wykonywania akcji niestandardowej. Akcja niestandardowa można wysyłać formularza, otwórz formularz lub Monituj użytkownika, czy chcą wysłać lub otworzyć formularz.|  
|**Nazwa**|Określa nazwę wewnętrzny, który służy do akcji niestandardowej w kodzie odwołania.|  
|**ShowOnRibbon**|Wskazuje, czy mają być wyświetlane na Wstążce oryginalnego elementu akcji niestandardowej.|  
|**SubjectPrefix**|Określa tekst, który dodaje się na początku wiersza tematu formularza docelowego.|  
|**TargetForm**|Określa nazwę klasy wiadomości w postaci docelowej. Na przykład wpisz **IPM. Zadanie** aby otworzyć formularz zadania.|  
|**Tytuł**|Określa etykietę przycisku akcji niestandardowej.|  
  
## <a name="customizing-a-custom-action-at-run-time"></a>Dostosowywanie akcji niestandardowej w czasie wykonywania  
 Można również dodać zachowanie do akcji niestandardowej przy użyciu kodu. Na przykład można dodać kod, który przyjmuje nazwy adresatów wiadomości e-mail i dodaje te nazwy jako uczestnicy nowego elementu terminu. W tym celu należy obsługiwać [Akcja niestandardowa](http://msdn.microsoft.com/library/office/ff862186.aspx) zdarzenie [MailItem obiektu](http://msdn.microsoft.com/library/office/ff861332.aspx).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Wskazówki: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  