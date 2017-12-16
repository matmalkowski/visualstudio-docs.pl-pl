---
title: "Wskazówki: Tworzenie DataTable w Projektancie obiektów Dataset | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/19/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: ec56d03acd9a0a4acae4fada28cf191cbe444059
ms.sourcegitcommit: e951faab601f5c05ad6606d8fd0cd2059fc4cc25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>Wskazówki: tworzenie DataTable w projektancie obiektów Dataset

W tym przewodniku opisano sposób tworzenia <xref:System.Data.DataTable> (bez TableAdapter) przy użyciu **Projektant obiektów Dataset**. Aby uzyskać informacje na temat tworzenia tabel danych, które obejmują TableAdapters, zobacz [tworzenie i konfigurowanie TableAdapters](../data-tools/create-and-configure-tableadapters.md).  

Zadania przedstawione w tym przewodniku obejmują:  

-   Tworzenie nowego projektu aplikacji Windows Forms  

-   Dodawanie nowy zestaw danych do aplikacji  

-   Dodawanie nowej tabeli danych do zestawu danych  

-   Dodawanie kolumn do tabeli danych  

-   Ustawienie klucza podstawowego dla tabeli  

## <a name="creating-a-new-windows-forms-application"></a>Tworzenie nowej aplikacji Windows Forms

### <a name="to-create-a-new-windows-forms-application-project"></a>Aby utworzyć nowy projekt aplikacji Windows Forms  
  
1. W programie Visual Studio na **pliku** menu, wybierz opcję **nowy**, **projektu...** .  
  
2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, następnie wybierz **Windows Desktop klasycznego**.  

3. W środkowym okienku wybierz **aplikacji formularzy systemu Windows** typu projektu.  

4. Nazwij projekt **DataTableWalkthrough**, a następnie wybierz pozycję **OK**. 
  
     **DataTableWalkthrough** projektu jest tworzony i dodane do **Eksploratora rozwiązań**.  

## <a name="adding-a-new-dataset-to-the-application"></a>Dodawanie nowy zestaw danych do aplikacji

### <a name="to-add-a-new-dataset-item-to-the-project"></a>Aby dodać nowy zestaw danych do projektu  
  
1.  Na **projektu** menu, wybierz opcję **Dodaj nowy element...** .  
  
     Zostanie wyświetlone okno dialogowe Dodaj nowy element.  
  
2.  W okienku po lewej stronie wybierz **danych**, a następnie wybierz pozycję **DataSet** w środkowym okienku.  
  
3.  Wybierz **dodać**.  
  
     Visual Studio dodaje plik o nazwie **DataSet1.xsd** do projektu i otwarcie go w **Projektant obiektów Dataset**.  

## <a name="adding-a-new-datatable-to-the-dataset"></a>Dodawanie nowego elementu DataTable z zestawem danych  

### <a name="to-add-a-new-data-table-to-the-dataset"></a>Aby dodać nową tabelę danych do zestawu danych  
  
1.  Przeciągnij **DataTable** z **DataSet** karcie **przybornika** na **Projektant obiektów Dataset**.  
  
     Tabela o nazwie **DataTable1** zostanie dodany do zestawu danych.  
   
2.  Kliknij na pasku tytułu **DataTable1** i zmień jego nazwę `Music`.  

## <a name="adding-columns-to-the-datatable"></a>Dodawanie kolumn do DataTable

### <a name="to-add-columns-to-the-datatable"></a>Aby dodać kolumny do elementu DataTable  
  
1.  Kliknij prawym przyciskiem myszy **utworów muzycznych** tabeli. Wskaż **Dodaj**, a następnie kliknij przycisk **kolumny**.  
  
2.  Nazwa kolumny `SongID`.  
  
3.  W **właściwości** ustaw <xref:System.Data.DataColumn.DataType%2A> właściwości <xref:System.Int16?displayProperty=fullName>.  
  
4.  Powtórz ten proces i dodaj następujące kolumny:  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## <a name="setting-the-primary-key-for-the-table"></a>Ustawienie klucza podstawowego dla tabeli

Wszystkie tabele danych powinny mieć klucz podstawowy. Klucz podstawowy unikatowo identyfikuje określonego rekordu w tabeli danych.  
  
### <a name="to-set-the-primary-key-of-the-data-table"></a>Można ustawić klucza podstawowego tabeli danych
  
-   Kliknij prawym przyciskiem myszy **SongID** kolumny, a następnie kliknij przycisk **klucz podstawowy**.  
  
     Ikona klucza jest wyświetlany obok pozycji **SongID** kolumny.  
  
## <a name="saving-your-project"></a>Zapisanie projektu  
  
### <a name="to-save-the-datatablewalkthrough-project"></a>Aby zapisać projekt DataTableWalkthrough  
  
-   Na **pliku** menu, kliknij przycisk **Zapisz wszystko**.  

## <a name="see-also"></a>Zobacz także

[Tworzenie i konfigurowanie zestawów danych w programie Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)  
[Powiązywanie formantów z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
[Sprawdzanie poprawności danych](../data-tools/validate-data-in-datasets.md)  
[Zapisywanie danych](../data-tools/saving-data.md)