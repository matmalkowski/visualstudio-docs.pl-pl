---
title: Wyszukaj i wybierz typ .NET dialogowe | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: "13"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: ac184805803e92758e1de93400c957d00e8ebda6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Wyszukaj i wybierz typ .NET okno dialogowe
W **właściwości** projektantów, takich jak projektanta zmiennych, po wybraniu okna, okien dialogowych lub **Przeglądaj w poszukiwaniu typów...**  z listy typów danych, jest **Wyszukaj i wybierz typ .NET** okno dialogowe (określone w formie skróconej jako "typ przeglądarki"). W tym oknie można wybrać typ z widoku drzewa, zespołów i projektów.  
  
 To okno dialogowe jest stosowanych wiele scenariuszy użytkownika, takie jak następujące:  
  
-   Podczas ustawiania typ zmiennej lub argumentu.  
  
-   Podczas wybierania typu ogólnego działania.  
  
-   Podczas dodawania catch na <xref:System.Activities.Statements.TryCatch> działania.  
  
> [!NOTE]
>  Przeglądarki typu można wyświetlić typy tablicy w Visual Basic nieregularne, ale typy tablicy wielowymiarowej nie. Zobacz [Tablice nieregularne](http://go.microsoft.com/fwlink/?LinkId=195226) i [tablice wielowymiarowe](http://go.microsoft.com/fwlink/?LinkId=195227) szczegółowe informacje.  
  
## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Wybranie wartości lub typ referencyjny z przeglądarki typu  
  
#### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Aby wybrać typ wartości lub odwołania z przeglądarki typu  
  
1.  W **nazwy typu** wprowadź nazwę typu, który ma być używany.  
  
2.  Wykonaj jedną z następujących czynności:  
  
    -   Gdy nazwa typu, który ma być używany jest wyświetlany w drzewie w **nazwy typu** pola, kliknij dwukrotnie typu, aby go wybrać.  
  
    -   Wpisz małej liczby znaków w **nazwy typu** pole, aby jednoznacznie zidentyfikować typ, który ma być używany, a następnie naciśnij klawisz enter, aby wybrać typ  
  
#### <a name="to-select-a-generic-type-from-the-type-browser"></a>Aby wybrać typu ogólnego z przeglądarki typu  
  
1.  W **nazwy typu** , wpisz nazwę typu, który ma być używany.  
  
2.  Gdy nazwa typu, który ma być używany jest wyświetlany w drzewie w **Nazwa typu** kliknij typ wybierz ją spowodować pola listy rozwijanej jest wyświetlany.  
  
     Wybierz typ, który ma być używany do Zamknij ogólnego z pola listy rozwijanej, a następnie kliknij przycisk **OK**.  
  
## <a name="types-displayed-in-the-type-browser"></a>Typy wyświetlany w przeglądarce typu  
 Typy wyświetlany w przeglądarce typ zależy od sposobu została uruchomiona w przeglądarce typu. Jeśli typ przeglądarki został uruchomiony z projektu przepływu pracy wewnątrz **vs2010**, domyślnie wszystkich typów w przywoływanych zestawach i przywoływane projekty są wyświetlane. Jeśli typ przeglądarki został uruchomiony z poza **vs2010** projektu systemu (takie jak aplikacja rehosted przepływu pracy lub w przypadku autonomicznego pliku przepływu pracy), następnie domyślnie są wyświetlane typów z wszystkich zestawów załadowany w domenie aplikacji .  
  
 Typy w przeglądarce typu mogą być filtrowane przez deweloperów projektanta działania. Dla danego działania może zostać wyświetlony tylko ich podzbiór typów. Na przykład w <xref:System.Activities.Statements.TryCatch> działania, tylko typy pochodzące z <xref:System.Exception> są wyświetlane w przeglądarce typu.  
  
## <a name="filtering-search-results-in-the-type-browser"></a>Filtrowanie wyników wyszukiwania w przeglądarce typu  
 Lista typów w **nazwy typu** pole pobiera krótszą wpisywania więcej znaków, które można odnaleźć dopasowania. Tylko typy którego Pełna nazwa zaczyna się od ciągu wpisany lub którego krótka nazwa zaczyna się od ciągu, który został wpisany znajdują się na liście filtrowane.  
  
 Na przykład:  
  
1.  Wpisywanie **operacji** odpowiada <xref:System.OperationCanceledException> , ale nie <xref:System.InvalidOperationException>. Aby dopasować <xref:System.InvalidOperationException>, zacznij pisać System.I lub jest nieprawidłowy.  
  
2.  Wpisywanie **ogólnego** odpowiada <xref:System.GenericUriParser> , ale nie typy w <xref:System.Collections.Generic> przestrzeni nazw. Aby wyszukać typów w <xref:System.Collections.Generic> przestrzeni nazw, typu, w pełni kwalifikowaną nazwę przestrzeni nazw.  
  
## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Wybieranie kontraktu usługi, korzystając z okna dialogowego przeglądarki typu  
 Wybierając typ kontraktu usługi, typ przeglądarki wyświetlane są tylko typy, które mają <xref:System.ServiceModel.ServiceContractAttribute> atrybutu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przy użyciu projektantów działań](../workflow-designer/using-the-activity-designers.md)