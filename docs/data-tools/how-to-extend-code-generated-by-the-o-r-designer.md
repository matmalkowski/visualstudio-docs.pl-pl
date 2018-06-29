---
title: 'Porady: rozszerzanie kod wygenerowany przez projektanta O-R'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9da4dca31043104c58122c2eed7aa55ae44ef07e
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089792"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Porady: rozszerzanie kod wygenerowany przez Projektanta obiektów relacyjnych
Kod wygenerowany przez **Projektanta obiektów relacyjnych** zostanie ponownie wygenerowany podczas wprowadzania zmian do innych obiektów na powierzchni projektanta i klas jednostek. Z powodu tego ponownego wygenerowania kodu żadnego kodu, które dodajesz do wygenerowanego kodu jest zwykle zastąpione, gdy projektant generuje kod. **Projektanta obiektów relacyjnych** umożliwia generowanie plików częściowej klasy, w których można dodać kod, który nie jest zastępowany. Jednym z przykładów Dodawanie własny kod do kod wygenerowany przez **Projektanta obiektów relacyjnych** polega na dodaniu sprawdzanie poprawności danych do programu LINQ w klasach SQL (jednostka). Aby uzyskać więcej informacji, zobacz [porady: Dodawanie walidacji do klas jednostek](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Dodawanie kodu do klasy jednostki

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Utwórz klasę częściową i dodać kod do klasy jednostki

1.  Otwarcia lub utworzenia nowego składnika LINQ to SQL klasy pliku (**.dbml** pliku) w **Projektanta obiektów relacyjnych**. (Kliknij dwukrotnie **.dbml** w pliku **Eksploratora rozwiązań** lub **Eksploratora bazy danych**.)

2.  W **Projektanta obiektów relacyjnych**, kliknij prawym przyciskiem myszy klasę, dla której chcesz dodać sprawdzanie poprawności, a następnie kliknij przycisk **kod widoku**.

     Otwiera edytora kodu z klasy częściowej klasy wybranej jednostki.

3.  Dodaj swój kod w deklaracji klasy częściowej klasy jednostka.

## <a name="add-code-to-a-datacontext"></a>Dodaj kod do elementu DataContext

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Utwórz klasę częściową i Dodaj kod do elementu DataContext

1.  Otwarcia lub utworzenia nowego składnika LINQ to SQL klasy pliku (**.dbml** pliku) w **Projektanta obiektów relacyjnych**. (Kliknij dwukrotnie **.dbml** w pliku **Eksploratora rozwiązań** lub **Eksploratora bazy danych**.)

2.  W **Projektanta obiektów relacyjnych**, kliknij prawym przyciskiem myszy pusty obszar na projektanta, a następnie kliknij przycisk **kod widoku**.

     Otwiera edytora kodu z częściowa klasy DataContext.

3.  Dodaj swój kod w deklaracji klasy częściowej dla elementu DataContext.

## <a name="see-also"></a>Zobacz także

- [LINQ do SQL narzędzi w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Wskazówki: Tworzenie LINQ w klasach SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)