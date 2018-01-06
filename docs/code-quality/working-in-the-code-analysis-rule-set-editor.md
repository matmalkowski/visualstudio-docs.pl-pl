---
title: "Zestaw roboczy w reguł analizy kodu w edytorze | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c832b29512bfd7339ab60044ece81f1626be9bc7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Praca w edytorze zestawu reguł analizy kodu
Edytor zestawu reguł analizy kodu umożliwia określenie reguł, które znajdują się w zestawie reguł niestandardowych oraz określić akcję. Można również określić akcję do wykonania po analizy kodu napotka naruszenie reguły.  
  
|Akcja|Opis|  
|------------|-----------------|  
|**Ostrzeżenie**|Generuje ostrzeżenie w **listy błędów** okna.|  
|**Błąd**|Generuje błąd w **listy błędów** okna.|  
|**Brak**|Wyłącza regułę.|  
  
 Edytor reguły są wyświetlane w strukturze drzewa grup reguł przez regułę ustawiony pola, które określisz. Aby dodać lub usunąć reguły z zestawem reguł, wykonaj jedną lub więcej z następujących czynności:  
  
-   Wybierz lub wyczyść pole wyboru węzła grupy, aby dodać lub usunąć wszystkie reguły w grupie. Po wybraniu grupy wszystkie reguły są ustawione na **ostrzeżenie** akcji.  
  
-   Kliknij przycisk **akcji** pole grupy, a następnie określ akcję zastosować do wszystkich reguł w grupie.  
  
-   Wybierz lub wyczyść pole wyboru dla poszczególnych reguł. Po zaznaczeniu pola wyboru dla reguł do akcji, ostrzeżenie jest zestawu reguł.  
  
## <a name="rule-set-editor-toolbar"></a>Edytor paska narzędzi zestawu reguł  
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
 Zestaw reguł pola wyświetlane informacje dotyczące reguły ustawiona i można sortować i grupować listę reguł. Aby wyświetlić lub ukryć pól, kliknij przycisk **opcje kolumny** w regule Ustaw paska narzędzi edytora i następnie zaznacz lub usuń zaznaczenie pól wyboru pól do wyświetlenia lub ukrycia.  
  
 W poniższej tabeli opisano pola zestawu reguł.  
  
|Pole|Opis|  
|-----------|-----------------|  
|**IDENTYFIKATOR**|Identyfikator reguły.|  
|**Kategoria**|Oprócz ich członkostwa w zestawów reguł reguł analizy kodu również są pogrupowane według kategorii. Aby uzyskać więcej informacji, zobacz [analizy kodu dla zarządzanego kodu — ostrzeżenia](../code-quality/code-analysis-for-managed-code-warnings.md).|  
|**Nazwa**|Tytuł reguły.|  
|**Namespace**|Przestrzeń nazw reguły.|  
|**Typ docelowy**|Wskazuje, czy reguła dotyczy macierzystego, zarządzane lub baza danych kodu.|  
|**Akcja**|Akcja podejmowana, gdy naruszenia reguły analizy kodu, uruchom.<br /><br /> **Ostrzeżenie** -generuje ostrzeżenie.<br /><br /> **Błąd** -generuje błąd.<br /><br /> **Brak** — wyłącza regułę.<br /><br /> Można edytować pole akcji. Ustawienie wartości None, jest taka sama jak usuwając zaznaczenie pola wyboru dla reguły.|  
|**Zestawy reguł źródła**|Zestaw reguł zawiera reguły.|  
  
## <a name="sorting-and-filtering-rule-sets"></a>Sortowanie i filtrowanie zestawów reguł  
 Z nagłówków kolumn siatki zestaw reguł można sortować i filtrować według wartości pola reguły.  
  
-   Aby posortować listy zestawu reguł, kliknij nagłówek kolumny, pola, przez którą chcesz posortować. Jeśli zestawów reguł są grupowane, każda grupa jest sortowana pojedynczo.  
  
-   Aby filtrować zestawów reguł według wartości pola, kliknij przycisk Filtr, pola, według której chcesz filtrować w nagłówku kolumny. Zaznacz pola wyboru wartości, które chcesz wyświetlić, a następnie usuń zaznaczenie pól wyboru wartości, które chcesz ukryć.