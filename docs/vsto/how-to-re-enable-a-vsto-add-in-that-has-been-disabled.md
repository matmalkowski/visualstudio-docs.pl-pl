---
title: "Porady: ponowne włączanie dodatku narzędzi VSTO, która została wyłączona | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.Warning.DisabledAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disabled add-ins
- add-ins [Office development in Visual Studio], disabled
- add-ins [Office development in Visual Studio], enabling
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: c2f86906db578987ec81e35aa8c49abd62b5e88f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-re-enable-a-vsto-add-in-that-has-been-disabled"></a>Porady: ponowne włączanie wcześniej wyłączonego dodatku narzędzi VSTO
  Aplikacje Microsoft Office może spowodować wyłączenie dodatków VSTO, które nieoczekiwane zachowanie. Jeśli aplikacja nie zostanie załadowany dodatek VSTO przy próbie jego debugowania, aplikacji mogą mieć twarde wyłączone lub nietrwałego wyłączone użytkownika dodatku VSTO.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="hard-disabled-vsto-add-ins"></a>Dodatków VSTO twardych wyłączone  
 Wyłączenie ciężko może wystąpić, gdy dodatku VSTO powoduje, że aplikacja jest nieoczekiwanie zamykany. Go może również wystąpić na komputerze deweloperskim po zatrzymaniu debugera podczas <xref:Microsoft.Office.Tools.AddIn.Startup> wykonuje program obsługi zdarzeń w Twojej dodatku VSTO.  
  
#### <a name="to-re-enable-a-vsto-add-in"></a>Aby ponownie włączyć dodatku narzędzi VSTO  
  
1.  W aplikacji, kliknij przycisk **pliku** kartę.  
  
2.  Kliknij przycisk *ApplicationName* **opcje** przycisku.  
  
3.  W okienku kategorii kliknij **dodatki**.  
  
4.  W okienku szczegółów, sprawdź, czy dodatku VSTO jest wyświetlany w **aplikacji wyłączone dodatki** listy.  
  
     **Nazwa** kolumna określa nazwę zestawu, a **lokalizacji** kolumna określa pełną ścieżkę manifestu aplikacji.  
  
5.  W **Zarządzaj** kliknij **elementy wyłączone**, a następnie kliknij przycisk **Przejdź**.  
  
6.  Wybierz dodatku VSTO i kliknij przycisk **włączyć**.  
  
7.  Kliknij przycisk **Zamknij**.  
  
## <a name="soft-disabled-vsto-add-ins"></a>Dodatków VSTO soft wyłączone  
 Wyłączanie nietrwałego może wystąpić, gdy dodatku VSTO generuje błąd, który nie powoduje nieoczekiwanego zamknięcia aplikacji. Na przykład aplikacji soft może wyłączyć dodatku VSTO, jeśli zgłasza nieobsługiwany wyjątek podczas <xref:Microsoft.Office.Tools.AddIn.Startup> program obsługi zdarzeń jest wykonywany.  
  
> [!NOTE]  
>  Po ponownym włączeniu dodatku VSTO soft wyłączone aplikacji natychmiast próbuje załadować dodatku VSTO. Jeśli nie został rozwiązany problem początkowo powodujący aplikacji do wyłączenia nietrwałego dodatku VSTO, aplikacja będzie soft wyłączyć dodatku VSTO ponownie.  
  
#### <a name="to-re-enable-an-vsto-add-in"></a>Aby ponownie włączyć dodatku narzędzi VSTO  
  
1.  W aplikacji, kliknij przycisk **pliku** kartę.  
  
2.  Kliknij przycisk *ApplicationName* **opcje** przycisku.  
  
3.  W okienku kategorii kliknij **dodatki**.  
  
4.  W okienku szczegółów, sprawdź, czy dodatku VSTO jest wyświetlany w **dodatki aplikacji nieaktywne** listy.  
  
     **Nazwa** kolumna określa nazwę zestawu, a **lokalizacji** kolumna określa pełną ścieżkę manifestu aplikacji.  
  
5.  W **Zarządzaj** kliknij **dodatki COM**, a następnie kliknij przycisk **Przejdź**.  
  
6.  W **dodatki COM** okno dialogowe, zaznacz pole wyboru obok wyłączonego dodatku VSTO.  
  
7.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowanie rozwiązań pakietu Office](../vsto/building-office-solutions.md)   
 [Debugowanie projektów pakietu Office](../vsto/debugging-office-projects.md)   
 [Programowanie dodatków VSTO](../vsto/programming-vsto-add-ins.md)  
  
  