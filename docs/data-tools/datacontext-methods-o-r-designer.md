---
title: Metody DataContext (Projektant O-R) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 5eb37bd3abbf88b04bed0d382e07abe4379eb661
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="datacontext-methods-or-designer"></a>Metody DataContext (Projektanta obiektów relacyjnych)
<xref:System.Data.Linq.DataContext>metody (w kontekście [składnika LINQ to SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) są metody <xref:System.Data.Linq.DataContext> klasy, która uruchamianie procedury składowane i funkcje w bazie danych.  
  
 <xref:System.Data.Linq.DataContext> Jest klasa [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klasy, która działa jako kanał między bazą danych programu SQL Server i [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klas jednostek zamapowane na tę bazę danych. <xref:System.Data.Linq.DataContext> Klasa zawiera informacje o parametrach połączenia i metody połączenia z bazą danych i manipulowania danymi w bazie danych. Domyślnie <xref:System.Data.Linq.DataContext> klasa zawiera kilka metod, które można wywoływać, takich jak <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metodę, która wysyła zaktualizowane dane z [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] klasy do bazy danych. Można również utworzyć dodatkowe <xref:System.Data.Linq.DataContext> metod, które mapują na procedury składowane i funkcje. Innymi słowy, wywołanie metody te niestandardowe będzie wykonywany procedura składowana lub funkcja w bazie danych <xref:System.Data.Linq.DataContext> metody jest mapowany na. Można dodać nowych metod <xref:System.Data.Linq.DataContext> klasy tak samo, jak należy dodać metody umożliwiające rozszerzenie dowolnej klasy. Jednak w dyskusjach na temat <xref:System.Data.Linq.DataContext> metod w kontekście [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], jest <xref:System.Data.Linq.DataContext> metod, które mapują na procedury składowane i funkcje, które są omawiana.  
  
## <a name="methods-pane"></a>Okienko metody  
 <xref:System.Data.Linq.DataContext>metody, które mapują na procedury składowane i funkcje są wyświetlane w okienku metody [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. W okienku metody to okienko po stronie **jednostek** okienka (powierzchni projektu głównego). Okienko metody zawiera wszystkie <xref:System.Data.Linq.DataContext> metod, które zostały utworzone przy użyciu [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Domyślnie w okienku metod jest pusty; Przeciągnij procedury składowanej lub funkcji z **Eksploratora serwera**/**Eksploratora bazy danych** na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] utworzyć <xref:System.Data.Linq.DataContext> metod i wypełnić okienko metody. Aby uzyskać więcej informacji, zobacz [porady: metody tworzenia DataContext mapowane na procedury składowane i funkcje (Projektanta obiektów relacyjnych)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).  
  
> [!NOTE]
>  Otwieranie i zamykanie okienko metody, klikając prawym przyciskiem myszy [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] , a następnie klikając polecenie **ukryć okienko metody** lub **Pokaż okienko metody**, lub użyj skrótu klawiaturowego CTRL + 1.  
  
## <a name="two-types-of-datacontext-methods"></a>Dwa typy metod DataContext  
 Metody DataContext są tych metod, które mapują na procedury składowane i funkcje w bazie danych. Możesz utworzyć i Dodawanie metody DataContext w okienku metody [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Istnieją dwa różne typy <xref:System.Data.Linq.DataContext> metod; takich, które zwracają jeden lub więcej zestawów wyników i tych, które nie zawierają:  
  
-   <xref:System.Data.Linq.DataContext>metody, które zwracają jeden lub więcej zestawów wyników:  
  
     Utworzyć ten rodzaj <xref:System.Data.Linq.DataContext> metody, gdy aplikacja wystarczy do uruchamiania procedury składowane i funkcje w bazie danych i zwracają wyniki. Aby uzyskać więcej informacji, zobacz [jak: metody tworzenia DataContext mapowane na procedury składowane i funkcje (Projektanta obiektów relacyjnych)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, a <xref:System.Data.Linq.IMultipleResults>.  
  
-   <xref:System.Data.Linq.DataContext>metody, które nie zwracają zestawów wyników: takie jak wstawia, aktualizacje i usuwa dla klasy określonej jednostki.  
  
     Utworzyć ten rodzaj <xref:System.Data.Linq.DataContext> metody po aplikacji do uruchamiania procedur składowanych zamiast przy użyciu domyślnego [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] zachowanie zapisywanie zmodyfikowanych danych między klasami jednostki oraz bazy danych. Aby uzyskać więcej informacji, zobacz [porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="return-types-of-datacontext-methods"></a>Zwracane typy metodę DataContext  
 Przeciągnięcie procedury składowane i funkcje z **Eksploratora serwera**/**Eksploratora bazy danych** na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], zwracany typ wygenerowany <xref:System.Data.Linq.DataContext> różni się — metoda w zależności od tego, gdzie można usunąć elementu. Usunięcie elementów bezpośrednio na istniejącej klasy jednostki tworzy <xref:System.Data.Linq.DataContext> metody z typem zwracanym klasy jednostki; upuszczanie elementów na pustym obszarem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] (w okienku albo) tworzy <xref:System.Data.Linq.DataContext> metodę zwracającą automatycznie wygenerowany typ. Automatycznie wygenerowany typ, który jest tworzony ma nazwę pasującą procedura składowana lub funkcja nazwę i właściwości, mapowane do pól zwrócone przez procedurę składowaną lub funkcję.  
  
> [!NOTE]
>  Można zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody po dodaniu do okienka metody. Aby sprawdzić lub zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody, zaznacz go i sprawdzić **typu zwracanego** właściwości w **właściwości** okna. Aby uzyskać więcej informacji, zobacz [porady: Zmienianie zwracanego typu metody DataContext (Projektanta obiektów relacyjnych)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 Obiekty, które przeciągnij z bazy danych na powierzchnię Projektanta obiektów relacyjnych będzie miała nazwę automatycznie, na podstawie nazwy obiektów w bazie danych. Jeśli ten sam obiekt zostanie przeciągnięty więcej niż raz, na końcu nową nazwę, która odróżnia nazwy zostanie dołączona liczba. Nazwy obiektów bazy danych zawierają spacje lub znaki nieobsługiwane w języku Visual Basic lub C#, zostanie zastąpiony miejsca lub nieprawidłowy znak podkreślenia.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ do SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 [Procedury składowane](/dotnet/framework/data/adonet/sql/linq/stored-procedures)   
 [Porady: tworzenie metodę DataContext mapowane na procedury składowane i funkcje (Projektanta obiektów relacyjnych)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Wskazówki: Dostosowywanie wstawiania, aktualizowania i usuwania zachowanie klas jednostek](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Wskazówki: Tworzenie klasy LINQ do SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)