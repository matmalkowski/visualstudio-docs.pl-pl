---
title: Użyj edytorze zestawu reguł analizy kodu w programie Visual Studio | Dokumentacja firmy Microsoft
ms.date: 04/-4/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c861a6beda6b0196ec03987915b1503f4cc55a19
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2018
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Edytor zestawu reguł analizy kodu

Edytor zestawu reguł analizy kodu umożliwia określenie reguł, które są dołączone do niestandardowego zestawu reguł i ważności naruszenia reguły.

|Akcja (waga)|Opis|
|-|-|
|Ostrzeżenie|Generuje ostrzeżenie w **listy błędów** , a także w czasie kompilacji.|
|Błąd|Generuje błąd w **listy błędów** , a także w czasie kompilacji.|
|Informacje o|Generuje komunikat w **listy błędów**.|
|Hidden|Naruszenie nie jest widoczny dla użytkownika. IDE jest powiadamiany o naruszenia, jednak.|
|Brak|Reguła jest pomijane. Zachowanie jest takie samo, jakby zasada została usunięta z zestawu reguł.|

Edytor reguły są wyświetlane w strukturze drzewa grup reguł przez regułę ustawiony pola, które określisz. Aby dodać lub usunąć reguły z zestawem reguł, wykonaj jedną lub więcej z następujących czynności:

- Wybierz lub wyczyść pole wyboru węzła grupy, aby dodać lub usunąć wszystkie reguły w grupie. Po wybraniu grupy wszystkie reguły są ustawione na **ostrzeżenie** akcji.

   > [!TIP]
   > Możesz zmienić sposób reguły są grupowane w **Grupuj według** listy rozwijanej.

- Kliknij przycisk **akcji** pole grupy, a następnie określ akcję zastosować do wszystkich reguł w grupie.

- Wybierz lub wyczyść pole wyboru dla poszczególnych reguł. Po zaznaczeniu pola wyboru dla reguł do akcji, ostrzeżenie jest zestawu reguł.

## <a name="toolbar"></a>Pasek narzędzi

Można użyć paska narzędzi edytora zestawu reguł do grupowania, filtrować i wyszukiwać dane wyświetlane w siatce zestawu reguł.

W poniższej tabeli opisano formantów na pasku narzędzi Edytor zestawu reguł.

|Toolbar — formant|Opis|
|---------------------|-----------------|
|**Rozwiń wszystko**|Zawiera reguły we wszystkich grupach.|
|**Zwiń wszystko**|Ukrywa reguł we wszystkich grupach.|
|**Grupuj według**|Określa pole, według której reguły są grupowane. Kliknij przycisk  **\<Brak >** pokazanie reguły bez grupy.|
|**Opcje kolumny**|Określa reguły pola do wyświetlenia.|
|**Ukryj reguł, które nie mają zastosowanie do bieżącego rozwiązania**|Pokazuje lub ukrywa reguł, które nie są tego samego typu docelowego jako rozwiązanie.|
|**Pokaż reguły, które mogą generować błędy analizy kodu**|Pokazuje lub ukrywa reguł, które są przypisane akcji błędu.|
|**Pokaż reguły, które mogą generować ostrzeżenia analizy kodu**|Pokazuje lub ukrywa reguł, które są przypisane ostrzeżenie akcję.|
|**Pokaż reguły, które nie są włączone**|Pokazuje lub ukrywa reguł, które są przypisane żadne działania.|
|**Dodaj lub usuń podrzędne zestawy reguł**|Dodaje lub usuwa zasady w zestawach wybranej reguły.|
|**Szukaj reguł**|Wyszukuje ciąg, który należy określić wszystkie wartości pól.|

## <a name="rule-set-fields"></a>Pola zestawu reguł

Pola zestaw reguł wyświetlać informacje na temat zestawu reguł i można sortować i grupować listę reguł. Aby wyświetlić lub ukryć pola, wybierz **opcje kolumny** w regule Ustaw paska narzędzi edytora i następnie zaznacz lub usuń zaznaczenie pól wyboru pól do wyświetlenia lub ukrycia.

W poniższej tabeli opisano pola zestawu reguł:

|Pole|Opis|
|-----------|-----------------|
|**ID**|Identyfikator reguły.|
|**Kategoria**|Oprócz ich członkostwa w zestawów reguł reguł analizy kodu również są pogrupowane według kategorii. Aby uzyskać więcej informacji, zobacz [ostrzeżeń analizy kodu](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Nazwa**|Tytuł reguły.|
|**Namespace**|Przestrzeń nazw reguły.|
|**Typ docelowy**|Wskazuje, czy reguła dotyczy macierzystego, zarządzane lub baza danych kodu.|
|**Akcja**|Akcja podejmowana, gdy naruszenia reguły analizy kodu, uruchom. Można edytować **akcji** pola.|
|**Zestawy reguł źródła**|Zestaw reguł zawiera reguły.|

## <a name="sort-and-filter-rule-sets"></a>Sortowanie i filtrowanie zestawów reguł

Z nagłówków kolumn siatki zestaw reguł można sortować i filtrować według wartości pola reguły.

- Aby posortować listy zestawu reguł, kliknij nagłówek kolumny, pola, przez którą chcesz posortować. Jeśli zestawów reguł są grupowane, każda grupa jest sortowana pojedynczo.

- Aby filtrować zestawów reguł według wartości pola, kliknij przycisk Filtr, pola, według której chcesz filtrować w nagłówku kolumny. Zaznacz pola wyboru wartości, które chcesz wyświetlić, a następnie usuń zaznaczenie pól wyboru wartości, które chcesz ukryć.

## <a name="see-also"></a>Zobacz także

- [Tworzenie niestandardowego zestawu reguł](../code-quality/how-to-create-a-custom-rule-set.md)