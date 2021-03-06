---
title: Zestaw reguł macierzystych reguł zalecanych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d845b5a-1b75-4e9d-861a-7c59cb7752af
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 345acf57686f57c79aa0d40ed5fdbf288475b156
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682747"
---
# <a name="native-recommended-rules-rule-set"></a>Zestaw reguł macierzystych reguł zalecanych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [zestaw reguł macierzystych reguł zalecanych](https://docs.microsoft.com/visualstudio/code-quality/native-recommended-rules-rule-set).  
  
Aktywność macierzystych reguł zalecanych i najpoważniejszych problemów w kodzie natywnym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji.  Należy dołączyć ten zestaw reguł każdego niestandardowego zestawu reguł tworzonego dla projektów natywnych.  Ten zestaw reguł jest przeznaczona do pracy z Visual Studio Professional edition lub nowszy.  
  
|Reguła|Opis|  
|----------|-----------------|  
|[C6001](../code-quality/c6001.md)|Używanie niezainicjowanej pamięci|  
|[C6011](../code-quality/c6011.md)|Wyłuskanie wskaźnika o wartości Null|  
|[C6029](../code-quality/c6029.md)|Użycie wartości typu Unchecked|  
|[C6031](../code-quality/c6031.md)|Zignorowano zwróconą wartość|  
|[C6053](../code-quality/c6053.md)|Zakończenie zerem z wywołania|  
|[C6054](../code-quality/c6054.md)|Brak zakończenia zerem|  
|[C6059](../code-quality/c6059.md)|Złe łączenie|  
|[C6063](../code-quality/c6063.md)|Brak argumentu ciągu w funkcji formatującej|  
|[C6064](../code-quality/c6064.md)|Brak argumentu całkowitego dla funkcji formatującej|  
|[C6066](../code-quality/c6066.md)|Brak argumentu będącego wskaźnikiem w funkcji formatującej|  
|[C6067](../code-quality/c6067.md)|Brak argumentu będącego wskaźnikiem ciągu w funkcji formatującej|  
|[C6101](../code-quality/c6101.md)|Zwracanie niezainicjowanej pamięci|  
|[C6200](../code-quality/c6200.md)|Indeks przekracza maksimum dla bufora|  
|[C6201](../code-quality/c6201.md)|Indeks przekracza maksimum dla bufora stosu|  
|[C6214](../code-quality/c6214.md)|Nieprawidłowe rzutowanie HRESULT na BOOL|  
|[C6215](../code-quality/c6215.md)|Nieprawidłowe rzutowanie BOOL na HRESULT|  
|[C6216](../code-quality/c6216.md)|Nieprawidłowe wstawione przez kompilator rzutowanie BOOL na HRESULT|  
|[C6217](../code-quality/c6217.md)|Nieprawidłowa wartość HRESULT testu z użyciem NOT|  
|[C6220](../code-quality/c6220.md)|Porównanie nieprawidłową HRESULT z -1|  
|[C6226](../code-quality/c6226.md)|Przypisanie nieprawidłowy HRESULT do -1|  
|[C6230](../code-quality/c6230.md)|Nieprawidłowa wartość HRESULT używany jako atrybut typu wartość logiczna|  
|[C6235](../code-quality/c6235.md)|Stała niezerowa z logiczny — lub|  
|[C6236](../code-quality/c6236.md)|Logiczny — lub Non-Zero Constant|  
|[C6237](../code-quality/c6237.md)|Zero z logiczny — i nie traci efekty uboczne|  
|[C6242](../code-quality/c6242.md)|Wymuszono rozwinięcie lokalne|  
|[C6248](../code-quality/c6248.md)|Tworzenie pustego DACL|  
|[C6250](../code-quality/c6250.md)|Nie zwolnione deskryptory adresów|  
|[C6255](../code-quality/c6255.md)|Niechronione użycie Alloca|  
|[C6258](../code-quality/c6258.md)|Za pomocą zakończenie wątku|  
|[C6259](../code-quality/c6259.md)|Dead kod bitowy — lub ograniczone przełącznika|  
|[C6260](../code-quality/c6260.md)|Użycie arytmetyki bajtów|  
|[C6262](../code-quality/c6262.md)|Nadmierne użycie stosu|  
|[C6263](../code-quality/c6263.md)|Używanie Alloca w pętli|  
|[C6268](../code-quality/c6268.md)|Brak nawiasów w rzutowaniu|  
|[C6269](../code-quality/c6269.md)|Wyłuskanie wskaźnika ignorowane|  
|[C6270](../code-quality/c6270.md)|Brak argumentu typu Float w funkcji formatującej|  
|[C6271](../code-quality/c6271.md)|Dodatkowy Argument w funkcji formatującej|  
|[C6272](../code-quality/c6272.md)|Argument niż typu Float w funkcji formatującej|  
|[C6273](../code-quality/c6273.md)|Argumen nie jest liczbą całkowitą w funkcji formatującej|  
|[C6274](../code-quality/c6274.md)|-Znakowy argumentu funkcji formatującej|  
|[C6276](../code-quality/c6276.md)|Nieprawidłowe rzutowanie ciągu|  
|[C6277](../code-quality/c6277.md)|Nieprawidłowe wywołanie funkcji CreateProcess|  
|[C6278](../code-quality/c6278.md)|Niezgodność Array New i operatora skalarnego Delete|  
|[C6279](../code-quality/c6279.md)|Niezgodność operatora skalarnego New Array Delete|  
|[C6280](../code-quality/c6280.md)|Niezgodność przydzielenia i cofnięcia przydziału pamięci|  
|[C6281](../code-quality/c6281.md)|Pierwszeństwo operacji bitowej i relacji|  
|[C6282](../code-quality/c6282.md)|Przypisanie zastępuje Test|  
|[C6283](../code-quality/c6283.md)|Pierwotny niezgodność Array New i operatora skalarnego Delete|  
|[C6284](../code-quality/c6284.md)|Nieprawidłowy Argument obiektu dla funkcji formatującej|  
|[C6285](../code-quality/c6285.md)|Logiczny — lub stałych|  
|[C6286](../code-quality/c6286.md)|Różna od zera logiczny — lub utraty efekty uboczne|  
|[C6287](../code-quality/c6287.md)|Zbędny Test|  
|[C6288](../code-quality/c6288.md)|Wzajemne włączenie nad logiczny — i ma wartość False|  
|[C6289](../code-quality/c6289.md)|Wzajemne wykluczenie nad logiczny — lub ma wartość True|  
|[C6290](../code-quality/c6290.md)|Bitowe or logiczne Not- i pierwszeństwo|  
|[C6291](../code-quality/c6291.md)|Bitowe or logiczne Not- lub priorytetu|  
|[C6292](../code-quality/c6292.md)|Pętla zlicza w górę od wartości maksymalnej|  
|[C6293](../code-quality/c6293.md)|Pętla zlicza w dół zaczynając od Minimum|  
|[C6294](../code-quality/c6294.md)|Wnętrze pętli nigdy wykonywane|  
|[C6295](../code-quality/c6295.md)|Pętla nieskończona|  
|[C6296](../code-quality/c6296.md)|Pętli wykonane jedynie raz|  
|[C6297](../code-quality/c6297.md)|Wynik przesunięcia rzutowane na większy rozmiar|  
|[C6299](../code-quality/c6299.md)|Bitfield do porównania logiczna|  
|[C6302](../code-quality/c6302.md)|Nieprawidłowy argument będący ciągiem znaków funkcji formatującej|  
|[C6303](../code-quality/c6303.md)|Argument ciągu nieprawidłowych znaków dwubajtowych w funkcji formatującej|  
|[C6305](../code-quality/c6305.md)|Niezgodny rozmiaru i korzystania z liczby|  
|[C6306](../code-quality/c6306.md)|Nieprawidłowy Argument zmiennej, wywołanie funkcji|  
|[C6308](../code-quality/c6308.md)|Przeciek Realloc|  
|[C6310](../code-quality/c6310.md)|Stała w filtrze wyjątków niedozwolone|  
|[C6312](../code-quality/c6312.md)|Wyjątek powoduje kontynuację wykonywania pętli|  
|[C6314](../code-quality/c6314.md)|Bitowe or- lub priorytetu|  
|[C6317](../code-quality/c6317.md)|Dopełnienie not Not|  
|[C6318](../code-quality/c6318.md)|Wyjątek powoduje kontynuację wyszukiwania|  
|[C6319](../code-quality/c6319.md)|Ignorowane przez przecinkami|  
|[C6324](../code-quality/c6324.md)|Kopia ciągu zamiast porównania ciągu|  
|[C6328](../code-quality/c6328.md)|Potencjalna niezgodność typu argumentu|  
|[C6331](../code-quality/c6331.md)|Flagi VirtualFree nieprawidłowy|  
|[C6332](../code-quality/c6332.md)|VirtualFree nieprawidłowy parametr|  
|[C6333](../code-quality/c6333.md)|VirtualFree nieprawidłowy rozmiar|  
|[C6335](../code-quality/c6335.md)|Przeciek uchwytu procesu|  
|[C6381](../code-quality/c6381.md)|Brak informacji o zamykaniu|  
|[C6383](../code-quality/c6383.md)|Liczba elementów bajt — liczba przepełnienie buforu|  
|[C6384](../code-quality/c6384.md)|Dzielenie rozmiaru wskaźnika|  
|[C6385](../code-quality/c6385.md)|Przepełnienie podczas odczytu|  
|[C6386](../code-quality/c6386.md)|Przepełnienie podczas zapisu|  
|[C6387](../code-quality/c6387.md)|Nieprawidłowa wartość parametru|  
|[C6388](../code-quality/c6388.md)|Nieprawidłowa wartość parametru|  
|[C6500](../code-quality/c6500.md)|Nieprawidłowa właściwość atrybutu|  
|[C6501](../code-quality/c6501.md)|Wartości właściwości atrybutów powodujące konflikt|  
|[C6503](../code-quality/c6503.md)|Odwołania nie może mieć wartości Null|  
|[C6504](../code-quality/c6504.md)|Wartość null na nie będącego wskaźnikiem|  
|[C6505](../code-quality/c6505.md)|MustCheck dla typu Void|  
|[C6506](../code-quality/c6506.md)|Rozmiar buforu dla elementu nie będącego wskaźnikiem lub tablicy|  
|[C6507](http://msdn.microsoft.com/en-us/18f88cd1-d035-4403-a6a4-12dd0affcf21)|Wartość null niezgodności w Wyłuskania Zero|  
|[C6508](../code-quality/c6508.md)|Dostęp do zapisu dla stałej|  
|[C6509](../code-quality/c6509.md)|Użyto Return w warunku wstępnym|  
|[C6510](../code-quality/c6510.md)|Zakończenie wartością null dla nie będącego wskaźnikiem|  
|[C6511](../code-quality/c6511.md)|MustCheck musi być tak lub nie|  
|[C6513](../code-quality/c6513.md)|Rozmiar elementu bez rozmiar bufora|  
|[C6514](../code-quality/c6514.md)|Rozmiar buforu przekracza rozmiar tablicy|  
|[C6515](../code-quality/c6515.md)|Rozmiar buforu dla elementu nie będącego wskaźnikiem|  
|[C6516](../code-quality/c6516.md)|Brak właściwości dla atrybutu|  
|[C6517](../code-quality/c6517.md)|Nieprawidłowy rozmiar dla bufora bez możliwości odczytu|  
|[C6518](../code-quality/c6518.md)|Rozmiar obszaru do zapisu dla bufora bez możliwości zapisu|  
|[C6519](http://msdn.microsoft.com/en-us/2b6326b0-0539-4d26-8fb1-720114933232)|Nieprawidłowa adnotacja: wartość właściwości "NeedsRelease" musi być tak lub nie|  
|[C6521](http://msdn.microsoft.com/en-us/e98d0ae3-6f13-47b2-9a15-15d4055af9ef)|Nieprawidłowy rozmiar ciągu Wyłuskania|  
|[C6522](../code-quality/c6522.md)|Nieprawidłowy typ ciągu rozmiaru|  
|[C6523](http://msdn.microsoft.com/en-us/11397a31-b224-46b0-afb7-d49ca576a3bb)|Nieprawidłowy rozmiar parametru ciągu|  
|[C6525](../code-quality/c6525.md)|Nieosiągalna lokalizacja ciągu nieprawidłowy rozmiar|  
|[C6526](http://msdn.microsoft.com/en-us/59c590c7-0098-4166-a1ac-87f324596002)|Nieprawidłowy typ ciągu rozmiaru buforu|  
|[C6527](../code-quality/c6527.md)|Nieprawidłowa adnotacja: właściwość "NeedsRelease" nie może być używana dla wartości typu void|  
|[C6530](../code-quality/c6530.md)|Nierozpoznany styl ciągu formatu|  
|[C6540](../code-quality/c6540.md)|Użycie adnotacji atrybutów dla tej funkcji spowoduje unieważnienie wszystkich istniejących adnotacji __declspec|  
|[C6551](../code-quality/c6551.md)|Nieprawidłowa specyfikacja rozmiaru: nie można przeanalizować wyrażenia|  
|[C6552](../code-quality/c6552.md)|Nieprawidłowe wyrażenie Deref = lub Notref =: nie można przeanalizować wyrażenia|  
|[C6701](../code-quality/c6701.md)|Wartość nie jest prawidłową wartością Yes/No/Maybe|  
|[C6702](../code-quality/c6702.md)|Wartość nie jest wartością ciągu|  
|[C6703](../code-quality/c6703.md)|Wartość nie jest liczbą|  
|[C6704](../code-quality/c6704.md)|Nieoczekiwany błąd adnotacji wyrażenia|  
|[C6705](../code-quality/c6705.md)|Oczekiwana liczba argumentów dla adnotacji nie jest zgodna z rzeczywistą liczbę argumentów dla adnotacji|  
|[C6706](../code-quality/c6706.md)|Nieoczekiwany błąd adnotacji dla adnotacji|  
|[C6995](../code-quality/c6995.md)|Nie można zapisać pliku dziennika XML|  
|[C26100](../code-quality/c26100.md)|Sytuacja wyścigu|  
|[C26101](../code-quality/c26101.md)|Niepowodzenie użycia operacji prawidłowo|  
|[C26110](../code-quality/c26110.md)|Obiekt wywołujący nie utrzymuje blokady|  
|[C26111](../code-quality/c26111.md)|Obiekt wywołujący nie zwolnił blokady|  
|[C26112](../code-quality/c26112.md)|Obiekt wywołujący nie może utrzymywać żadnej blokady|  
|[C26115](../code-quality/c26115.md)|Niepowodzenie zwolnienia blokady|  
|[C26116](../code-quality/c26116.md)|Błąd nabycia lub wstrzymać blokady|  
|[C26117](../code-quality/c26117.md)|Zwalnianie nie utrzymywanej blokady|  
|[C26140](../code-quality/c26140.md)|Błąd adnotacji SAL współbieżności|  
|[C28020](../code-quality/c28020.md)|Wyrażenie jest prawdziwe w tym wywołaniu|  
|[C28021](../code-quality/c28021.md)|Parametr, którego dodawana jest adnotacja, musi być wskaźnikiem|  
|[C28022](../code-quality/c28022.md)|Klasy(-a) funkcji dla tej funkcji nie pasują do klas(-y) funkcji, dotyczących typedef, używanych do definiowania go.|  
|[C28023](../code-quality/c28023.md)|Jest przypisywana lub przekazywana funkcja powinna mieć _Function_class\_ adnotacja dla co najmniej jednej klasy|  
|[C28024](../code-quality/c28024.md)|Przypisany wskaźnik funkcji jest oznaczony za pomocą klasy funkcja, która nie znajduje się na liście klas funkcji.|  
|[C28039](../code-quality/c28039.md)|Typ rzeczywistego parametru musi być dokładnie dopasowany typ|  
|[C28112](../code-quality/c28112.md)|Zmienna, która jest dostępna za pośrednictwem funkcji Interlocked musi być zawsze dostępna za pośrednictwem funkcji Interlocked.|  
|[C28113](../code-quality/c28113.md)|Uzyskiwanie dostępu do zmiennej lokalnej za pośrednictwem funkcji Interlocked|  
|[C28125](../code-quality/c28125.md)|Funkcja musi być wywołana z w ramach bloku try / except bloku|  
|[C28137](../code-quality/c28137.md)|Argument w postaci zmiennej musi być zamiast tego stałą (literałem)|  
|[C28138](../code-quality/c28138.md)|Argument w postaci stałej musi być zamiast tego zmienną|  
|[C28159](../code-quality/c28159.md)|Rozważ użycie innej funkcji.|  
|[C28160](../code-quality/c28160.md)|Błąd adnotacji|  
|[C28163](../code-quality/c28163.md)|Funkcja nigdy nie powinna być wywoływana z, w bloku try / except bloku|  
|[C28164](../code-quality/c28164.md)|Argument jest przekazywany do funkcji, która oczekuje wskaźnika do obiektu (nie wskaźnika do wskaźnika)|  
|[C28182](../code-quality/c28182.md)|Wyłuskanie wskaźnika o wartości NULL. Wskaźnik zawiera tę samą wartość NULL, tak jak innego wskaźnika.|  
|[C28183](../code-quality/c28183.md)|Argument może być jedną wartością i jest kopią wartości znalezionej we wskaźniku|  
|[C28193](../code-quality/c28193.md)|Zmienna zawiera wartość, która musi zostać zbadana|  
|[C28196](../code-quality/c28196.md)|Wymaganie nie został spełniony. (Wyrażenie nie zwraca wartość true.)|  
|[C28202](../code-quality/c28202.md)|Niedozwolone odwołanie do niestatycznego elementu członkowskiego|  
|[C28203](../code-quality/c28203.md)|Niejednoznaczne odwołanie do składowej klasy.|  
|[C28205](../code-quality/c28205.md)|_Success\_ lub _On_failure\_ używane w niedozwolonym kontekście|  
|[C28206](../code-quality/c28206.md)|Lewy argument operacji wskazuje na strukturę, użyj opcji "->"|  
|[C28207](../code-quality/c28207.md)|Lewy operand jest strukturą, użyj "."|  
|[C28209](../code-quality/c28209.md)|Deklaracja symbolu ma sprzeczną deklarację|  
|[C28210](../code-quality/c28210.md)|Adnotacje dla kontekstu __on_failure nie może być w jawnym kontekście pre|  
|[C28211](../code-quality/c28211.md)|Oczekiwano nazwy kontekstu statycznego dla SAL_context|  
|[C28212](../code-quality/c28212.md)|Oczekiwano wyrażenia wskaźnikowego dla adnotacji|  
|[C28213](../code-quality/c28213.md)|_Use_decl_annotations\_ adnotacja musi być używana do odwołania, bez żadnych modyfikacji, wcześniejszej deklaracji.|  
|[C28214](../code-quality/c28214.md)|Nazwy parametrów atrybutów muszą być p1... p9|  
|[C28215](../code-quality/c28215.md)|Nie można zastosować elementu typefix parametr, który ma już typefix|  
|[C28216](../code-quality/c28216.md)|Adnotacja checkReturn dotyczy tylko warunków końcowych dla określonego parametru funkcji.|  
|[C28217](../code-quality/c28217.md)|Dla funkcji liczba parametrów dla adnotacji odpowiada znalezionej w pliku|  
|[C28218](../code-quality/c28218.md)|Dla paramteer funkcja adnotacji nie odpowiada znalezionej w pliku|  
|[C28219](../code-quality/c28219.md)|Element członkowski wyliczenia oczekiwał na adnotację parametru w adnotacji|  
|[C28220](../code-quality/c28220.md)|Wyrażenia typu całkowitego oczekiwana dla adnotacji parametru w adnotacji|  
|[C28221](../code-quality/c28221.md)|Oczekiwano wyrażenia ciągu dla parametru w adnotacji|  
|[C28222](../code-quality/c28222.md)|Oczekiwano __yes \__NIE, lub \__maybe oczekiwana dla adnotacji|  
|[C28223](../code-quality/c28223.md)|Nie odnaleziono oczekiwanego tokenu/identyfikatora dla adnotacji, parametr|  
|[C28224](../code-quality/c28224.md)|Adnotacja wymaga parametrów|  
|[C28225](../code-quality/c28225.md)|Nie znaleziono prawidłowej liczby wymaganych parametrów w adnotacji|  
|[C28226](../code-quality/c28226.md)|Adnotacja nie może być PrimOp (w bieżącej deklaracji)|  
|[C28227](../code-quality/c28227.md)|Adnotacja nie może być PrimOp (patrz Poprzednia deklaracja)|  
|[C28228](../code-quality/c28228.md)|Parametr adnotacji: nie można użyć typu w adnotacjach|  
|[C28229](../code-quality/c28229.md)|Adnotacja nie obsługuje parametrów|  
|[C28230](../code-quality/c28230.md)|Typ parametru nie ma składowej.|  
|[C28231](../code-quality/c28231.md)|Adnotacja jest prawidłowa tylko na tablicy|  
|[C28232](../code-quality/c28232.md)|Operatory pre, post i deref nie są stosowane do żadnej adnotacji|  
|[C28233](../code-quality/c28233.md)|Operatory pre, post i deref zostały zastosowane do bloku|  
|[C28234](../code-quality/c28234.md)|__at wyrażenie nie ma zastosowania do bieżącej funkcji|  
|[C28235](../code-quality/c28235.md)|Funkcja nie może występować samodzielnie jako adnotacja|  
|[C28236](../code-quality/c28236.md)|Nie można użyć adnotacji w wyrażeniu|  
|[C28237](../code-quality/c28237.md)|Adnotacja dla parametru nie jest już obsługiwana|  
|[C28238](../code-quality/c28238.md)|Adnotacja dla parametru ma więcej niż jedną wartość, stringValue i longValue. Użyj paramn = xxx|  
|[C28239](../code-quality/c28239.md)|Adnotacja dla parametru ma zarówno wartość, stringValue lub longValue; i paramn = xxx. Użyj tylko paramn = xxx|  
|[C28240](../code-quality/c28240.md)|Adnotacja dla parametru ma param2, ale nie ma param1|  
|[C28241](../code-quality/c28241.md)|Adnotacja dla funkcji na parametrze nie została rozpoznana.|  
|[C28243](../code-quality/c28243.md)|Adnotacja dla funkcji na parametrze, wymaga więcej wyłuskań niż pozwala właściwy adnotowany typ|  
|[C28244](../code-quality/c28244.md)|Adnotacja dla funkcji posiada adnotację parametru/zewnętrzną adnotację|  
|[C28245](../code-quality/c28245.md)|Adnotacja dla funkcji oznacza stosowanym "this" w innych — funkcji składowej|  
|[C28246](../code-quality/c28246.md)|Adnotacja parametru dla funkcji jest niezgodna z typem parametru|  
|[C28250](../code-quality/c28250.md)|Niespójna adnotacja dla funkcji: poprzednie wystąpienie zawiera błąd.|  
|[C28251](../code-quality/c28251.md)|Niespójna adnotacja dla funkcji: to wystąpienie posiada błąd.|  
|[C28252](../code-quality/c28252.md)|Niespójna adnotacja dla funkcji: parametr ma inne adnotacje, w tym wystąpieniu.|  
|[C28253](../code-quality/c28253.md)|Niespójna adnotacja dla funkcji: parametr ma inne adnotacje, w tym wystąpieniu.|  
|[C28254](../code-quality/c28254.md)|(dynamic_cast <>) nie jest obsługiwane w adnotacjach|  
|[C28262](../code-quality/c28262.md)|Znaleziono błąd składni w adnotacji w funkcji dla adnotacji|  
|[C28263](../code-quality/c28263.md)|Znaleziono błąd składni w warunkowej adnotacji dla wewnętrznych adnotacji|  
|[C28264](http://msdn.microsoft.com/en-us/bf6ea983-a06e-4752-a042-747a7dbf338c)|Wynikowe wartości listy muszą być stałymi.|  
|[C28267](../code-quality/c28267.md)|Znaleziono błąd składni w adnotacjach adnotacji w funkcji.|  
|[C28272](../code-quality/c28272.md)|Adnotacja dla funkcji, parametr podczas badania jest niespójny z deklaracją funkcji|  
|[C28273](../code-quality/c28273.md)|W przypadku funkcji są niespójne z deklaracją funkcji|  
|[C28275](../code-quality/c28275.md)|Parametr _Macro_value\_ ma wartość null|  
|[C28279](../code-quality/c28279.md)|Dla symbolu znaleziono "begin" bez pasującego "end"|  
|[C28280](../code-quality/c28280.md)|Dla symbolu element "end" znaleziono bez pasującego "begin"|  
|[C28282](../code-quality/c28282.md)|Ciągi formatu muszą znajdować się w warunkach wstępnych|  
|[C28285](../code-quality/c28285.md)|Dla funkcji, błąd składni w parametrze|  
|[C28286](../code-quality/c28286.md)|Dla funkcji, błąd składni w pobliżu końca|  
|[C28287](../code-quality/c28287.md)|Dla funkcji, błąd składni w _At\_adnotacji () (Nierozpoznana nazwa parametru)|  
|[C28288](../code-quality/c28288.md)|Dla funkcji, błąd składni w _At\_adnotacji () (Nieprawidłowa nazwa parametru)|  
|[C28289](../code-quality/c28289.md)|Dla funkcji: elementy ReadableTo lub WritableTo nie ma specyfikacji limitu jako parametru|  
|[C28290](../code-quality/c28290.md)|Adnotacja dla funkcji zawierających więcej obiektów zewnętrznych niż rzeczywista liczba parametrów|  
|[C28291](../code-quality/c28291.md)|Post null/notnull na poziomie deref 0 jest bez znaczenia dla funkcji.|  
|[C28300](../code-quality/c28300.md)|Argumenty operacji wyrażenia o niezgodnych typach dla operatora|  
|[C28301](../code-quality/c28301.md)|Brak adnotacji dla pierwszej deklaracji funkcji.|  
|[C28302](../code-quality/c28302.md)|Dodatkowe _deref —\_ operator znaleziono w adnotacji.|  
|[C28303](../code-quality/c28303.md)|Niejednoznaczny _deref —\_ operator znaleziono w adnotacji.|  
|[C28304](../code-quality/c28304.md)|Nieprawidłowo umieszczony _Notref\_ znaleziono operator zastosowany do tokenu.|  
|[C28305](../code-quality/c28305.md)|Wykryto błąd podczas analizowania tokenu.|  
|[C28306](../code-quality/c28306.md)|Adnotacja dla parametru jest przestarzała|  
|[C28307](../code-quality/c28307.md)|Adnotacja dla parametru jest przestarzała|  
|[C28350](../code-quality/c28350.md)|Adnotacja opisuje sytuację, która nie jest warunkowo stosowana.|  
|[C28351](../code-quality/c28351.md)|Adnotacja zawiera opis, gdy wartość dynamiczna (zmienna) nie można użyć w warunku.|



