---
title: Zestaw reguł Native Minimum Rules
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 2d898bc4-fba5-472e-8f09-b0c6b511c5a3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9d09b9e1486442177251c330b0281c9555006430
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="native-minimum-rules-rule-set"></a>Zestaw reguł Native Minimum Rules
Microsoft Native Minimum Rules dotyczą najpoważniejszych problemów w kodzie natywnym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji. Należy dołączyć ten zestaw reguł w każdego niestandardowego zestawu reguł tworzonego dla projektów natywnych.

|Reguła|Opis|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|Przy użyciu niezainicjowanej pamięci|
|[C6011](../code-quality/c6011.md)|Dereferencji wskaźnika o wartości Null|
|[C6029](../code-quality/c6029.md)|Użycie wartości typu Unchecked|
|[C6053](../code-quality/c6053.md)|Zakończenie zerem z wywołania|
|[C6059](../code-quality/c6059.md)|Zły łączenia|
|[C6063](../code-quality/c6063.md)|Brak argumentu ciągu w funkcji formatującej|
|[C6064](../code-quality/c6064.md)|Brak argumentu całkowitego dla funkcji formatującej|
|[C6066](../code-quality/c6066.md)|Brak argumentu będącego wskaźnikiem w funkcji formatującej|
|[C6067](../code-quality/c6067.md)|Brak argumentu będącego wskaźnikiem ciągu w funkcji formatującej|
|[C6101](../code-quality/c6101.md)|Zwrot niezainicjowanej pamięci|
|[C6200](../code-quality/c6200.md)|Indeks przekracza maksimum dla bufora|
|[C6201](../code-quality/c6201.md)|Indeks przekracza maksimum dla bufora stosu|
|[C6270](../code-quality/c6270.md)|Brak argumentu typu Float w funkcji formatującej|
|[C6271](../code-quality/c6271.md)|Dodatkowy Argument w funkcji formatującej|
|[C6272](../code-quality/c6272.md)|Argument z systemem innym niż Float w funkcji formatującej|
|[C6273](../code-quality/c6273.md)|Argumen nie jest liczbą całkowitą w funkcji formatującej|
|[C6274](../code-quality/c6274.md)|Argument-znakowy funkcji formatującej|
|[C6276](../code-quality/c6276.md)|Nieprawidłowy ciąg rzutowania|
|[C6277](../code-quality/c6277.md)|Nieprawidłowe wywołanie CreateProcess|
|[C6284](../code-quality/c6284.md)|Nieprawidłowy Argument obiektu dla funkcji formatującej|
|[C6290](../code-quality/c6290.md)|Operator logiczny Not- i priorytet|
|[C6291](../code-quality/c6291.md)|Operator logiczny Not- lub priorytetu|
|[C6302](../code-quality/c6302.md)|Argument ciągu nieprawidłowy znak w funkcji formatującej|
|[C6303](../code-quality/c6303.md)|Argument ciągu nieprawidłowych znaków dwubajtowych w funkcji formatującej|
|[C6305](../code-quality/c6305.md)|Niedopasowane rozmiaru i liczby korzystania|
|[C6306](../code-quality/c6306.md)|Wywołanie funkcji niepoprawne zmiennych argumentów|
|[C6328](../code-quality/c6328.md)|Potencjalna niezgodność typu argumentu|
|[C6385](../code-quality/c6385.md)|Przepełnienie odczytu|
|[C6386](../code-quality/c6386.md)|Przepełnienie zapisu|
|[C6387](../code-quality/c6387.md)|Nieprawidłowa wartość parametru|
|[C6500](../code-quality/c6500.md)|Nieprawidłowy atrybut właściwości|
|[C6501](../code-quality/c6501.md)|Wartości właściwości atrybutów powodujące konflikt|
|[C6503](../code-quality/c6503.md)|Odwołania nie może mieć wartości Null|
|[C6504](../code-quality/c6504.md)|Wartości null na nie będącego wskaźnikiem|
|[C6505](../code-quality/c6505.md)|MustCheck na Void|
|[C6506](../code-quality/c6506.md)|Rozmiar buforu dla elementu nie będącego wskaźnikiem lub tablicy|
|[C6508](../code-quality/c6508.md)|Dostęp do zapisu dla stałej|
|[C6509](../code-quality/c6509.md)|Użyto Return w warunku wstępnym|
|[C6510](../code-quality/c6510.md)|Zakończenie wartością null dla nie będącego wskaźnikiem|
|[C6511](../code-quality/c6511.md)|Element MustCheck musi mieć tak lub nie|
|[C6513](../code-quality/c6513.md)|Rozmiar elementu bez rozmiar bufora|
|[C6514](../code-quality/c6514.md)|Rozmiar buforu przekracza rozmiar tablicy|
|[C6515](../code-quality/c6515.md)|Rozmiar buforu dla elementu nie będącego wskaźnikiem|
|[C6516](../code-quality/c6516.md)|Brak właściwości dla atrybutu|
|[C6517](../code-quality/c6517.md)|Nieprawidłowy rozmiar dla bufora bez możliwości odczytu|
|[C6518](../code-quality/c6518.md)|Rozmiar zapisu dla bufora bez możliwości zapisu|
|[C6522](../code-quality/c6522.md)|Nieprawidłowy typ ciągu rozmiaru|
|[C6525](../code-quality/c6525.md)|Nieprawidłowy rozmiar nieosiągalna lokalizacja ciągu|
|[C6527](../code-quality/c6527.md)|Nieprawidłowa adnotacja: właściwość "NeedsRelease", nie może być używana dla wartości typu void|
|[C6530](../code-quality/c6530.md)|Nierozpoznany styl ciągu formatu|
|[C6540](../code-quality/c6540.md)|Użycie adnotacji atrybutów dla tej funkcji spowoduje unieważnienie wszystkich istniejących adnotacji __declspec|
|[C6551](../code-quality/c6551.md)|Nieprawidłowa specyfikacja rozmiaru: nie można przeanalizować wyrażenia|
|[C6552](../code-quality/c6552.md)|Nieprawidłowe wyrażenie Deref = lub Notref =: nie można przeanalizować wyrażenia|
|[C6701](../code-quality/c6701.md)|Wartość nie jest prawidłową wartością Yes/No/może|
|[C6702](../code-quality/c6702.md)|Wartość nie jest wartością ciągu|
|[C6703](../code-quality/c6703.md)|Wartość nie jest liczbą|
|[C6704](../code-quality/c6704.md)|Nieoczekiwany błąd adnotacji wyrażenia|
|[C6705](../code-quality/c6705.md)|Oczekiwana liczba argumentów dla adnotacji jest niezgodny z rzeczywistą liczbę argumentów dla adnotacji|
|[C6706](../code-quality/c6706.md)|Nieoczekiwany błąd adnotacji|
|[C28021](../code-quality/c28021.md)|Parametr adnotacją musi być wskaźnikiem|
|[C28182](../code-quality/c28182.md)|Wskaźnik usuwania odwołań o wartości NULL. Wskaźnik zawiera tę samą wartość NULL, tak jak innego wskaźnika.|
|[C28202](../code-quality/c28202.md)|Niedozwolone odwołanie do niestatycznego elementu członkowskiego|
|[C28203](../code-quality/c28203.md)|Niejednoznaczne odwołanie do elementu członkowskiego klasy.|
|[C28205](../code-quality/c28205.md)|_Success\_ lub _On_failure\_ używane w niedozwolonym kontekście|
|[C28206](../code-quality/c28206.md)|Lewy argument operacji wskazuje na strukturę, użyj "->"|
|[C28207](../code-quality/c28207.md)|Lewy argument operacji jest strukturą, użyj "."|
|[C28210](../code-quality/c28210.md)|Adnotacje dla kontekstu __on_failure nie może być w jawnym kontekście wstępnym|
|[C28211](../code-quality/c28211.md)|Nazwy kontekstu statycznego dla SAL_context|
|[C28212](../code-quality/c28212.md)|Oczekiwano wyrażenia wskaźnikowego dla adnotacji|
|[C28213](../code-quality/c28213.md)|_Use_decl_annotations\_ adnotacji musi być używany do odwołania, bez żadnych modyfikacji, wcześniejszej deklaracji.|
|[C28214](../code-quality/c28214.md)|Nazwy parametrów atrybutu muszą być: p1... p9|
|[C28215](../code-quality/c28215.md)|Nie można zastosować elementu typefix do parametru, który ma już typefix.|
|[C28216](../code-quality/c28216.md)|Adnotacja checkReturn dotyczy tylko dla parametru określoną funkcję.|
|[C28217](../code-quality/c28217.md)|Dla funkcji liczbę parametrów dla adnotacji nie odpowiada znalezionej w pliku|
|[C28218](../code-quality/c28218.md)|Dla funkcji paramteer parametr adnotacji nie odpowiada znalezionej w pliku|
|[C28219](../code-quality/c28219.md)|Oczekiwano elementu członkowskiego dla adnotacji parametr w adnotacji|
|[C28220](../code-quality/c28220.md)|Wyrażenie całkowite oczekiwany dla adnotacji, parametr w adnotacji|
|[C28221](../code-quality/c28221.md)|Oczekiwano wyrażenia ciągu dla parametrów w adnotacji|
|[C28222](../code-quality/c28222.md)|Oczekiwano __yes \__NIE, lub \__maybe oczekiwany dla adnotacji|
|[C28223](../code-quality/c28223.md)|Nie znaleziono oczekiwanego tokenu/identyfikatora dla adnotacji, parametr|
|[C28224](../code-quality/c28224.md)|Adnotacja wymaga parametrów|
|[C28225](../code-quality/c28225.md)|Nie znaleziono nieprawidłową liczbę wymaganych parametrów w adnotacji|
|[C28226](../code-quality/c28226.md)|Adnotacja nie może być PrimOp (w bieżącej deklaracji)|
|[C28227](../code-quality/c28227.md)|Adnotacja nie może być PrimOp (patrz Poprzednia deklaracja)|
|[C28228](../code-quality/c28228.md)|Parametr adnotacji: nie można użyć typu w adnotacjach|
|[C28229](../code-quality/c28229.md)|Adnotacja nie obsługuje parametrów|
|[C28230](../code-quality/c28230.md)|Typ parametru nie ma elementu członkowskiego.|
|[C28231](../code-quality/c28231.md)|Adnotacja jest prawidłowa tylko dla tablicy|
|[C28232](../code-quality/c28232.md)|Operatory pre, post i deref nie są stosowane do jakichkolwiek adnotacji|
|[C28233](../code-quality/c28233.md)|Operatory pre, post i deref zostały zastosowane do bloku|
|[C28234](../code-quality/c28234.md)|__at wyrażenie nie ma zastosowania do bieżącej funkcji|
|[C28235](../code-quality/c28235.md)|Funkcja nie może występować samodzielnie jako adnotacja|
|[C28236](../code-quality/c28236.md)|Nie można użyć adnotacji w wyrażeniu|
|[C28237](../code-quality/c28237.md)|Adnotacja parametru nie jest już obsługiwana|
|[C28238](../code-quality/c28238.md)|Adnotacja parametru ma więcej niż jedną wartość, stringValue i longValue. Użyj zapisu paramn = xxx|
|[C28239](../code-quality/c28239.md)|Adnotacja parametru ma zarówno wartość, stringValue lub longValue; i zapisu paramn = xxx. Użyj tylko zapisu paramn = xxx|
|[C28240](../code-quality/c28240.md)|Adnotacja parametru ma param2 ale nie ma param1|
|[C28241](../code-quality/c28241.md)|Adnotacja dla funkcji na parametr nie został rozpoznany.|
|[C28243](../code-quality/c28243.md)|Adnotacja dla funkcji w parametrze wymaga więcej wyłuskań niż pozwala właściwy adnotowany typ|
|[C28245](../code-quality/c28245.md)|Adnotacja dla funkcji oznacza "this" w innej niż — funkcja członkowska|
|[C28246](../code-quality/c28246.md)|Adnotacja parametru funkcji nie jest zgodny z typem parametru|
|[C28250](../code-quality/c28250.md)|Niespójna adnotacja dla funkcji: poprzednie wystąpienie posiada błąd.|
|[C28251](../code-quality/c28251.md)|Niespójna adnotacja dla funkcji: to wystąpienie posiada błąd.|
|[C28252](../code-quality/c28252.md)|Niespójna adnotacja dla funkcji: parametr ma inny adnotacje w tym wystąpieniu.|
|[C28253](../code-quality/c28253.md)|Niespójna adnotacja dla funkcji: parametr ma inny adnotacje w tym wystąpieniu.|
|[C28254](../code-quality/c28254.md)|(dynamic_cast <>) nie jest obsługiwane w adnotacjach|
|[C28262](../code-quality/c28262.md)|Znaleziono błąd składni w adnotacji w funkcji dla adnotacji|
|[C28263](../code-quality/c28263.md)|Znaleziono błąd składni w adnotacji warunkowej dla adnotacji — wewnętrzne|
|[C28267](../code-quality/c28267.md)|Znaleziono błąd składni w adnotacjach adnotacji w funkcji.|
|[C28272](../code-quality/c28272.md)|Adnotacja dla funkcji, parametr Rozpatrując jest niespójny z deklaracją funkcji|
|[C28273](../code-quality/c28273.md)|W przypadku funkcji wskazówek są niezgodne z deklaracją funkcji|
|[C28275](../code-quality/c28275.md)|Parametr _Macro_value\_ ma wartość null|
|[C28279](../code-quality/c28279.md)|Dla symbolu znaleziono "begin" bez odpowiadającego elementu "end"|
|[C28280](../code-quality/c28280.md)|Dla symbolu "end" znaleziono bez odpowiadającego mu "begin"|
|[C28282](../code-quality/c28282.md)|Ciągi formatów muszą być w warunkach wstępnych|
|[C28285](../code-quality/c28285.md)|Błąd składni w parametrze funkcji|
|[C28286](../code-quality/c28286.md)|W przypadku funkcji błąd składniowy w pobliżu elementu end|
|[C28287](../code-quality/c28287.md)|Dla funkcji, wystąpił błąd składni w _At\_adnotacji () (Nierozpoznana nazwa parametru)|
|[C28288](../code-quality/c28288.md)|Dla funkcji, wystąpił błąd składni w _At\_adnotacji () (Nieprawidłowa nazwa parametru)|
|[C28289](../code-quality/c28289.md)|Dla funkcji: ReadableTo lub WritableTo nie ma elementu limit-spec jako parametru|
|[C28290](../code-quality/c28290.md)|Adnotacja dla funkcji zawiera więcej symboli zewnętrznych niż rzeczywista liczba parametrów|
|[C28291](../code-quality/c28291.md)|Post null/notnull przy deref poziom 0 nie ma znaczenia dla funkcji.|
|[C28300](../code-quality/c28300.md)|Operandy wyrażenia niezgodnych typów dla operatora|
|[C28301](../code-quality/c28301.md)|Brak adnotacji dla pierwszej deklaracji funkcji.|
|[C28302](../code-quality/c28302.md)|Dodatkowe _deref —\_ znaleziono operatora w adnotacji.|
|[C28303](../code-quality/c28303.md)|Niejednoznaczne _deref —\_ znaleziono operatora w adnotacji.|
|[C28304](../code-quality/c28304.md)|Nieprawidłowo umieszczony _Notref\_ znaleziono operator zastosowany do tokenu.|
|[C28305](../code-quality/c28305.md)|Wykryto błąd podczas analizowania tokenu.|
|[C28350](../code-quality/c28350.md)|Adnotacja opisuje sytuację, której nie można zastosować warunkowo.|
|[C28351](../code-quality/c28351.md)|Adnotacja opisano, w której wartość dynamiczna (zmienna) nie można użyć w tym stanie.|