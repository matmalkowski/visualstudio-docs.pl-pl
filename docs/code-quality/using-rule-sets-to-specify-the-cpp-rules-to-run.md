---
title: Korzystanie z zestawów reguł do określania reguł C++ do uruchomienia
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: ad464b11538dd8a3faf2bdf26cd7e3b2bc9650dd
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Użyj zestawów reguł do określania reguł C++ do uruchomienia

W programie Visual Studio, można tworzyć i modyfikować niestandardowy *zestaw reguł* do określonego projektu potrzeb skojarzonych z analizy kodu. Aby utworzyć regułę niestandardową C++ zestaw, projektu C/C++ musi być otwarty w programie Visual Studio IDE. Możesz następnie otwórz zestaw standardowych reguł w edytorze zestawu reguł, a następnie dodaj lub usuń określone zasady i opcjonalnie zmienić akcję, która występuje, gdy analiza kodu Określa, że naruszono reguły.

Aby utworzyć nową regułę niestandardową zestaw, zapisz go przy użyciu nowej nazwy pliku. Zestaw reguł niestandardowych zostanie automatycznie przypisany do projektu.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Aby utworzyć niestandardową regułę z jednej istniejącego zestawu reguł

1. W Eksploratorze rozwiązań Otwórz menu skrótów projektu, a następnie wybierz pozycję **właściwości**.

2. Na **właściwości** , wybierz pozycję **analizy kodu**.

3. W **zestawu reguł** listy rozwijanej, wykonaj jedną z następujących czynności:

    - Wybierz zestaw reguł, który chcesz dostosować.

     \- lub -

    - Wybierz  **\<Przeglądaj >** określ zestaw istniejącej reguły, których nie ma na liście.

4. Wybierz **Otwórz** reguły są wyświetlane w edytorze zestawu reguł.

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Aby zmodyfikować reguły ustawić w edytorze zestawu reguł

- Aby zmienić nazwę wyświetlaną w zestawie reguł na **widoku** menu, wybierz **okna właściwości**. Wprowadź nazwę wyświetlaną w **nazwa** pole. Należy zauważyć, że nazwa wyświetlana może się różnić od nazwy pliku.

- Aby dodać zasady grupy do niestandardowego zestawu reguł, zaznacz pole wyboru grupy. Aby usunąć zasady grupy, wyczyść pole wyboru.

- Aby dodać regułę określonego zestawu reguł niestandardowych, zaznacz pole wyboru reguły. Aby usunąć regułę w zestawie reguł, usuń zaznaczenie pola wyboru.

- Aby zmienić Akcja podejmowana, gdy naruszenia reguły analizy kodu, wybierz **akcji** reguły do pola, a następnie wybierz jedną z następujących wartości:

     **Ostrzegaj** -generuje ostrzeżenie.

     **Błąd** -generuje błąd.

     **Brak** — wyłącza regułę. Ta akcja jest taka sama jak usunięcie reguły z zestawu reguł.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Do grupy, filtrowanie, lub zmień pola w edytorze zestawu reguł za pomocą paska narzędzi edytora zestawu reguł

- Aby rozszerzyć reguł we wszystkich grupach, wybierz **Rozwiń wszystkie**.

- Aby zwinąć reguł we wszystkich grupach, wybierz **Zwiń wszystkie**.

- Aby zmienić pole reguły są grupowane według, wybierz pola z **Group By** listy. Aby wyświetlić zasady rozgrupować, wybierz  **\<Brak >**.

- Aby dodać lub usunąć pola w kolumnach regułę, wybierz **opcje kolumny**.

- Aby ukryć reguł, które nie mają zastosowanie do bieżącego rozwiązania, wybierz polecenie **Ukryj reguł, które nie mają zastosowanie do bieżącego rozwiązania**.

- Aby przełączyć między pokazywanie i ukrywanie reguł, które są przypisane Akcja błędu, wybierz **Pokaż reguły, które mogą generować błędy analizy kodu**.

- Aby przełączyć między pokazywanie i ukrywanie reguł, które są przypisane ostrzeżenie akcję, wybierz **Pokaż reguły, które mogą generować ostrzeżenia analizy kodu**.

- Aby przełączyć między pokazywanie i ukrywanie reguł, które są przypisane **Brak** akcji, wybierz **Pokaż reguły, które nie są włączone**.

- Aby dodać lub usunąć domyślną regułę ustawia bieżący zestaw reguł firmy Microsoft, wybierz **Dodaj lub usuń podrzędne zestawy reguł**.