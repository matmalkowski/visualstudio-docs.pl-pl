---
title: 'Wskazówki: Tworzenie DataTable w Projektancie obiektów Dataset | Dokumentacja firmy Microsoft'
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
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 832dba200fca438d000bae101381389ea20cfb17
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42696685"
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>Wskazówki: tworzenie DataTable w projektancie obiektów Dataset
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym przewodniku opisano sposób tworzenia <xref:System.Data.DataTable> (bez TableAdapter) przy użyciu **Projektanta obiektów Dataset**. Aby uzyskać informacje na temat tworzenia tabel danych, które obejmują TableAdapters, zobacz [tworzenie i konfigurowanie adapterów TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Tworzenie nowego projektu aplikacji Windows  
  
-   Dodawanie nowego zestawu danych do aplikacji  
  
-   Dodawanie nowej tabeli danych do zestawu danych  
  
-   Dodawanie kolumn do tabeli danych  
  
-   Ustawienie klucza podstawowego dla tabeli  
  
## <a name="creating-a-new-windows-application"></a>Tworzenie nowej aplikacji Windows  
  
#### <a name="to-create-a-new-windows-application-project"></a>Aby utworzyć nowy projekt aplikacji Windows  
  
1.  Z **pliku** menu, Utwórz nowy projekt.  
  
2.  Wybierz język programowania w **typów projektów** okienka.  
  
3.  Kliknij przycisk **aplikacji Windows** w **szablony** okienka.  
  
4.  Nadaj projektowi nazwę `DataTableWalkthrough`, a następnie kliknij przycisk **OK**.  
  
     Program Visual Studio dodaje projekt do **Eksploratora rozwiązań** i wyświetla **Form1** w projektancie.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Dodawanie nowego zestawu danych do aplikacji  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Aby dodać nowy zestaw danych do projektu  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
     Dodaj nowy element pojawi się okno dialogowe.  
  
2.  W **szablony** wybierz opcję **zestawu danych**.  
  
3.  Kliknij przycisk **Dodaj**.  
  
     Program Visual Studio zostanie dodany plik o nazwie **DataSet1.xsd** do projektu, a następnie otwórz go w **Projektanta obiektów Dataset**.  
  
## <a name="adding-a-new-datatable-to-the-dataset"></a>Dodawanie nowego elementu DataTable do zestawu danych  
  
#### <a name="to-add-a-new-data-table-to-the-dataset"></a>Aby dodać nową tabelę danych do zestawu danych  
  
1.  Przeciągnij **DataTable** z **DataSet** karcie **przybornika** na **Projektanta obiektów Dataset**.  
  
     Tabela o nazwie **DataTable1** zostanie dodany do zestawu danych.  
  
    > [!NOTE]
    >  Aby utworzyć tabelę danych, która zawiera TableAdapter, zobacz [wskazówki: tworzenie TableAdapter z wieloma zapytaniami](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md).  
  
2.  Kliknij pasek tytułu **DataTable1** i zmień jego nazwę `Music`.  
  
## <a name="adding-columns-to-the-data-table"></a>Dodawanie kolumn do tabeli danych  
  
#### <a name="to-add-columns-to-the-data-table"></a>Aby dodać kolumny do tabeli danych  
  
1.  Kliknij prawym przyciskiem myszy **utworów muzycznych** tabeli. Wskaż **Dodaj**, a następnie kliknij przycisk **kolumny**.  
  
2.  Nadaj kolumnie nazwę `SongID`.  
  
3.  W **właściwości** oknie <xref:System.Data.DataColumn.DataType%2A> właściwość <xref:System.Int16?displayProperty=fullName>.  
  
4.  Powtórz ten proces i dodaj następujące kolumny:  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## <a name="setting-the-primary-key-for-the-table"></a>Ustawienie klucza podstawowego dla tabeli  
 Wszystkie tabele danych powinny mieć klucz podstawowy. Klucz podstawowy jednoznacznie identyfikuje określonego rekordu w tabeli danych.  
  
#### <a name="to-set-the-primary-key-of-the-data-table"></a>Można ustawić klucza podstawowego w tabeli danych  
  
-   Kliknij prawym przyciskiem myszy **SongID** kolumny, a następnie kliknij **Ustaw klucz podstawowy**.  
  
     Ikona klucza pojawia się obok **SongID** kolumny.  
  
## <a name="saving-your-project"></a>Zapisywanie projektu  
  
#### <a name="to-save-the-datatablewalkthrough-project"></a>Aby zapisać projekt DataTableWalkthrough  
  
-   Na **pliku** menu, kliknij przycisk **Zapisz wszystko**.  
  
## <a name="next-steps"></a>Następne kroki  
 Teraz, po utworzeniu tabeli, możesz chcieć wykonać jedną z następujących czynności:  
  
|Zadanie|Zobacz|  
|--------|---------|  
|Tworzenie formularza na dane wejściowe|[Wskazówki: Wyświetlanie danych w formularzu Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).|  
|Dodawanie danych do tabeli|[Dodawanie danych do elementu DataTable](http://msdn.microsoft.com/library/d6aa8474-7bde-48f7-949d-20dc38a1625b).|  
|Wyświetlanie danych w tabeli|[Wyświetlanie danych w elemencie DataTable](http://msdn.microsoft.com/library/1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc).|  
|Edytowanie danych|[Edycje elementu DataTable](http://msdn.microsoft.com/library/f08008a9-042e-4de9-94f3-4f0e502b1eb5)|  
|Usuń wiersz z tabeli|[Usuwanie elementu DataRow](http://msdn.microsoft.com/library/c34f531d-4b9b-4071-b2d7-342c402aa586)|  
  
## <a name="see-also"></a>Zobacz też  
 [O łączeniu z danymi w programie Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Przygotowanie aplikacji na odbieranie danych](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Pobieranie danych do aplikacji](../data-tools/fetching-data-into-your-application.md)   
 [Powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edytowanie danych w aplikacji](../data-tools/editing-data-in-your-application.md)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Zapisywanie danych](../data-tools/saving-data.md)   
 [Wskazówki dotyczące danych](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)