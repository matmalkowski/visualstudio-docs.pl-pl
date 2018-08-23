---
title: 'Porady: Tworzenie tabel danych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VSDesigner.DataSource.DesignTable
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], creating data tables
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
ms.assetid: 0e8bf4c4-3d05-4b20-9926-9d29914b26ed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 596c2760e100bc45eefdde10743b3d9b45490b91
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42691558"
---
# <a name="how-to-create-data-tables"></a>Porady: tworzenie tabel danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dane mogą być przechowywane w pamięci w <xref:System.Data.DataTable> obiektów. (Zestawy danych są tworzone przez <xref:System.Data.DataTable> obiektów.) Zazwyczaj tworzenie nowych tabel danych przy użyciu TableAdapters [Kreator konfiguracji TableAdapter](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8) lub poprzez przeciąganie obiektów bazy danych z **Eksploratora serwera** na **Projektanta obiektów Dataset** .  
  
 Tabele danych są tworzone jako byproduct, podczas tworzenia nowych elementów TableAdapter w [Kreatora konfiguracji źródła danych](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) tak dobrze, ale także mogą być tworzone niezależnie. Tworzenie tabeli danych z autonomicznych, przeciągając <xref:System.Data.DataTable> obiektu z **zestawu danych** karcie **przybornika** na **Projektanta obiektów Dataset**.  
  
> [!NOTE]
>  Aby programowo utworzyć tabele danych, zobacz [Tworzenie elementu DataTable](http://msdn.microsoft.com/library/eecf9d78-60e3-4fdc-8de0-e56c13a89414).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datatable-with-tableadapter"></a>Tworzenie elementu DataTable za pomocą TableAdapter  
 Tabele danych z TableAdapters to metody, które wypełnić tabelę z danymi i zapisania zmiany z powrotem do bazy danych. Tworzenie TableAdapters, uruchamiając **Kreator konfiguracji TableAdapter** lub poprzez przeciąganie obiektów bazy danych z **Eksploratora serwera** na **Projektanta obiektów Dataset**.  
  
#### <a name="to-create-a-new-data-table-with-tableadapter"></a>Aby utworzyć nową tabelę danych za pomocą TableAdapter  
  
1.  Otwórz swój zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać informacje, zobacz [porady: otwieranie zestawu w Projektancie obiektów Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Przeciągnij **TableAdapter** z **DataSet** karcie **przybornika** na **Projektanta obiektów Dataset**.  
  
     **Kreator konfiguracji TableAdapter** zostanie otwarty.  
  
3.  Ukończ pracę kreatora. Aby uzyskać więcej informacji, zobacz [Kreator konfiguracji TableAdapter](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8)  
  
#### <a name="to-create-a-new-data-table-with-a-tableadapter-from-server-explorer"></a>Aby utworzyć nową tabelę danych za pomocą TableAdapter z poziomu Eksploratora serwera  
  
1.  Otwórz swój zestaw danych w **projektanta źródła danych**.  
  
2.  Przeciągnij obiekt bazy danych (na przykład tabela) z **Eksploratora serwera** na **Projektanta obiektów Dataset**.  
  
## <a name="creating-a-standalone-datatable"></a>Tworzenie elementu DataTable autonomiczny  
 Tabele autonomiczny musi być `Fill` zaimplementować logikę w celu wypełnienia danymi. Aby uzyskać informacji na temat Wypełnianie tabel danych autonomicznych, zobacz [wypełnianie zestawu danych z elementu DataAdapter](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).  
  
#### <a name="to-create-a-new-stand-alone-data-table"></a>Aby utworzyć nową tabelę danych autonomicznego  
  
1.  Otwórz swój zestaw danych w **Projektanta obiektów Dataset**.  
  
2.  Przeciągnij <xref:System.Data.DataTable> z **DataSet** karcie **przybornika** na **Projektanta obiektów Dataset**.  
  
3.  Dodawanie kolumn do definiowania tabeli danych. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie kolumn do DataTable](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataTable>   
 [Wskazówki dotyczące danych](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Wskazówki: Wyświetlanie danych w formularzu Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [TableAdapter — Przegląd](../data-tools/tableadapter-overview.md)   
 [Tworzenie i edytowanie wpisanych zestawów danych](../data-tools/creating-and-editing-typed-datasets.md)   
 [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)   
 [Okno źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Porady: łączenie z danymi w bazie danych](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)