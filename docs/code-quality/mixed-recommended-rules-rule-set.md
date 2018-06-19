---
title: Zestaw reguł Mixed Recommended Rules
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 77774f4460bab7b36fd3684175228e7522a67027
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31926982"
---
# <a name="mixed-recommended-rules-rule-set"></a>Zestaw reguł Mixed Recommended Rules

Microsoft mieszanych zalecane reguły dotyczą najczęstszych i najpoważniejszych problemów w projektach C++ obsługujących środowisko uruchomieniowe języka wspólnego, w tym potencjalnych luk w zabezpieczeniach, awarii aplikacji i inne ważne błędy logiki i projektowania. Należy dołączyć ten zestaw reguł w każdego niestandardowego zestawu reguł tworzonego dla projektów C++ obsługujących środowisko uruchomieniowe języka wspólnego.

|Reguła|Opis|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|Przy użyciu niezainicjowanej pamięci|
|[C6011](../code-quality/c6011.md)|Dereferencji wskaźnika o wartości Null|
|[C6029](../code-quality/c6029.md)|Użycie wartości typu Unchecked|
|[C6031](../code-quality/c6031.md)|Wartość zwracana ignorowane|
|[C6053](../code-quality/c6053.md)|Zakończenie zerem z wywołania|
|[C6054](../code-quality/c6054.md)|Brak zakończenia od zera|
|[C6059](../code-quality/c6059.md)|Zły łączenia|
|[C6063](../code-quality/c6063.md)|Brak argumentu ciągu w funkcji formatującej|
|[C6064](../code-quality/c6064.md)|Brak argumentu całkowitego dla funkcji formatującej|
|[C6066](../code-quality/c6066.md)|Brak argumentu będącego wskaźnikiem w funkcji formatującej|
|[C6067](../code-quality/c6067.md)|Brak argumentu będącego wskaźnikiem ciągu w funkcji formatującej|
|[C6101](../code-quality/c6101.md)|Zwrot niezainicjowanej pamięci|
|[C6200](../code-quality/c6200.md)|Indeks przekracza maksimum dla bufora|
|[C6201](../code-quality/c6201.md)|Indeks przekracza maksimum dla bufora stosu|
|[C6214](../code-quality/c6214.md)|Nieprawidłowe rzutowanie HRESULT na BOOL|
|[C6215](../code-quality/c6215.md)|Nieprawidłowe rzutowanie BOOL na HRESULT|
|[C6216](../code-quality/c6216.md)|Nieprawidłowe wstawione przez kompilator rzutowanie BOOL na HRESULT|
|[C6217](../code-quality/c6217.md)|Test nieprawidłowy HRESULT z użyciem NOT|
|[C6220](../code-quality/c6220.md)|Porównanie nieprawidłowy HRESULT z -1|
|[C6226](../code-quality/c6226.md)|Przypisanie nieprawidłowy HRESULT do -1|
|[C6230](../code-quality/c6230.md)|Użycie HRESULT nieprawidłowa jako wartość logiczna|
|[C6235](../code-quality/c6235.md)|Stała niezerowa z logiczną — lub|
|[C6236](../code-quality/c6236.md)|Logiczne — lub stała niezerowa|
|[C6237](../code-quality/c6237.md)|Zero z logiczną- i powoduje utratę efektów ubocznych|
|[C6242](../code-quality/c6242.md)|Lokalne rozwinięcie wymuszone|
|[C6248](../code-quality/c6248.md)|Tworzenie listy DACL wartości Null|
|[C6250](../code-quality/c6250.md)|Deskryptory adresu nieopublikowane|
|[C6255](../code-quality/c6255.md)|Niechronione użycie Alloca|
|[C6258](../code-quality/c6258.md)|Przy użyciu zakończenie wątku|
|[C6259](../code-quality/c6259.md)|Martwych kod bitowy — lub przełącznik z ograniczeniami|
|[C6260](../code-quality/c6260.md)|Użycie arytmetyki bajtów|
|[C6262](../code-quality/c6262.md)|Wykorzystanie stosu nadmiernego|
|[C6263](../code-quality/c6263.md)|Używanie Alloca w pętli|
|[C6268](../code-quality/c6268.md)|Brak nawiasów w rzutowaniu|
|[C6269](../code-quality/c6269.md)|Wyłuskania wskaźnika ignorowane|
|[C6270](../code-quality/c6270.md)|Brak argumentu typu Float w funkcji formatującej|
|[C6271](../code-quality/c6271.md)|Dodatkowy Argument w funkcji formatującej|
|[C6272](../code-quality/c6272.md)|Argument z systemem innym niż Float w funkcji formatującej|
|[C6273](../code-quality/c6273.md)|Argument nie jest liczbą całkowitą w funkcji formatującej|
|[C6274](../code-quality/c6274.md)|Argument-znakowy funkcji formatującej|
|[C6276](../code-quality/c6276.md)|Nieprawidłowy ciąg rzutowania|
|[C6277](../code-quality/c6277.md)|Nieprawidłowe wywołanie CreateProcess|
|[C6278](../code-quality/c6278.md)|Niezgodność Array New operatora skalarnego Delete|
|[C6279](../code-quality/c6279.md)|Niezgodność nowe skalarną usuwania tablicy|
|[C6280](../code-quality/c6280.md)|Niezgodność dezalokacji alokacji pamięci|
|[C6281](../code-quality/c6281.md)|Pierwszeństwo bitowe relacji|
|[C6282](../code-quality/c6282.md)|Przypisanie zastępuje testu|
|[C6283](../code-quality/c6283.md)|Pierwotne niezgodność Array New operatora skalarnego Delete|
|[C6284](../code-quality/c6284.md)|Nieprawidłowy Argument obiektu dla funkcji formatującej|
|[C6285](../code-quality/c6285.md)|Logiczne — lub stałych|
|[C6286](../code-quality/c6286.md)|Niezerowy logiczne — lub utraty efekty uboczne|
|[C6287](../code-quality/c6287.md)|Nadmiarowe testu|
|[C6288](../code-quality/c6288.md)|Wzajemne włączenie nad logicznej- i ma wartość False|
|[C6289](../code-quality/c6289.md)|Wzajemne wykluczenie nad logiczne — lub ma wartość True|
|[C6290](../code-quality/c6290.md)|Operator logiczny Not- i priorytet|
|[C6291](../code-quality/c6291.md)|Operator logiczny Not- lub priorytetu|
|[C6292](../code-quality/c6292.md)|Pętla zlicza w górę od wartości maksymalnej|
|[C6293](../code-quality/c6293.md)|Pętla zlicza w dół zaczynając od Minimum|
|[C6294](../code-quality/c6294.md)|Wnętrze pętli nigdy nie zostanie wykonane|
|[C6295](../code-quality/c6295.md)|Nieskończonej pętli|
|[C6296](../code-quality/c6296.md)|Pętla wykonywane tylko raz|
|[C6297](../code-quality/c6297.md)|Rzutowanie wynik przesunięcia na większy rozmiar|
|[C6299](../code-quality/c6299.md)|Bitfield do porównania logiczna|
|[C6302](../code-quality/c6302.md)|Argument ciągu nieprawidłowy znak w funkcji formatującej|
|[C6303](../code-quality/c6303.md)|Argument ciągu nieprawidłowych znaków dwubajtowych w funkcji formatującej|
|[C6305](../code-quality/c6305.md)|Niedopasowane rozmiaru i liczby korzystania|
|[C6306](../code-quality/c6306.md)|Wywołanie funkcji niepoprawne zmiennych argumentów|
|[C6308](../code-quality/c6308.md)|Przeciek Realloc|
|[C6310](../code-quality/c6310.md)|Stała w filtrze wyjątków niedozwolony|
|[C6312](../code-quality/c6312.md)|Wyjątek powoduje kontynuację wykonywania pętli|
|[C6314](../code-quality/c6314.md)|Operator- lub priorytetu|
|[C6317](../code-quality/c6317.md)|Nie nie dopełnienia|
|[C6318](../code-quality/c6318.md)|Wyjątek powoduje kontynuację wyszukiwania|
|[C6319](../code-quality/c6319.md)|Ignorowane przez przecinkami|
|[C6324](../code-quality/c6324.md)|Kopia ciągu zamiast porównania ciągu|
|[C6328](../code-quality/c6328.md)|Potencjalna niezgodność typu argumentu|
|[C6331](../code-quality/c6331.md)|VirtualFree nieprawidłowe flagi|
|[C6332](../code-quality/c6332.md)|VirtualFree nieprawidłowy parametr|
|[C6333](../code-quality/c6333.md)|VirtualFree nieprawidłowy rozmiar|
|[C6335](../code-quality/c6335.md)|Przeciek uchwytu procesu|
|[C6381](../code-quality/c6381.md)|Brak informacji o zamknięcia|
|[C6383](../code-quality/c6383.md)|Element — liczba bajtów-Liczba przepełnienie buforu|
|[C6384](../code-quality/c6384.md)|Dzielenie rozmiaru wskaźnika|
|[C6385](../code-quality/c6385.md)|Przepełnienie odczytu|
|[C6386](../code-quality/c6386.md)|Przepełnienie zapisu|
|[C6387](../code-quality/c6387.md)|Nieprawidłowa wartość parametru|
|[C6388](../code-quality/c6388.md)|Nieprawidłowa wartość parametru|
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
|[C6995](../code-quality/c6995.md)|Nie można zapisać pliku dziennika XML|
|[C26100](../code-quality/c26100.md)|Sytuacja wyścigu|
|[C26101](../code-quality/c26101.md)|Niepowodzenie prawidłowo użyciu operacji blokowanej|
|[C26110](../code-quality/c26110.md)|Obiekt wywołujący nie utrzymuje blokady|
|[C26111](../code-quality/c26111.md)|Obiekt wywołujący nie zwolnił blokady|
|[C26112](../code-quality/c26112.md)|Obiekt wywołujący nie może utrzymywać żadnej blokady|
|[C26115](../code-quality/c26115.md)|Błąd zwolnienia blokady|
|[C26116](../code-quality/c26116.md)|Błąd nabycia lub utrzymuje blokady|
|[C26117](../code-quality/c26117.md)|Prawdopodobne zwalnianie nieuzyskanej blokady|
|[C26140](../code-quality/c26140.md)|Błąd adnotacji SAL współbieżności|
|[C28020](../code-quality/c28020.md)|Wyrażenie nie jest prawdziwe w tym wywołaniu|
|[C28021](../code-quality/c28021.md)|Parametr adnotacją musi być wskaźnikiem|
|[C28022](../code-quality/c28022.md)|Z klasami funkcji dla tej funkcji nie są zgodne z klasami funkcji w definicji typu użytej definiować go.|
|[C28023](../code-quality/c28023.md)|Funkcja jest przypisany lub przekazany powinny mieć _Function_class\_ adnotacji dla co najmniej jednej klasy|
|[C28024](../code-quality/c28024.md)|Wskaźnik funkcji jest przypisywany do jest oznaczony za pomocą klasy funkcja, która nie jest zawarta w funkcji listy klasy.|
|[C28039](../code-quality/c28039.md)|Typ rzeczywistego parametru należy dokładnie zgodny z typem|
|[C28112](../code-quality/c28112.md)|Zmienna, który jest dostępny przez funkcję blokowaną, zawsze muszą być dostępne przez funkcję blokowaną.|
|[C28113](../code-quality/c28113.md)|Uzyskiwanie dostępu do zmiennej lokalnej przez funkcję blokowaną|
|[C28125](../code-quality/c28125.md)|Funkcja musi być wywołana z bloku try / except bloku|
|[C28137](../code-quality/c28137.md)|Argument zmiennej musi być zamiast tego stałą (literałem)|
|[C28138](../code-quality/c28138.md)|Argument w postaci stałej musi być zamiast tego zmienną|
|[C28159](../code-quality/c28159.md)|Rozważ użycie zamiast niej inną funkcję.|
|[C28160](../code-quality/c28160.md)|Błąd adnotacji|
|[C28163](../code-quality/c28163.md)|Funkcja nigdy nie powinna być wywoływana z bloku try / except bloku|
|[C28164](../code-quality/c28164.md)|Argument jest przekazywany do funkcji, która oczekuje wskaźnika do obiektu (nie wskaźnika do wskaźnika)|
|[C28182](../code-quality/c28182.md)|Wskaźnik usuwania odwołań o wartości NULL. Wskaźnik zawiera tę samą wartość NULL, tak jak innego wskaźnika.|
|[C28183](../code-quality/c28183.md)|Argument może być jedną wartością i jest kopią wartości znalezionej we wskaźniku|
|[C28193](../code-quality/c28193.md)|Zmienna przechowuje wartość, która musi być zbadana|
|[C28196](../code-quality/c28196.md)|To wymaganie nie został spełniony. (Wyrażenie nie zwraca wartość true.)|
|[C28202](../code-quality/c28202.md)|Niedozwolone odwołanie do niestatycznego elementu członkowskiego|
|[C28203](../code-quality/c28203.md)|Niejednoznaczne odwołanie do elementu członkowskiego klasy.|
|[C28205](../code-quality/c28205.md)|_Success\_ lub _On_failure\_ używane w niedozwolonym kontekście|
|[C28206](../code-quality/c28206.md)|Lewy argument operacji wskazuje na strukturę, użyj "->"|
|[C28207](../code-quality/c28207.md)|Lewy argument operacji jest strukturą, użyj "."|
|[C28209](../code-quality/c28209.md)|Deklaracja symbolu ma sprzeczną deklarację|
|[C28210](../code-quality/c28210.md)|Adnotacje dla kontekstu __on_failure nie może być w jawnym kontekście wstępnym|
|[C28211](../code-quality/c28211.md)|Nazwy kontekstu statycznego dla SAL_context|
|[C28212](../code-quality/c28212.md)|Oczekiwano wyrażenia wskaźnikowego dla adnotacji|
|[C28213](../code-quality/c28213.md)|_Use_decl_annotations\_ adnotacji musi być używany do odwołania, bez żadnych modyfikacji, wcześniejszej deklaracji.|
|[C28214](../code-quality/c28214.md)|Nazwy parametrów atrybutu muszą być: p1... p9|
|[C28215](../code-quality/c28215.md)|Nie można zastosować elementu typefix do parametru, który ma już typefix.|
|[C28216](../code-quality/c28216.md)|Adnotacja checkReturn dotyczy tylko dla parametru określoną funkcję.|
|[C28217](../code-quality/c28217.md)|Dla funkcji liczbę parametrów dla adnotacji nie odpowiada znalezionej w pliku|
|[C28218](../code-quality/c28218.md)|Dla parametru funkcji parametru adnotacji nie odpowiada znalezionej w pliku|
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
|[C28244](../code-quality/c28244.md)|Adnotacja dla funkcji jest niemożliwy do przeanalizowania parametr/zewnętrzna adnotacja|
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
|[C28306](../code-quality/c28306.md)|Adnotacja parametru jest przestarzała|
|[C28307](../code-quality/c28307.md)|Adnotacja parametru jest przestarzała|
|[C28350](../code-quality/c28350.md)|Adnotacja opisuje sytuację, której nie można zastosować warunkowo.|
|[C28351](../code-quality/c28351.md)|Adnotacja opisano, w której wartość dynamiczna (zmienna) nie można użyć w tym stanie.|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typy, które posiadają pola usuwalne powinny być usuwalne|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Poprawnie Zadeklaruj procedury obsługi zdarzeń|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Oznacz zestawy atrybutem Assemblyversion|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Metody interfejsu powinny móc zostać wywołane przez typy podrzędne|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Typy, które posiadają natywne zasoby powinny być usuwalne|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Przenieś P/Invokes do klasy NativeMethods|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Nie ukrywaj metod klasy podstawowej|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Prawidłowo zaimplementować interfejs IDisposable|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Nie zgłaszaj wyjątków w nieoczekiwanych lokalizacjach|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Należy unikać duplikowania akceleratorów|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Punkty wejścia P/Invoke powinny istnieć|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invoke nie powinny być widoczne|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Typy z automatycznym układem nie powinny być widoczne dla modelu COM|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Wywołać GetLastError natychmiast po P/Invoke|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Typy podstawowe typu widocznego modelu COM powinny być widoczne dla modelu COM|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Metody rejestracji modelu COM powinny być zgodne.|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Poprawnie zadeklarować P/Invoke|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Usuń puste finalizatory|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Pola typu wartości powinny być przenośne|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Deklaracje P/Invoke powinny być przenośne|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Nie blokuj obiektów o słabej tożsamości|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Sprawdź zapytania SQL w poszukiwaniu luk w zabezpieczeniach|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Określ kierowanie dla argumentów ciągu P/Invoke|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Przejrzyj zabezpieczenia deklaratywne dla typów wartości|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Wskaźniki nie powinny być widoczne|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Zabezpieczone typy nie powinny ujawniać pól|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Zabezpieczenie metody powinno być nadzbiorem typu|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Metody z atrybutem APTCA powinny wywoływać tylko metody APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Typy APTCA powinny rozszerzać tylko typy bazowe APTCA|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Nie ujawniaj pośrednio metod żądaniami linkdemand|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Zastąpienie powinny być identyczne z bazowym|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Opakuj podatne na koniec spróbuj klauzule zewnętrzne|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Typ żądań konsolidacji wymaga żądań dziedziczenia|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Typy krytyczne dla zabezpieczeń nie może uczestniczyć w równoważnikach typów|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Konstruktory domyślne muszą być co najmniej tak ważne, jak podstawowe konstruktory domyślne|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegatów należy powiązać z metodami ze spójną jawnością|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Metody muszą przechowywać spójną jawność podczas nadpisywania metod bazowych|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Jawne metody muszą zawierać tylko weryfikowalne IL|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Jawne metody nie mogą wywoływać metod z atrybutem suppressunmanagedcodesecurity|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Kod o przezroczystym nie może odwoływać się elementów krytycznych dla zabezpieczeń|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Jawne metody nie mogą spełniać LinkDemands|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Typy muszą być co najmniej tak ważne, jak ich typy podstawowe i interfejsy|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Jawne metody nie mogą używać zabezpieczeń potwierdzeń|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Jawne metody nie mogą wywoływać kodu natywnego|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Ponownie, aby zachować szczegóły stosu|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Nie Likwiduj wielokrotnie obiektów|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Inicjowanie pól statycznych typu wartościowego|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Nie należy oznaczać obsługiwanych składników znacznikiem WebMethod|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Pola usuwalne powinny zostać usunięte.|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Nie należy wywoływać nadpisywalnych metod w konstruktorach|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Typy usuwalne powinny deklarować finalizator|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Finalizatory powinny wywoływać finalizator klasy podstawowej|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Zaimplementować konstruktory serializacji|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Przeciąż operator equals przy zastępowaniu ValueType.Equals|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Punkty wejścia formularzy systemu Windows Oznacz za pomocą STAThread|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Oznaczyć wszystkie nieserializowane pola|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Wywołanie metod klasy podstawowej typu ISerializable|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Oznacz typy ISerializable atrybutem SerializableAttribute|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Poprawnie Implementuj metody serializacji|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Poprawnie zaimplementować ISerializable|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Podaj poprawne argumenty metod formatowania|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Testowania poprawnie liczby (NaN)|