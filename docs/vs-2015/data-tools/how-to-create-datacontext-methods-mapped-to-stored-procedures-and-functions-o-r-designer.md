---
title: 'Porady: Tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (Projektant O-R) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 62d250946e634627c16dbd3b56fce370c11e1f3f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684904"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Porady: Tworzenie metod DataContext zamapowanych na procedury składowane i funkcje (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak: metod tworzenia DataContext zamapowanych na procedury składowane i funkcje (Projektant O-R)](https://docs.microsoft.com/visualstudio/data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer).  
  
  
Procedury składowane i funkcje, które mogą być dodawane do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] jako <xref:System.Data.Linq.DataContext> metody. Wywołanie metody i przekazując wymaganych parametrów uruchamia procedurę składowaną lub funkcję w bazie danych i zwraca dane w typie zwracanym <xref:System.Data.Linq.DataContext> metody. Aby uzyskać szczegółowe informacje na temat <xref:System.Data.Linq.DataContext> metod, zobacz [metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Procedury składowane można również zastąpić to ustawienie domyślne [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] zachowania w czasie wykonywania, który wykonuje wstawiania, aktualizacji i usuwa podczas zmiany są zapisywane z klas jednostek bazy danych. Aby uzyskać więcej informacji, zobacz [porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="creating-datacontext-methods"></a>Tworzenie metod DataContext  
 Możesz utworzyć <xref:System.Data.Linq.DataContext> metody, przeciągając przechowywane procedury lub funkcji z **Server Explorer/Eksploratorze bazy danych** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
> [!NOTE]
>  Zwracany typ wygenerowany <xref:System.Data.Linq.DataContext> metoda różni się w zależności od tego, gdzie porzucić procedury składowanej lub funkcji na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Upuszczenie elementów bezpośrednio na istniejącej klasy jednostki tworzy <xref:System.Data.Linq.DataContext> metody z typem zwracanym klasy jednostki. Upuszczenie elementów na pustym obszarem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tworzy <xref:System.Data.Linq.DataContext> metodę, która zwraca typ wygenerowany automatycznie. Możesz zmienić typ zwracany <xref:System.Data.Linq.DataContext> metoda po dodaniu go do okienko metod. Aby sprawdzić lub zmienić typ zwracany <xref:System.Data.Linq.DataContext> metody, zaznacz ją i sprawdź **typie zwracanym** właściwość **właściwości** okna. Aby uzyskać więcej informacji, zobacz [porady: zmiana zwracanego typu metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Aby utworzyć element DataContext metody, które zwracają automatycznie wygenerowane typy  
  
1.  W **Eksploratora serwera**/**Eksplorator bazy danych**, rozwiń węzeł **procedur składowanych** węzeł bazy danych, w którym pracujesz.  
  
2.  Zlokalizuj odpowiednią procedurę składowaną i przeciągnij go na pustym obszarem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     <xref:System.Data.Linq.DataContext> Metody jest tworzone z automatycznie wygenerowanego zwracany typ i pojawia się w **metody** okienka.  
  
#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Aby utworzyć metody DataContext, które mają zwracany typ klasę jednostki  
  
1.  W **Eksploratora serwera**/**Eksplorator bazy danych**, rozwiń węzeł **procedur składowanych** węzeł bazy danych, w którym pracujesz.  
  
2.  Zlokalizuj odpowiednią procedurę składowaną i przeciągnij go do istniejącej klasy jednostki w [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     <xref:System.Data.Linq.DataContext> Metody jest tworzony z typem zwracanym klasy wybranej jednostki i pojawia się w **metody** okienka.  
  
> [!NOTE]
>  Informacje dotyczące zmiany istniejącego typu zwracanego <xref:System.Data.Linq.DataContext> metod, zobacz [porady: zmiana zwracanego typu metody DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Wskazówki: Tworzenie składnika LINQ to SQL klas (Projektant O-R)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ do SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Wprowadzenie do LINQ w Visual Basic](http://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984)   
 [Porady: zapisywanie kwerend LINQ w C#](http://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)

