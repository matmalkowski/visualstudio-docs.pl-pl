---
title: 'Porady: tworzenie zapytań TableAdapter | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, creating queries
- queries [Visual Studio], creating
- data [Visual Studio], TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f7d4bd84d5cd4538d06048fd6953fa95fc344da0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677183"
---
# <a name="how-to-create-tableadapter-queries"></a>Porady: tworzenie zapytań TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zapytań TableAdapter są instrukcji SQL lub procedur składowanych, które aplikacji mogą być wykonywane względem bazy danych.  
  
 Dodaj jako wiele zapytań do TableAdapter jako wymaganych przez aplikację. Zapytań TableAdapter są traktowane jako metody TableAdapter. Po utworzeniu zapytania o nazwie `FillByCity` przyjmującą parametr reprezentujący wartość miejscowości, zapytanie jest dodawany do TableAdapter. Zostanie dodany jako typizowane metody, która przyjmuje poprawny typ parametru jako argument — w tym przypadku ciąg reprezentujący wartość miejscowości. Zapytania TableAdapter, podobnie jak każda metoda jest wywoływana dla dowolnego obiektu. Na przykład, poniższy kod wykonuje `FillByCity` zapytania i wypełnienia `Customers` tabeli wszystkich klientów o wartości city `Seattle`:  
  
 [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
 [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
 Zapytań TableAdapter można wypełnić tabelę danych (`Fill` i `FillBy` zapytań) lub je zwracają nowe tabele danych zawierają dane zwracane przez zapytanie (`GetData` i `GetDataBy` zapytań).  
  
 Możesz dodawać zapytania do istniejących metod TableAdapter, uruchamiając [edytowanie TableAdapters](../data-tools/editing-tableadapters.md). (Kliknij prawym przyciskiem myszy dowolnego TableAdapter, a następnie wybierz **Dodaj zapytanie**.)  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="create-a-query-in-the-dataset-designer"></a>Utwórz zapytanie w Projektancie obiektów Dataset  
  
#### <a name="to-add-a-query-to-a-tableadapter-in-the-dataset-designer"></a>Aby dodać zapytanie do TableAdapter w Projektancie obiektów Dataset  
  
1.  Otwórz zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [porady: otwieranie zestawu w Projektancie obiektów Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Kliknij prawym przyciskiem myszy żądany obiekt TableAdapter, a następnie wybierz pozycję **Dodaj zapytanie**.  
  
     —lub—  
  
3.  Przeciągnij **zapytania** z **DataSet** karcie **przybornika** do tabeli w projektancie.  
  
     **Kreatora konfiguracji zapytania TableAdapter** zostanie otwarty.  
  
4.  Ukończ pracę kreatora; Zapytanie jest dodawany do TableAdapter.  
  
## <a name="create-a-query-directly-on-a-form-in-your-windows-application"></a>Utwórz zapytanie bezpośrednio na formularzu w aplikacji Windows  
 Jeśli utworzono wystąpienie TableAdapter w formularzu można dodać zapytania za pomocą [kompilator kryteriów wyszukiwania — okno dialogowe](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d), która dodaje <xref:System.Windows.Forms.ToolStrip> formantu do formularza, który akceptuje danych wejściowych parametrów dla kwerendy, a także przycisk, aby uruchomić zapytanie.  
  
#### <a name="to-add-a-query-to-a-tableadapter-using-the-search-criteria-dialog-box"></a>Aby dodać zapytanie do TableAdapter za pomocą okna dialogowego kryteria wyszukiwania  
  
1.  Wybierz TableAdapter w zasobniku składnika.  
  
2.  Kliknij tag inteligentny TableAdapter, a następnie wybierz **Dodaj zapytanie**.  
  
3.  Wypełnij okno dialogowe, a zapytanie jest dodawany do TableAdapter. Aby uzyskać więcej informacji, zobacz [kompilator kryteriów wyszukiwania — okno dialogowe](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d).  
  
## <a name="see-also"></a>Zobacz też  
 [TableAdapter — Przegląd](../data-tools/tableadapter-overview.md)   
 [Porady: edytowanie zapytań TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Tworzenie i edytowanie wpisanych zestawów danych](../data-tools/creating-and-editing-typed-datasets.md)   
 [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)   
 [Porady: łączenie z danymi w bazie danych](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Porady: nawigowanie po danych za pomocą kontrolki BindingNavigator formularzy Windows Forms](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [Wskazówki: Wyświetlanie danych w formularzu Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Wskazówki: Tworzenie TableAdapter z wieloma zapytaniami](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)