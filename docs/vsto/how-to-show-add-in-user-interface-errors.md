---
title: "Porady: Pokaż błędy interfejsu użytkownika dodatku | Dokumentacja firmy Microsoft"
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
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
ms.assetid: aa82cc04-e616-4501-940c-79d11fb393cc
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3b483889dbd970b2225c773e6dd43b9333b0d8a5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Porady: pokazywanie błędów dodatków interfejsu użytkownika
  Domyślnie jeśli dodatku VSTO podejmie próbę manipulowania Microsoft Office interfejsu użytkownika (UI) i kończy się niepowodzeniem, żaden komunikat o błędzie jest wyświetlany. Można jednak skonfigurować aplikacje Microsoft Office, aby wyświetlić komunikaty o błędach dla błędów, które odnoszą się do interfejsu użytkownika. Te komunikaty umożliwia pomagają w ustaleniu, dlaczego nie ma niestandardowa Wstążka, lub też dlaczego wstążki jest wyświetlana, ale żadne formanty nie są wyświetlane.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-show-vsto-add-in-user-interface-errors"></a>Aby wyświetlić błędy interfejsu użytkownika w dodatku VSTO  
  
1.  Uruchom aplikację.  
  
2.  Kliknij przycisk **pliku** kartę.  
  
3.  Kliknij przycisk **opcje**.  
  
4.  W okienku kategorii kliknij **zaawansowane**.  
  
5.  W okienku szczegółów wybierz **dodatku VSTO Pokaż błędy interfejsu użytkownika**, a następnie kliknij przycisk **OK**.  
  
    > [!NOTE]  
    >  Dla programu Outlook **dodatku VSTO Pokaż błędy interfejsu użytkownika** wyboru znajduje się w **Developer** sekcji okienka szczegółów. Dla innych aplikacji, pole wyboru znajduje się w **ogólne** sekcji okienka szczegółów.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Wstążka ― omówienie](../vsto/ribbon-overview.md)   
 [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)  
  
  