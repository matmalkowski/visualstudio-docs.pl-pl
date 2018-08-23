---
title: 'Porady: dodawanie zapytań globalnych do TableAdapter | Dokumentacja firmy Microsoft'
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
- global functions, datasets
- scalar functions, datasets
- TableAdapters, global queries
- data [Visual Studio], TableAdapters
- datasets [Visual Basic], scalar functions
- TableAdapter Query Configuration Wizard
- datasets [Visual Basic], global functions
- TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: 4abffd6b-2e9f-4ef3-99b2-6e9ae4ad4679
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 681fea494557e555c745d33c07c4e2c25cfe0f88
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678913"
---
# <a name="how-to-add-global-queries-to-a-tableadapter"></a>Porady: dodawanie zapytań globalnych do adaptera TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Zapytania globalne* zapytań SQL, które zwraca pojedynczą wartość (skalarną) lub nie ma wartości. Zwykle funkcje globalne wykonywania operacji bazy danych, takie jak operacje wstawiania, aktualizacji, usuwa i agregując informacje, takie jak zwracanie liczby klientów w tabeli lub łączne opłaty dla wszystkich elementów w określonej kolejności.  
  
 Dodawanie zapytań globalnych, uruchamiając **Kreatora konfiguracji zapytania TableAdapter** z poziomu **Projektanta obiektów Dataset**.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-global-query-to-a-dataset"></a>Aby dodać zapytanie globalne do zestawu danych  
  
1.  Otwórz zestaw danych w **Projektanta obiektów Dataset**. Aby uzyskać więcej informacji, zobacz [porady: otwieranie zestawu w Projektancie obiektów Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Przeciągnij **zapytania** z **zestawu danych** karcie **przybornika** na pustym obszarem **Projektanta obiektów Dataset**.  
  
     [Edytowanie TableAdapters](../data-tools/editing-tableadapters.md) zostanie otwarty.  
  
3.  Wybierz połączenie dla zapytania do użycia. Możesz wybrać jedną z listy lub Utwórz nowe połączenie. Jeśli tworzysz nowe połączenie, masz możliwość zapisywania pliku konfiguracji aplikacji. Aby uzyskać więcej informacji, zobacz [porady: zapisywanie i Edycja parametrów połączeń](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
4.  Wybierz, czy ma być używane w instrukcji SQL lub procedur składowanych.  
  
5.  Wybierz procedurę składowaną do użycia lub na **wybierz typ zapytania** strony kreatora, wybierz typ zapytania, a następnie kliknij przycisk **dalej**.  
  
6.  Podaj zapytania, który wykonuje odpowiednie zadanie, na przykład `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  Przeciąganie zapytanie bezpośrednio na **Projektanta obiektów Dataset** tworzy metodę, która zwróci tylko wartością skalarną (pojedynczą). Gdy zapytanie lub procedura składowana, którą wybierzesz może zwrócić więcej niż jedną wartość, metoda tworzone przez kreatora zwróci jedynie pojedyncza wartość. Na przykład zapytanie może zwrócić pierwszą kolumnę pierwszego wiersza zwrócone dane.  
  
7.  Ukończ pracę kreatora; Zapytanie jest dodawany do **Projektanta obiektów Dataset**. Aby uzyskać informacje na temat uruchamiania zapytania, zobacz [porady: wykonywanie zapytań TableAdapter](http://msdn.microsoft.com/library/c7518855-f896-41c1-b3de-1a8116280593).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie i konfigurowanie adapterów TableAdapter](../data-tools/create-and-configure-tableadapters.md)   
 [Porady: tworzenie zapytań TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Powiązywanie kontrolek formularzy Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [TableAdapter — Przegląd](../data-tools/tableadapter-overview.md)   
 [Tworzenie i edytowanie wpisanych zestawów danych](../data-tools/creating-and-editing-typed-datasets.md)   
 [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)   
 [Porady: łączenie z danymi w bazie danych](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Sprawdzanie poprawności danych](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Porady: nawigowanie po danych za pomocą kontrolki BindingNavigator formularzy Windows Forms](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [Wskazówki: Wyświetlanie danych w formularzu Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)