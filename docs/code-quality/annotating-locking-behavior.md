---
title: Dodawanie adnotacji do zachowania blokującego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Releases_nonreentrant_lock_
- _Lock_kind_mutex_
- _Lock_kind_critical_section_
- _Acquires_lock_
- _Releases_lock_
- _Has_lock_kind_
- _Releases_exclusive_lock_
- _Post_same_lock_
- _Requires_exclusive_lock_held_
- _Requires_shared_lock_held_
- _Lock_kind_semaphore_
- _Requires_lock_held_
- _Acquires_exclusive_lock_
- _Create_lock_level_
- _Acquires_nonreentrant_lock_
- _Releases_shared_lock_
- _Has_lock_level_
- _Lock_kind_spin_lock_
- _Requires_lock_not_held_
- _Acquires_shared_lock_
- _Requires_no_locks_held_
- _Lock_level_order_
- _Lock_kind_event_
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e42762c77b1ee5fe006a48c4cf7abebea196a0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="annotating-locking-behavior"></a>Dodawanie adnotacji do zachowania blokującego
Aby uniknąć współbieżności usterki w programie wielowątkowe, zawsze wykonaj odpowiednie dyscypliny blokowania, użyj adnotacji SAL.  
  
 Współbieżność usterki są bardzo trudne do odtworzenia, diagnozowanie i debugowania, ponieważ są one deterministyczna. Rozsądkiem o naprzemiennego wykonywania wątku jest trudne w najlepszym i staje się niepraktyczne podczas projektowania treści kodu, który ma więcej niż kilka wątków. W związku z tym jest dobrym rozwiązaniem wykonaj blokowania dyscypliny programów wielowątkowych. Na przykład obeying kolejności blokady podczas pobierania wiele zamków pomaga uniknąć zakleszczenie i uzyskiwanie prawidłowego blokady guarding przed uzyskaniem dostępu do zasobu udostępnionego pomaga zapobiegać wyścigu.  
  
 Niestety, pozornie proste zasady blokowania zaskakująco trudno jest wykonaj w praktyce. Pewne ograniczenie języków programowania i kompilatory współczesnych jest, czy nie bezpośrednio obsługują specyfikację i analizy wymagania współbieżności. Programiści muszą polegać na komentarze w kodzie nieformalne Express ich cele dotyczące wykorzystania do blokad.  
  
 Adnotacje SAL współbieżności mają pomagają określić blokowania efekty uboczne, blokowanie odpowiedzialność, opieki danych blokady kolejności hierarchii i innych oczekiwane zachowanie blokowania. Adnotacje SAL współbieżności tworzenia reguł niejawnych jawne, zapewnia spójny sposób dokumentów, jak kod używa zasad blokowania. Adnotacje współbieżności zwiększa się również możliwość znalezienia wyścigu, zakleszczenie operacji synchronizacji niedopasowanych i inne błędy niewielkie współbieżności narzędzi analizy kodu.  
  
## <a name="general-guidelines"></a>Ogólne wskazówki  
 Za pomocą adnotacji, można prezentować umów, które są implikowana przez definicje funkcji między implementacji (callees) oraz klientów (wywołań), a express invariants i inne właściwości program, który może dodatkowo ulepszyć analizy.  
  
 SAL obsługuje wiele różnych elementów podstawowych blokowania — na przykład sekcje krytyczne, muteksy pokrętła blokad i innych obiektów zasobów. Wiele adnotacji współbieżności zająć wyrażenia blokady jako parametr. Według Konwencji blokady jest wskazywane przez wyrażenie ścieżki obiektu podstawowego blokady.  
  
 Niektóre reguły własność wątku należy wziąć pod uwagę:  
  
-   SPIN blokady są uncounted blokad, które mają własność wyczyść wątku.  
  
-   Muteksy i sekcje krytyczne są zliczane blokad, które mają własność wyczyść wątku.  
  
-   Semaforów i zdarzenia są zliczane blokad, które nie mają własność wyczyść wątku.  
  
## <a name="locking-annotations"></a>Blokowanie adnotacji  
 W poniższej tabeli wymieniono blokowania adnotacji.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|`_Acquires_exclusive_lock_(expr)`|Oznacza funkcji i wskazuje, że w post stan funkcji zwiększa o jeden w trybie wyłączności liczbę obiektu blokady o nazwie przez `expr`.|  
|`_Acquires_lock_(expr)`|Oznacza funkcji i wskazuje, że w post stan funkcji zwiększa przez jedną liczbę blokad obiektu blokady o nazwie przez `expr`.|  
|`_Acquires_nonreentrant_lock_(expr)`|Zablokuj o nazwie przez `expr` są uzyskiwane.  Błąd jest zgłaszany, gdy blokada jest już używana.|  
|`_Acquires_shared_lock_(expr)`|Oznacza funkcji oraz wskazuje, czy w post stan funkcji zwiększa o jeden licznik blokady współużytkowanej zablokować obiektu o nazwie przez `expr`.|  
|`_Create_lock_level_(name)`|Instrukcja, która deklaruje symbol `name` być poziomu blokady, dzięki czemu mogą być używane w adnotacjach `_Has_Lock_level_` i `_Lock_level_order_`.|  
|`_Has_lock_kind_(kind)`|Oznacza dowolnego obiektu, aby zawęzić kryteria informacji o typie obiektu zasobów. Czasami wspólny typ jest używany dla różnych rodzajów zasobów i przeciążone typ nie jest wystarczających do odróżnienia semantycznego wymagania między różnymi zasobami. Poniżej przedstawiono listę wstępnie zdefiniowanych `kind` parametry:<br /><br /> `_Lock_kind_mutex_`<br /> Identyfikator rodzaju blokady dla muteksy.<br /><br /> `_Lock_kind_event_`<br /> Zablokuj rodzaju identyfikator zdarzenia.<br /><br /> `_Lock_kind_semaphore_`<br /> Identyfikator rodzaju blokady dla semaforów.<br /><br /> `_Lock_kind_spin_lock_`<br /> Identyfikator rodzaju blokady blokad pokrętła.<br /><br /> `_Lock_kind_critical_section_`<br /> Identyfikator rodzaju blokady dla sekcji krytycznych.|  
|`_Has_lock_level_(name)`|Oznacza obiektu blokady i nadaje mu poziom blokady `name`.|  
|`_Lock_level_order_(name1, name2)`|Instrukcja, która zapewnia blokady kolejności między `name1` i `name2`.|  
|`_Post_same_lock_(expr1, expr2)`|Oznacza funkcji oraz wskazuje, w post stan blokady dwóch `expr1` i `expr2`, są traktowane jako są tego samego obiektu blokady.|  
|`_Releases_exclusive_lock_(expr)`|Oznacza funkcji oraz wskazuje, że w post stan zmniejsza funkcja przez jeden licznik w trybie wyłączności zablokować obiektu o nazwie przez `expr`.|  
|`_Releases_lock_(expr)`|Oznacza funkcji i wskazuje, że w post stan zmniejsza funkcja przez jeden licznik blokady zablokować obiektu o nazwie przez `expr`.|  
|`_Releases_nonreentrant_lock_(expr)`|Zablokuj o nazwie przez `expr` zostanie zwolniony. Błąd jest zgłaszany, gdy blokada nie jest obecnie używana.|  
|`_Releases_shared_lock_(expr)`|Oznacza funkcji i wskazuje, że w post stan zmniejsza funkcja przez jeden licznik blokady współużytkowanej zablokować obiektu o nazwie przez `expr`.|  
|`_Requires_lock_held_(expr)`|Oznacza funkcji oraz wskazuje, w wersji pre stanu liczbę blokad obiektu o nazwie przez `expr` co najmniej jeden.|  
|`_Requires_lock_not_held_(expr)`|Oznacza funkcji oraz wskazuje, w wersji pre stanu liczbę blokad obiektu o nazwie przez `expr` wynosi zero.|  
|`_Requires_no_locks_held_`|Oznacza funkcji i wskazuje, że licznik blokady wszystkich blokad, które są znane, aby narzędzie do sprawdzania zero.|  
|`_Requires_shared_lock_held_(expr)`|Oznacza funkcji oraz wskazuje, w wersji pre stanu blokady współużytkowanej liczba obiektu o nazwie przez `expr` co najmniej jeden.|  
|`_Requires_exclusive_lock_held_(expr)`|Oznacza funkcji oraz wskazuje, w wersji pre stanu liczby w trybie wyłączności obiektu o nazwie przez `expr` co najmniej jeden.|  
  
## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>Funkcje wewnętrzne SAL nieujawnionych blokowanie obiektów  
 Niektóre obiekty blokady nie są widoczne przez implementację funkcji blokowania skojarzone.  W poniższej tabeli wymieniono SAL wewnętrzne zmienne, które umożliwią adnotacje dla funkcji, które działają na tych obiektach nieujawnionych blokady.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|`_Global_cancel_spin_lock_`|W tym artykule opisano Anuluj blokadę pokrętła.|  
|`_Global_critical_region_`|W tym artykule opisano krytyczne regionu.|  
|`_Global_interlock_`|W tym artykule opisano operacje blokowane.|  
|`_Global_priority_region_`|W tym artykule opisano region priorytet.|  
  
## <a name="shared-data-access-annotations"></a>Adnotacje dostępu do udostępnionych danych  
 W poniższej tabeli wymieniono adnotacje dla dostępu do udostępnionych danych.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|`_Guarded_by_(expr)`|Oznacza zmienną i wskazuje, że jest dostępny zawsze, gdy zmienna, liczbę blokad obiektu blokady o nazwie przez `expr` co najmniej jeden.|  
|`_Interlocked_`|Oznacza zmienną i stanowi odpowiednik `_Guarded_by_(_Global_interlock_)`.|  
|`_Interlocked_operand_`|Parametr funkcji adnotacjami jest argument docelowy jednego z różnych funkcji blokowaną.  Tych argumentów operacji musi mieć określone dodatkowe właściwości.|  
|`_Write_guarded_by_(expr)`|Oznacza zmienną i wskazuje, że zawsze, gdy zmienna jest, liczbę blokad obiektu blokady o nazwie przez `expr` co najmniej jeden.|  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z adnotacji SAL w celu redukowanie defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Poznanie SAL](../code-quality/understanding-sal.md)   
 [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)   
 [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)   
 [Określanie, kiedy i gdzie dotyczy adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)   
 [Najlepsze praktyki i przykłady](../code-quality/best-practices-and-examples-sal.md)   
 [Blog zespołu ds. analizy kodu](http://go.microsoft.com/fwlink/p/?LinkId=251197)