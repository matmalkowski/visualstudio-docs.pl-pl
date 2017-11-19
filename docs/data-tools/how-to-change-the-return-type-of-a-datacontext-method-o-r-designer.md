---
title: 'Porady: Zmienianie zwracanego typu metody DataContext (Projektant O-R) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 869460f4ac40aece5421611cd83aad6a7f11ef57
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Porady: Zmienianie zwracanego typu metody DataContext (Projektanta obiektów relacyjnych)
Zwracany typ <xref:System.Data.Linq.DataContext> — metoda (utworzone na podstawie procedury składowanej lub funkcji) różni się w zależności od tego, gdzie porzucić procedury składowanej lub funkcji w [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Jeśli musisz porzucić elementu bezpośrednio na istniejącej klasy jednostki, <xref:System.Data.Linq.DataContext> metodę, która ma zwracany typ klasy jednostka jest tworzony (Jeśli schemat danych zwróconych przez procedura składowana lub funkcja odpowiada kształtu klasy jednostka). Jeśli element jest upuścić nad pustym obszarem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], <xref:System.Data.Linq.DataContext> metodę zwracającą automatycznie wygenerowany typ jest tworzony. Można zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody po dodaniu do okienka metody. Aby sprawdzić lub zmienić zwracany typ <xref:System.Data.Linq.DataContext> metody, zaznacz go i kliknij **typu zwracanego** właściwości w **właściwości** okna.  
  
> [!NOTE]
>  Nie można przywrócić <xref:System.Data.Linq.DataContext> metod, które mają zwracany typ. ustawione na klasę jednostki, aby zwracany typ generowane automatycznie za pomocą **właściwości** okna. Aby przywrócić <xref:System.Data.Linq.DataContext> metody, aby przywrócić automatycznie wygenerowany typ, musisz przeciągnąć oryginalny obiekt bazy danych ponownie do Projektanta obiektów relacyjnych.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Aby zmienić zwracanego typu metody DataContext z typu automatycznie generowanej klasy jednostki  
  
1.  Wybierz <xref:System.Data.Linq.DataContext> metody w okienku metody.  
  
2.  Wybierz **typu zwracanego** w **właściwości** okna, a następnie wybierz dostępne jednostki klasy w **typu zwracanego** listy. Jeśli klasa żądanej jednostki nie jest na liście, dodaj go do lub utwórz go w [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ją dodać do listy.  
  
3.  Zapisz plik .dbml.  
  
## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Aby zmienić zwracany typ metody DataContext z klasy jednostki do automatycznie generowanej typu  
  
1.  Wybierz <xref:System.Data.Linq.DataContext> metody w okienku metod i usuń go.  
  
2.  Przeciągnij obiekty z **Eksploratora serwera**/**Eksploratora bazy danych** nad pustym obszarem Projektanta obiektów relacyjnych.  
  
3.  Zapisz plik .dbml.  
  
## <a name="see-also"></a>Zobacz także
[LINQ do SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[LINQ do SQL](/dotnet/framework/data/adonet/sql/linq/index)   
[Metody DataContext (Projektanta obiektów relacyjnych)](../data-tools/datacontext-methods-o-r-designer.md)   
[Porady: tworzenie metodę DataContext mapowane na procedury składowane i funkcje (Projektanta obiektów relacyjnych)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)