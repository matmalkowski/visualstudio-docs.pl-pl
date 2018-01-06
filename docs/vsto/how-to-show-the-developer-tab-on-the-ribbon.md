---
title: "Porady: pokazywanie karty dewelopera na Wstążce | Dokumentacja firmy Microsoft"
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
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
ms.assetid: ce7cb641-44f2-4a40-867e-a7d88f8e98a9
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3885ce387aa27857e59fb3af74990d953c047225
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Porady: pokazywanie karty dewelopera na wstążce
  Aby uzyskać dostęp do **Developer** kartę na Wstążce aplikacji pakietu Office, musisz skonfigurować go do wyświetlenia tej karty, ponieważ nie jest wyświetlane domyślnie. Na przykład konieczne jest wyświetlenie danej karcie Jeśli chcesz dodać <xref:Microsoft.Office.Tools.Word.GroupContentControl> na dostosowanie poziomie dokumentu dla programu Word.  
  
> [!NOTE]  
>  Niniejsze wytyczne mają zastosowanie do pakietu Office 2010 lub nowszej tylko aplikacji. Jeśli chcesz, aby było wyświetlane na tej karcie w pakietu Microsoft Office 2007, zobacz następującą wersję tego tematu [porady: pokazywanie karty dewelopera na wstążce](http://msdn.microsoft.com/library/bb608625(v=vs.90).aspx).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Nie ma dostępu do **Developer** kartę.  
  
### <a name="to-show-the-developer-tab"></a>Na pokazywanie karty dewelopera  
  
1.  Uruchom dowolne z aplikacji pakietu Office, obsługiwane w tym temacie. Zobacz **ma zastosowanie do:** Uwaga wcześniej w tym temacie.  
  
2.  Na **pliku** , wybierz pozycję **opcje** przycisku.  
  
     Poniższy rysunek pokazuje **pliku** kartę i **opcje** przycisk w pakiecie Office 2010.  
  
     ![Wybieranie pliku, opcje w programie Outlook 2010](../vsto/media/vsto-office-file-tab.png "opcje wybierania plików, w programie Outlook 2010")  
  
     Poniższy rysunek pokazuje **pliku** kartę w pakietu Office 2013.  
  
     ![Karta plików w programie Outlook 2013](../vsto/media/vsto-office2013-filetab.png "kartę Plik w programie Outlook 2013")  
  
     Poniższy rysunek pokazuje **opcje** przycisk Office 2013.  
  
     ![Przycisk Opcje w programie Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "przycisk Opcje w programie Outlook 2013 Preview")  
  
3.  W *ApplicationName***opcje** oknie dialogowym wybierz **Dostosowywanie wstążki** przycisku.  
  
     Poniższy rysunek pokazuje **opcje** okno dialogowe i **Dostosowywanie wstążki** przycisku w programie Excel 2010. Lokalizacja ten przycisk jest podobna wszystkie inne aplikacje wymienione w sekcji "Dotyczy" u góry tego tematu.  
  
     ![Dostosowywanie Wstążki przycisk](../vsto/media/vsto-office2010-customizeribbonbutton.png "przycisk Dostosowywanie Wstążki")  
  
4.  Na liście głównych kart, wybierz **Developer** pole wyboru.  
  
     Poniższy rysunek pokazuje **Developer** pole wyboru w programie Word 2010 i [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. Lokalizacja to pole wyboru jest podobna wszystkie inne aplikacje wymienione w sekcji "Dotyczy" u góry tego tematu.  
  
     ![Pole wyboru deweloperów w oknie dialogowym Opcje programu Word](../vsto/media/vsto-office2010-developercheckbox.png "Deweloper pole wyboru w oknie dialogowym Opcje programu Word")  
  
5.  Wybierz **OK** przycisk, aby zamknąć **opcje** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)  
  
  