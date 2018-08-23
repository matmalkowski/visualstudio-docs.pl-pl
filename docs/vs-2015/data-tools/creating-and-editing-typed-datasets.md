---
title: Tworzenie i edytowanie zestawów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner
- vs.data.adddataset
dev_langs:
- VB
- CSharp
- C++
- aspx
- aspx
helpviewer_keywords:
- datasets [Visual Basic], visual designer
- data [Visual Studio], Dataset Designer
- Dataset Designer
ms.assetid: cd0dbe93-be9b-41e4-bc39-e9300678c1f2
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 0147a114dff7144116e52f6fabe72f92e0885c4f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681885"
---
# <a name="creating-and-editing-typed-datasets"></a>Tworzenie i edytowanie wpisanych zestawów danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Projektanta obiektów Dataset** to zestaw narzędzi wizualnych, których można tworzyć i edytować typizowane zestawy danych i pojedynczych elementów, które zawierają.  
  
 **Projektanta obiektów Dataset** zapewnia wizualne reprezentacje obiektów znajdujących się w typizowanych zestawów danych. Tworzenie i modyfikowanie [TableAdapters](../data-tools/tableadapter-overview.md), [zapytań TableAdapter](../data-tools/how-to-create-tableadapter-queries.md), <xref:System.Data.DataTable>s, <xref:System.Data.DataColumn>s, i <xref:System.Data.DataRelation>s **Projektanta obiektów Dataset**.  
  
 Aby otworzyć **Projektanta obiektów Dataset**, kliknij dwukrotnie zestaw danych w **Eksploratora rozwiązań**, lub kliknij prawym przyciskiem myszy zestaw danych w **źródeł danych** oknie i kliknij przycisk **edycji Zestaw danych za pomocą projektanta**. Aby uzyskać więcej informacji, zobacz [porady: otwieranie zestawu w Projektancie obiektów Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3). Dodawanie nowego <xref:System.Data.DataSet> element o **Dodaj nowy element** zostanie otwarte okno dialogowe **Projektanta obiektów Dataset** z pustego zestawu danych w gotowe do edycji.  
  
> [!NOTE]
>  **Projektanta obiektów Dataset** może służyć do rozszerzanie funkcjonalności zestawu danych. Kliknij dwukrotnie na powierzchnię projektową lub kliknij prawym przyciskiem myszy i wybierz pozycję **Wyświetl kod** można utworzyć pliku częściowej klasy, gdzie możesz dodać kod do zestawu danych, który nie będzie można zmienić ani usunąć przez projektanta. Aby uzyskać informacje na rozszerzanie funkcjonalności TableAdapter, zobacz [rozszerzanie funkcjonalności TableAdapter](../data-tools/extend-the-functionality-of-a-tableadapter.md).  
  
 Poniższa tabela zawiera listę typowych zadań, które można wykonać przy użyciu **Projektanta obiektów Dataset**.  
  
|Zadanie|Zobacz|  
|--------|---------|  
|Utworzyć obiekt TableAdapter|[Tworzenie i konfigurowanie adapterów TableAdapter](../data-tools/create-and-configure-tableadapters.md)|  
|Edytuj TableAdapter|[Porady: edytowanie TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855)|  
|Tworzenie zapytań TableAdapter|[Porady: tworzenie zapytań TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)|  
|Edytowanie zapytań TableAdapter|[Porady: edytowanie zapytań TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)|  
|Utwórz <xref:System.Data.DataTable>|[Porady: Tworzenie tabel danych](../data-tools/how-to-create-data-tables.md)|  
|Edytuj <xref:System.Data.DataTable>|[Projektowanie DataTables](../data-tools/designing-datatables.md)|  
|Utwórz <xref:System.Data.DataColumn>|[Porady: Dodawanie kolumn do DataTable](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)|  
|Utwórz relację między dwiema <xref:System.Data.DataTable>s|[Porady: tworzenie DataRelations przy użyciu Projektanta obiektów Dataset](http://msdn.microsoft.com/library/a3ab4803-0b50-4b74-9920-ab20bfbf1aa2)|  
|Rozszerzanie funkcjonalności zestawu danych|[Porady: rozszerzanie funkcjonalności zestawu danych](http://msdn.microsoft.com/library/dfbc21eb-7ea2-4942-addd-49677f5493be)|  
|Dodawanie walidacji do tabeli danych <xref:System.Data.DataTable.ColumnChanging> zdarzeń|[Porady: Sprawdzanie poprawności danych podczas zmiany kolumn](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5)|  
|Dodawanie walidacji do tabeli danych <xref:System.Data.DataTable.RowChanging> zdarzeń|[Porady: Sprawdzanie poprawności danych podczas przeprowadzania zmian w wierszach](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc)|  
  
## <a name="creating-objects-on-the-design-surface"></a>Tworzenie obiektów na powierzchni projektowej  
 Zestawy danych można utworzyć, dodawania i edytowania pojedyncze obiekty, które tworzą zestaw danych. Poniższa tabela zawiera omówienie różnych obiektów w **DataSet** karcie **przybornika** mogą być przeciągnięte na powierzchnię projektu:  
  
|Obiekt|Opis|  
|------------|-----------------|  
|TableAdapter|Zawiera kolekcję danych poleceń i połączenia danych, które są używane do komunikowania się z podstawowej bazy danych i Wypełnij tabelę danych. Aby uzyskać więcej informacji, zobacz [TableAdapter — Przegląd](../data-tools/tableadapter-overview.md) i [tworzenie i konfigurowanie adapterów TableAdapter](../data-tools/create-and-configure-tableadapters.md).|  
|Zapytanie|Zapytania TableAdapter są silnie typizowane metody, które wykonania instrukcji SQL i procedur składowanych. Uruchamianie zapytania TableAdapter wypełnia tabelę danych z danymi lub wykonywania innych zadań bazy danych. Aby uzyskać więcej informacji, zobacz [porady: tworzenie zapytań TableAdapter](../data-tools/how-to-create-tableadapter-queries.md). Przeciąganie zapytanie na tabeli dodaje zapytanie do tej tabeli, natomiast przeciągając zapytanie na pusty obszar **Projektanta obiektów Dataset** tworzy zapytania globalnego. Aby uzyskać więcej informacji, zobacz [porady: dodawanie zapytań globalnych do TableAdapter](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).|  
|<xref:System.Data.DataTable>|Reprezentuje kolekcję wierszy zwrócony z bazy danych w pamięci.|  
|Relacja (<xref:System.Data.DataRelation>)|Reprezentuje relację nadrzędny podrzędny między dwoma <xref:System.Data.DataTable>s. Aby uzyskać więcej informacji, zobacz [wprowadzenie do obiektów DataRelation](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192) i [wskazówki: tworzenie relacji między tabelami danych](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82).|  
  
> [!NOTE]
>  **Projektanta obiektów Dataset** nawiązanie połączenia z podstawowej bazy danych tylko wtedy, gdy zestaw danych jest tworzony; Projektant nie wykryje automatycznie kolejne zmiany w bazie danych. Aby odświeżyć istniejący XSD, uruchom ponownie **Kreatora konfiguracji**. Jeśli relacje tabel zostały zmienione, Usuń i ponownie dodać tabele do XSD.  
  
## <a name="linq-to-dataset"></a>LINQ to Dataset  
 [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] Włącza [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) nad danymi w <xref:System.Data.DataSet> obiektu. Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie zestawu danych za pomocą Projektanta obiektów Dataset](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)   
 [Wskazówki: Tworzenie TableAdapter z wieloma zapytaniami](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)   
 [Wskazówki: Tworzenie DataTable w Projektancie obiektów Dataset](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)   
 [Wskazówki: Tworzenie relacji pomiędzy tabelami danych](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82)   
 [Wskazówki: Wyświetlanie danych w formularzu Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Okno źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Przygotowanie aplikacji na odbieranie danych](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Pobieranie danych do aplikacji](../data-tools/fetching-data-into-your-application.md)   
 [Edytowanie danych w aplikacji](../data-tools/editing-data-in-your-application.md)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Zapisywanie danych](../data-tools/saving-data.md)