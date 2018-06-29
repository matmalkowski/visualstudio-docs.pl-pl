---
title: 'Wskazówki: tworzenie DataTable w projektancie obiektów Dataset'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 2e02f01924d5bae2770c579c4bfadd314e03cbe3
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089108"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>Wskazówki: Tworzenie DataTable w Projektancie obiektów Dataset

W tym przewodniku opisano sposób tworzenia <xref:System.Data.DataTable> (bez TableAdapter) przy użyciu **Projektant obiektów Dataset**. Aby uzyskać informacje na temat tworzenia tabel danych, które obejmują TableAdapters, zobacz [tworzenie i konfigurowanie TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="create-a-new-windows-forms-application"></a>Tworzenie nowej aplikacji Windows Forms

1. W programie Visual Studio na **pliku** menu, wybierz opcję **nowy** > **projektu**.

2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, następnie wybierz **Windows Desktop**.

3. W środkowym okienku wybierz **aplikacji formularzy systemu Windows** typu projektu.

4. Nazwij projekt **DataTableWalkthrough**, a następnie wybierz pozycję **OK**.

     **DataTableWalkthrough** projektu jest tworzony i dodawany do **Eksploratora rozwiązań**.

## <a name="add-a-new-dataset-to-the-application"></a>Dodaj nowy zestaw danych do aplikacji

1.  Na **projektu** menu, wybierz opcję **Dodaj nowy element**.

     Zostanie wyświetlone okno dialogowe Dodaj nowy element.

2.  W okienku po lewej stronie wybierz **danych**, a następnie wybierz pozycję **DataSet** w środkowym okienku.

3.  Wybierz **dodać**.

     Visual Studio dodaje plik o nazwie **DataSet1.xsd** do projektu i otwarcie go w **Projektant obiektów Dataset**.

## <a name="add-a-new-datatable-to-the-dataset"></a>Dodaj nową tabelę DataTable z zestawem danych

1.  Przeciągnij **DataTable** z **DataSet** karcie **przybornika** na **Projektant obiektów Dataset**.

     Tabela o nazwie **DataTable1** zostanie dodany do zestawu danych.

2.  Kliknij na pasku tytułu **DataTable1** i zmień jego nazwę `Music`.

## <a name="add-columns-to-the-datatable"></a>Dodawanie kolumn do DataTable

1.  Kliknij prawym przyciskiem myszy **utworów muzycznych** tabeli. Wskaż **Dodaj**, a następnie kliknij przycisk **kolumny**.

2.  Nazwa kolumny `SongID`.

3.  W **właściwości** ustaw <xref:System.Data.DataColumn.DataType%2A> właściwości <xref:System.Int16?displayProperty=fullName>.

4.  Powtórz ten proces i dodaj następujące kolumny:

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Ustaw klucz podstawowy dla tabeli

Wszystkie tabele danych powinny mieć klucz podstawowy. Klucz podstawowy unikatowo identyfikuje określonego rekordu w tabeli danych.

Można ustawić klucza podstawowego, kliknij prawym przyciskiem myszy **SongID** kolumny, a następnie kliknij przycisk **klucz podstawowy**. Ikona klucza jest wyświetlany obok pozycji **SongID** kolumny.

## <a name="save-your-project"></a>Zapisz projekt

Aby zapisać projekt DataTableWalkthrough na **pliku** menu, wybierz opcję **Zapisz wszystko**.

## <a name="see-also"></a>Zobacz także

- [Tworzenie i konfigurowanie zestawów danych w programie Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Powiązywanie formantów z danymi w Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Sprawdzanie poprawności danych](../data-tools/validate-data-in-datasets.md)