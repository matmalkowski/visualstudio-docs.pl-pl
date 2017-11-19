---
title: "Tworzenie i konfigurowanie zestawów danych w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typed datasets, creating
- datasets [Visual Basic], creating
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 5dd27f35bdfd0ee2f576c1a4ac2fe3fde5a357e6
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Tworzenie i konfigurowanie zestawów danych w programie Visual Studio
A *dataset* jest zestaw obiektów, które przechowują dane z bazy danych w pamięci i obsługuje śledzenia zmian, aby włączyć tworzenia, odczytu, aktualizacji i usuwania (CRUD) operacje na danych bez konieczności być zawsze połączone z bazą danych. Zestawy danych zostały zaprojektowane do prosty *formularzy nad danymi* aplikacji biznesowych. Dla nowych aplikacji należy rozważyć użycie programu Entity Framework do przechowywania i model danych w pamięci. Aby pracować z zestawami danych, należy mieć podstawową wiedzę na temat pojęć bazy danych.  
  
 Można utworzyć typu <xref:System.Data.DataSet> klasy w Visual Studio w czasie projektowania przy użyciu **Kreator konfiguracji źródła danych**. Informacje o tworzeniu zestawów danych programowo, zobacz [Tworzenie zestawu danych](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).  
  
## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Utwórz nowy zestaw danych za pomocą Kreatora konfiguracji źródła danych  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj nowe źródło danych** uruchomić **Kreator konfiguracji źródła danych**.  
  
2.  Wybierz typ źródła danych, które będą łączyć się.  
  
     ![Kreator konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png "Kreator konfiguracji źródła danych")  
  
3.  W przypadku baz danych wybierz bazę danych lub bazy danych, które będą źródła danych dla zestawu danych.  
  
     ![Źródło danych wybierz połączenie](../data-tools/media/data-source-choose-a-connection.png "źródła danych, wybierz połączenie")  
  
4.  Wybierz tabele (lub poszczególnych kolumn), przechowywane procedury, funkcje i widoki z bazy danych, które mają być reprezentowane w zestawie danych.  
  
     ![Wybierz obiekty bazy danych](../data-tools/media/raddata-chose-objects.png "raddata wybranego obiektów")  
  
5.  Kliknij przycisk **Zakończ**.  
  
6.  Zestaw danych jest wyświetlany jako węzeł **Eksploratora rozwiązań**:  
  
     ![Zestaw danych w Eksploratorze rozwiązań](../data-tools/media/dataset-in-solution-explorer.png "zestawu danych w Eksploratorze rozwiązań")  
  
     Kliknij ten węzeł, a zestaw danych zostanie wyświetlony w **Projektant obiektów DataSet**. Należy pamiętać, że każdy tabeli w zestawie danych nie ma skojarzonego obiektu TableAdapter, która jest reprezentowana w dolnej części. Karta tabeli jest używany do wypełniania zestawu danych i opcjonalnie należy wysyłać polecenia do bazy danych.  
  
     ![Projektant obiektów DataSet](../data-tools/media/dataset-designer.png "Projektant obiektów DataSet")  
  
7.  Wiersze relacji połączonych tabel reprezentują relacje między tabelami, zgodnie z definicją w bazie danych. Domyślnie ograniczenia klucza obcego w bazie danych są reprezentowane jako relacji tylko przy użyciu aktualizacji i usuwania reguł wartość none. Zazwyczaj jest to czego chcesz. Jednak można kliknąć przycisk wiersze, aby wyświetlić **relacji** okna dialogowego, w którym można zmienić zachowanie hierarchicznej aktualizacji. Aby uzyskać więcej informacji, zobacz [relacje w zestawach danych](../data-tools/relationships-in-datasets.md) i [hierarchicznej aktualizacji](../data-tools/hierarchical-update.md).  
  
     ![Zestaw danych relacji w oknie dialogowym](../data-tools/media/raddata-relation-dialog.png "raddata relacji w oknie dialogowym")  
  
8.  Kliknij przycisk tabeli, karta tabeli lub nazwa kolumny w tabeli, aby wyświetlić jego właściwości w **właściwości** okna. Można zmodyfikować niektórych wartości w tym miejscu. Pamiętaj tylko modyfikujesz zestawu danych, nie źródłowej bazy danych.  
  
     ![Właściwości kolumny zestawu danych](../data-tools/media/dataset-column-properties.png "właściwości kolumny zestawu danych")  
  
9. Można dodać nowe tabele lub adaptery tabel do zestawu danych, lub Dodaj nowe kwerendy istniejących kart tabeli lub określić nowe relacje między tabelami, przeciągając elementy z **przybornika** kartę. Na tej karcie jest wyświetlane, gdy **Projektant obiektów DataSet** mającego fokus.  
  
     ![Zestaw danych przybornika](../data-tools/media/raddata-dataset-toolbox.png "raddata przybornika zestawu danych")  
  
10. Następnie prawdopodobnie chcesz określić sposób wypełnić zestaw danych z danymi. Do tego użyć **TableAdapter Kreator konfiguracji**. Aby uzyskać więcej informacji, zobacz [wypełnienia zestawów danych przy użyciu TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md) .  
  
## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Dodawanie tabeli bazy danych lub inny obiekt do istniejący zestaw danych  
 W tej procedurze pokazano, jak dodać tabelę z tej samej bazy danych, który został użyty do utworzenia zestawu danych.  
  
1.  Kliknij węzeł zestawu danych w **Eksploratora rozwiązań** do zapewnienia Projektanta obiektów dataset fokus.  
  
2.  Kliknij przycisk **źródeł danych** karcie na lewym marginesie programu Visual Studio, lub wprowadź `Data Sources` w **szybkiego uruchamiania**.  
  
3.  Kliknij prawym przyciskiem myszy węzeł zestawu danych i wybierz **Konfigurowanie źródła danych przy użyciu kreatora** .  
  
     ![Menu kontekstowe źródła danych](../data-tools/media/data-source-context-menu.png "menu kontekstowe źródła danych")  
  
4.  Użyj kreatora, aby określić, które dodatkowe tabele i procedury składowane lub innego obiektu bazy danych, aby dodać do zestawu danych.  
  
## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Dodaj tabelę danych autonomicznej do zestawu danych  
  
1.  Otwórz zestaw danych w **Projektant obiektów Dataset**.  
  
2.  Przeciągnij <xref:System.Data.DataTable> klasę z **DataSet** karcie **przybornika** na **Projektant obiektów Dataset**.  
  
3.  Dodawanie kolumn do definiowania tabeli danych. Kliknij prawym przyciskiem myszy w tabeli, a następnie wybierz pozycję **Dodaj > kolumny**. Użyj **właściwości** okno, aby ustawić typ danych kolumny i klucz, jeśli to konieczne.  
  
4.  Tabele autonomicznej konieczne wdrożenie `Fill` logikę w tabelach autonomicznej tak, aby wypełnić je danymi. Uzyskać informacji o Wypełnianie tabel danych autonomicznych, zobacz [wypełnianie zestawu danych z element DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Zobacz także
[Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)