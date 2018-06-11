---
title: 'Porady: dodawanie formantów XMLNodes do dokumentów programu Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ff7a1966c9107fcd2a60b14c21b6a2dfbda09033
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258073"
---
# <a name="how-to-add-xmlnodes-controls-to-word-documents"></a>Porady: dodawanie formantów XMLNodes do dokumentów programu Word
  **Ważne** informacji zawartych w tym temacie dotyczące programu Microsoft Word jest przedstawioną wyłącznie do korzyści i użyj osób i organizacji, które znajdują się poza Stanami Zjednoczonymi i jego terytoriów lub używający lub tworzenie programy, które działają na, produktów Microsoft Word, które są licencjonowane przez firmę Microsoft przed 2010 stycznia, po usunięciu implementację funkcji określonej przez Microsoft związane z niestandardowy plik XML z programu Microsoft Word. Te informacje dotyczące programu Microsoft Word może nie być odczytywane lub używane przez osoby lub organizacji w Stanach Zjednoczonych lub w jego terytoriów użytkowników przy użyciu lub tworzenie programów uruchamianych na produktów Microsoft Word, które są licencjonowane przez firmę Microsoft po 10 stycznia 2010 ; te produkty nie będzie działać taka sama jak produktów licencjonowanych przed tą datą lub zakupione i licencję na korzystanie z niego poza Stanami Zjednoczonymi.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Podczas mapowania powtarzający się element schematu XML do dokumentu programu Microsoft Office Word, Visual Studio automatycznie dodaje <xref:Microsoft.Office.Tools.Word.XMLNodes> formantu do dokumentu.  
  
 Aby uzyskać informacje o mapowaniu niepowtarzającymi elementów schematu XML, zobacz [porady: XMLNode Dodaj formanty do dokumentów programu Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.XMLNodes> Formant nie jest dostępny z **przybornika** lub **źródeł danych** okna, ani nie może być utworzone programowo.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnodes-control-to-a-document"></a>Aby dodać formant XMLNodes do dokumentu  
  
1.  W dokumencie w projektancie programu Visual Studio na wstążce kliknij **Developer** kartę.  
  
    > [!NOTE]  
    >  Jeśli **Developer** karta nie jest widoczna, należy go najpierw wyświetlić. Aby uzyskać więcej informacji, zobacz [porady: pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  W **XML** kliknij przycisk **schematu**.  
  
     **Szablony i dodatki** zostanie otwarte okno dialogowe.  
  
3.  Kliknij przycisk **schematu XML** kartę.  
  
4.  Kliknij przycisk **dodać schematu**.  
  
     **Dodaj schemat** zostanie otwarte okno dialogowe.  
  
5.  Wybierz opcję schematu XML, który zawiera powtarzające się elementy schematu i kliknij przycisk **Otwórz**.  
  
     **Schemat ustawień** zostanie wyświetlone okno dialogowe.  
  
6.  Przypisz aliasu lub kliknij przycisk **OK** można dodać schematu bez aliasu.  
  
     Schemat jest dodawany do **Dodaj schemat** okno dialogowe.  
  
7.  W **Dodaj schemat** okno dialogowe, kliknij przycisk **OK**.  
  
     **Struktury XML** otwiera w okienku zadań.  
  
8.  Kliknij element schematu identycznych **struktury XML** okienka zadań, aby dodać go do dokumentu.  
  
     <xref:Microsoft.Office.Tools.Word.XMLNodes> Kontroli jest tworzony i dodawany do projektu.  
  
## <a name="see-also"></a>Zobacz także  
 [Formant XMLNodes](../vsto/xmlnodes-control.md)   
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Obiekty hosta i informacje o formantach hosta](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i formantów hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  