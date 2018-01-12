---
title: "Porady: mapowanie schematów z dokumentami programu Word w Visual Studio | Dokumentacja firmy Microsoft"
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
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 65ecd3adbeb6f554a901345c2fa5dbf8359a1428
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Porady: mapowanie schematów z dokumentami programu Word w programie Visual Studio
  **Ważne** informacji zawartych w tym temacie dotyczące programu Microsoft Word jest przedstawioną wyłącznie do korzyści i użyj osób i organizacji, które znajdują się poza Stanami Zjednoczonymi i jego terytoriów lub używający lub tworzenie programy, które działają na, produktów Microsoft Word, które są licencjonowane przez firmę Microsoft przed 2010 stycznia, po usunięciu implementację funkcji określonej przez Microsoft związane z niestandardowy plik XML z programu Microsoft Word. Te informacje dotyczące programu Microsoft Word może nie być odczytywane lub używane przez osoby lub organizacji w Stanach Zjednoczonych lub w jego terytoriów użytkowników przy użyciu lub tworzenie programów uruchamianych na produktów Microsoft Word, które są licencjonowane przez firmę Microsoft po 10 stycznia 2010 ; te produkty nie będzie działać taka sama jak produktów licencjonowanych przed tą datą lub zakupione i licencję na korzystanie z niego poza Stanami Zjednoczonymi.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Schemat XML można mapować do dokumentu, dokument jest otwarty w programie Visual Studio. Możesz użyć tego samego narzędzi Microsoft Office Word używanych podczas dokument jest otwarty poza Visual Studio. Office project tworzy obiekty tej samej, czy należy mapować schematu przed lub po utworzeniu rozwiązania programu Word.  
  
### <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Aby mapować schematu XML do dokumentu programu Word w Visual Studio  
  
1.  Otwórz projekt dokumentu lub szablonu programu Word w programie Visual Studio.  
  
2.  Kliknij w dokumencie, aby przejść do projektanta.  
  
3.  Na wstążce kliknij **Developer** kartę.  
  
    > [!NOTE]  
    >  Jeśli **Developer** karta nie jest widoczna, należy go najpierw wyświetlić. Aby uzyskać więcej informacji, zobacz [porady: pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  W **XML** kliknij przycisk **schematu**.  
  
     **Szablony i dodatki** zostanie otwarte okno dialogowe.  
  
5.  Kliknij przycisk **schematu XML** kartę.  
  
6.  Kliknij przycisk **dodać schematu**.  
  
     **Dodaj schemat** zostanie otwarte okno dialogowe.  
  
7.  Przejdź do pliku schematu, zaznacz go, a następnie kliknij przycisk **Otwórz**.  
  
     **Schemat ustawień** zostanie otwarte okno dialogowe.  
  
8.  Przypisz aliasu lub kliknij przycisk **OK** można dodać schematu bez aliasu.  
  
9. Kliknij przycisk **OK**.  
  
     **Struktury XML** zostanie otwarte okno.  
  
10. Przeciągnij elementy z **struktury XML** okna do miejsca w dokumencie miejscu odpowiedniego służy do utworzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: mapowanie schematów z arkuszami w programie Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Schematy XML i dane dostosowywane na poziomie dokumentu](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  