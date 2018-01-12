---
title: 'Porady: dodawanie regionu formularza na projekt dodatku programu Outlook | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSTO.NewFormRegionWizard.Page1
- VSTO.NewFormRegionWizard.Page3
- VSTO.NewFormRegionWizard.Page2
- VSTO.NewFormRegionWizard.Page0
dev_langs:
- VB
- CSharp
helpviewer_keywords: form regions [Office development in Visual Studio], adding
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2029b154ca97f2e856a9e6af8ef58b82f4438df6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-form-region-to-an-outlook-add-in-project"></a>Porady: dodawanie regionu formularza do projektu dodatków w programie Outlook
  Utwórz region formularza, aby rozszerzyć za pomocą standardowych lub niestandardowych formularzy programu Microsoft Office Outlook **nowych regionów formularzy programu Outlook** kreatora. Można utworzyć nowego regionu formularza i projektowanie interfejsu użytkownika w programie Visual Studio lub mogą być importowane regionu formularza, który został zaprojektowany w programie Outlook i Dodaj kod Visual Basic lub C#.  
  
 Jeśli masz regionów formularzy programu Outlook, który został użyty w innym projekcie programu Outlook, może używać go w bieżącym projekcie dodatku narzędzi VSTO programu Outlook przy użyciu **Dodaj istniejący element** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### <a name="to-add-a-new-form-region-to-an-outlook-project"></a>Aby dodać nowy regionu formularza do projektu programu Outlook  
  
1.  Otwarcia lub utworzenia projektów dodatku VSTO dla programu Outlook w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  W **Eksploratora rozwiązań**, wybierz węzeł projektów dodatku VSTO dla programu Outlook.  
  
3.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
4.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **regionów formularzy programu Outlook**.  
  
5.  Wpisz nazwę do regionu formularza w **nazwa** , a następnie kliknij przycisk **Dodaj**.  
  
     **Regionu formularza NewOutlook** zostanie uruchomiony Kreator.  
  
6.  Na **wybierz jak chcesz utworzyć regionu formularza** wybierz, czy ma być projektowanie regionów formularzy przy przeciągania zarządzane formanty do projektanta wizualnego lub importowanie regionów formularzy, który został zaprojektowany w programie Outlook.  
  
    > [!NOTE]  
    >  Jeśli chcesz zaimportować regionu formularza, który został zaprojektowany w programie Outlook, należy określić lokalizację pliku magazynu formularzy programu Outlook (.ofs). Nie można dodać zarządzane formanty do regionu formularza, który projekt w programie Outlook; można dodawać tylko kod związany z istniejącego interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md).  
  
7.  Na **wybierz typ regionu formularza, którego chcesz utworzyć** , przejrzyj typów regionu formularza i wybierz jedną, a następnie kliknij przycisk **dalej**. Aby uzyskać więcej informacji na temat typów regionu formularza, zobacz [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md).  
  
8.  Na **Podaj opis, a następnie wybierz preferencje wyświetlania** strony w **nazwa** wpisz nazwę do regionu formularza. Zastąpienie i typów regionu formularza Zamień wszystkie **tytuł** i **opis** pola są również dostępne.  
  
     Informacje o którym nazwę, tytuł i opis są wyświetlane w programie Outlook podczas wdrażania regionu formularza, zobacz [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md).  
  
9. Wybierz co najmniej jeden tryb wyświetlania, w których chcesz regionu formularza i pojawienie się.  
  
     Wszystkie typy regionu formularza może występować w inspektorzy, tworzą trybu (do tworzenia elementów) i w trybie do odczytu (w przypadku wyświetlania elementów). Sąsiadujące, zastąpienia i typów regionu formularza Zamień wszystkie można również wyświetlane w okienku odczytu.  
  
10. Kliknij przycisk **Dalej**.  
  
11. Na **zidentyfikować klasy wiadomości, które spowoduje wyświetlenie tego regionu formularza** , wybierz standardowe klasy wiadomości programu Outlook lub wpisz nazwy co najmniej jedną klasę niestandardowy komunikat, a następnie kliknij przycisk **Zakończ**. Aby uzyskać więcej informacji, zobacz [kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do regionów formularzy w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)   
 [Rozwiązania programu Outlook](../vsto/outlook-solutions.md)   
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Wytyczne dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Wskazówki: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Wskazówki: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Niestandardowe akcje w regionach formularzy programu Outlook](../vsto/custom-actions-in-outlook-form-regions.md)  
  
  