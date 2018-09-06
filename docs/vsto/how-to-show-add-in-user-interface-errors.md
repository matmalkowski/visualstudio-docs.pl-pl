---
title: 'Porady: dodatek Pokaż błędy interfejsu użytkownika'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dd6da0c83d0dee835169a0a8068af8d75facbbd4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677172"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Porady: dodatek Pokaż błędy interfejsu użytkownika
  Domyślnie jeśli dodatku narzędzi VSTO prób do manipulowania Microsoft Office interfejsu użytkownika (UI) i kończy się niepowodzeniem, żaden komunikat o błędzie jest wyświetlany. Można jednak skonfigurować aplikacje Microsoft Office, aby wyświetlić komunikaty błędów, które odnoszą się do interfejsu użytkownika. Te komunikaty można użyć w celu określenia, dlaczego niestandardowa Wstążka jest niewidoczny, lub dlaczego Wstążka pojawia się, ale nie formanty są wyświetlane.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="to-show-vsto-add-in-user-interface-errors"></a>Aby wyświetlić błędy interfejsu użytkownika dodatku narzędzi VSTO  
  
1.  Uruchom aplikację.  
  
2.  Kliknij przycisk **pliku** kartę.  
  
3.  Kliknij przycisk **opcje**.  
  
4.  W okienku kategorii kliknij **zaawansowane**.  
  
5.  W okienku szczegółów wybierz **błędów interfejsu użytkownika dodatku narzędzi VSTO dla programów Pokaż**, a następnie kliknij przycisk **OK**.  
  
    > [!NOTE]  
    >  Dla programu Outlook **błędów interfejsu użytkownika dodatku narzędzi VSTO dla programów Pokaż** pole wyboru znajduje się w **Developer** części okienka szczegółów. Dla innych aplikacji, pole wyboru znajduje się w **ogólne** części okienka szczegółów.  
  
## <a name="see-also"></a>Zobacz także  
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Wstążka — omówienie](../vsto/ribbon-overview.md)   
 [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)  
  
  