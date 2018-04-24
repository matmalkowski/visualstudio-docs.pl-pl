---
title: 'Porady: rozszerzanie kod wygenerowany przez projektanta O-R'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0210037cdd554838c9fe08c424f02b081c6f2e1a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Porady: rozszerzanie kod wygenerowany przez Projektanta obiektów relacyjnych
Kod wygenerowany przez [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] zostanie ponownie wygenerowany podczas wprowadzania zmian do innych obiektów na powierzchni projektanta i klas jednostek. Z powodu tego ponownego wygenerowania kodu żadnego kodu, które dodajesz do wygenerowanego kodu jest zwykle zastąpione, gdy projektant generuje kod. [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] Umożliwia generowanie plików częściowej klasy, w których można dodać kod, który nie zostanie nadpisany. Jednym z przykładów Dodawanie własny kod do kod wygenerowany przez [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] polega na dodaniu sprawdzanie poprawności danych do programu LINQ w klasach SQL (jednostka). Aby uzyskać informacje, zobacz [porady: Dodawanie walidacji do klas jednostek](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="adding-code-to-an-entity-class"></a>Dodawanie kodu do klasy jednostki

#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Utwórz klasę częściową i dodać kod do klasy jednostki

1.  Otwarcia lub utworzenia nowego składnika LINQ to SQL klasy pliku (**.dbml** pliku) w [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Kliknij dwukrotnie **.dbml** w pliku **Eksploratora rozwiązań**/**Eksploratora bazy danych**.)

2.  W [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], kliknij prawym przyciskiem myszy klasę, dla której chcesz dodać sprawdzanie poprawności, a następnie kliknij przycisk **kod widoku**.

     Otwiera edytora kodu z klasy częściowej klasy wybranej jednostki.

3.  Dodaj swój kod w deklaracji klasy częściowej klasy jednostka.

## <a name="adding-code-to-a-datacontext"></a>Dodawanie kodu do elementu DataContext

#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Utwórz klasę częściową i Dodaj kod do elementu DataContext

1.  Otwarcia lub utworzenia nowego składnika LINQ to SQL klasy pliku (**.dbml** pliku) w [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Kliknij dwukrotnie **.dbml** w pliku **Eksploratora rozwiązań**/**Eksploratora bazy danych**.)

2.  W [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], kliknij prawym przyciskiem myszy pusty obszar na projektanta, a następnie kliknij przycisk **kod widoku**.

     Otwiera edytora kodu z częściowa klasy DataContext.

3.  Dodaj swój kod w deklaracji klasy częściowej dla elementu DataContext.

## <a name="see-also"></a>Zobacz także

- [LINQ do SQL narzędzia w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Wskazówki: Tworzenie klasy LINQ do SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)