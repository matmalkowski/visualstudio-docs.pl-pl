---
title: "Porady: tworzenie metodę DataContext mapowane na procedury składowane i funkcje (Projektant O-R) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: a56bacfd2d726e2ec7bedf69f6c79ce347e3556e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Porady: tworzenie metodę DataContext mapowane na procedury składowane i funkcje (Projektanta obiektów relacyjnych)
Procedury składowane i funkcje, które mogą być dodawane do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] jako <xref:System.Data.Linq.DataContext> metody. Wywołanie metody i przekazując wymaganych parametrów uruchamia procedura składowana lub funkcja w bazie danych i zwraca dane typu zwracanego przez <xref:System.Data.Linq.DataContext> metody. Aby uzyskać szczegółowe informacje o <xref:System.Data.Linq.DataContext> metod, zobacz [metodę DataContext (Projektanta obiektów relacyjnych)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Procedury składowane można również zastąpić domyślną [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] zachowanie środowiska uruchomieniowego, które wykonuje wstawiania, aktualizacji i usuwa podczas zmiany są zapisywane z klasami jednostki bazy danych. Aby uzyskać więcej informacji, zobacz [porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="creating-datacontext-methods"></a>Tworzenie metody DataContext  
 Można utworzyć <xref:System.Data.Linq.DataContext> metody, przeciągając przechowywane procedury lub funkcji z **Eksploratora Explorer/bazy danych serwera** na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
> [!NOTE]
>  Zwracany typ wygenerowany <xref:System.Data.Linq.DataContext> metoda zależy od tego, gdzie porzucić procedury składowanej lub funkcji na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Usunięcie elementów bezpośrednio na istniejącej klasy jednostki tworzy <xref:System.Data.Linq.DataContext> metoda ze zwracanym typem klasy jednostka. Usunięcie elementów na pustym obszarem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] tworzy <xref:System.Data.Linq.DataContext> metodę zwracającą automatycznie wygenerowanego typu. Można zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody po dodaniu go do okienka metody. Aby sprawdzić lub zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody, zaznacz go i sprawdzić **typu zwracanego** właściwości w **właściwości** okna. Aby uzyskać więcej informacji, zobacz [porady: Zmienianie zwracanego typu metody DataContext (Projektanta obiektów relacyjnych)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Aby utworzyć element DataContext metody, które zwracają automatycznie wygenerowane typy  
  
1.  W **Eksploratora serwera**/**Eksploratora bazy danych**, rozwiń węzeł **procedur składowanych** węzła w przypadku korzystania z bazy danych.  
  
2.  Znajdź odpowiednie procedury składowanej i przeciągnij go na pustym obszarem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     <xref:System.Data.Linq.DataContext> Metody jest tworzony z automatycznie wygenerowanym typem zwracanym i wyświetlany w **metody** okienka.  
  
#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Aby utworzyć metodę DataContext, które mają zwracany typ klasy jednostki  
  
1.  W **Eksploratora serwera**/**Eksploratora bazy danych**, rozwiń węzeł **procedur składowanych** węzła w przypadku korzystania z bazy danych.  
  
2.  Znajdź odpowiednie procedury składowanej i przeciągnij go do istniejącej klasy jednostki w [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     <xref:System.Data.Linq.DataContext> Metody jest tworzony z typem zwracanym klasy wybranej jednostki i wyświetlany w **metody** okienka.  
  
> [!NOTE]
>  Informacje o zmianie typu zwracanego przez istniejące <xref:System.Data.Linq.DataContext> metod, zobacz [porady: zmienić zwracany typ metody DataContext (Projektanta obiektów relacyjnych)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Metody DataContext (Projektanta obiektów relacyjnych)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Wskazówki: Tworzenie klasy LINQ do SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [LINQ do SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 [Wprowadzenie do LINQ w Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ w C#](/dotnet/csharp/linq/linq-in-csharp)