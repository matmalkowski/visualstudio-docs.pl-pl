---
title: "Ostrzeżenia wydajności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.performancerules
helpviewer_keywords:
- warnings, performance
- performance warnings
- performance, warnings
- managed code analysis warnings, performance warnings
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: baf04adf4589f0809db6a2de2bedcc0efd0f6fcb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="performance-warnings"></a>Wydajność — Ostrzeżenia
Ostrzeżenia wydajności obsługi bibliotek wysokiej wydajności i aplikacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Reguła|Opis|  
|----------|-----------------|  
|[CA1800: Nie rzutuj niepotrzebnie](../code-quality/ca1800-do-not-cast-unnecessarily.md)|Zduplikowane rzutowania zmniejszają wydajność, zwłaszcza gdy rzutowania są wykonywane w niedużej iteracji.|  
|[CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801-review-unused-parameters.md)|Podpis metody zawiera parametr, który nie jest używany w jej treści.|  
|[CA1802: Używaj literałów wszędzie tam, gdzie jest to odpowiednie](../code-quality/ca1802-use-literals-where-appropriate.md)|Pole jest zadeklarowany jako statyczny i tylko do odczytu (Shared i tylko do odczytu w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) i został zainicjowany z wartością, która jest obliczanie w czasie kompilacji. Ponieważ wartość, która jest przypisana do pola docelowego jest obliczanie w czasie kompilacji, zmień deklarację typu const (Const w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) pola tak, aby wartość jest obliczana w czasie kompilacji zamiast w czasie wykonywania.|  
|[CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)|Nieużywane zmienne lokalne i niepotrzebne przydziały zwiększają rozmiar zestawu i zmniejszają wydajność.|  
|[CA1806: Nie ignoruj wyników metod](../code-quality/ca1806-do-not-ignore-method-results.md)|Zostanie utworzony nowy obiekt, ale nigdy nie jest używany, nosi nazwę metody, które tworzy i zwraca nowy ciąg i nowy ciąg nie jest nigdy używane lub składnik modelu COM (Object) lub P/Invoke — metoda zwraca wartość HRESULT lub kodu błędu, który nie jest nigdy używane.|  
|[CA1809: Unikaj zbyt wielu zmiennych lokalnych](../code-quality/ca1809-avoid-excessive-locals.md)|Typowa optymalizacja wydajności polega na przechowywaniu wartości w rejestrze procesora zamiast w pamięci, co określa się jako „rejestrowanie wartości”.  Aby zwiększyć szansę, że wszystkie zmienne lokalne są zarejestrowany, ograniczyć liczbę zmiennych lokalnych 64.|  
|[CA1810: Inicjuj pola statyczne typu referencyjnego śródwierszowo](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Podczas gdy typ deklaruje jawny, statyczny konstruktor, kompilator just in time (JIT) do każdej metody statycznej dodaje sprawdzenie i konstruktora wystąpienia, aby upewnić się, że konstruktor statyczny został wcześniej wywołany. Sprawdzenia konstruktora statycznego mogą obniżyć wydajność.|  
|[CA1811: Unikaj niewywoływanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)|Prywatny lub wewnętrzny elementu członkowskiego (poziomu zestawu) nie ma obiektów wywołujących w zestawie, nie jest wywoływany przez środowisko uruchomieniowe języka wspólnego i nie jest wywoływany przez obiekt delegowany.|  
|[CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Wystąpienie typu na poziomie zestawu nie jest tworzone przez kod w zestawie.|  
|[CA1813: Unikaj niezapieczętowanych atrybutów](../code-quality/ca1813-avoid-unsealed-attributes.md)|[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Biblioteki klas udostępnia metody do pobierania atrybutów niestandardowych. Domyślnie te metody wyszukują hierarchie dziedziczenia atrybutu. Plombowanie atrybutu eliminuje wyszukiwanie przez hierarchię dziedziczenia i może zwiększyć wydajność.|  
|[CA1814: Wybieraj tablice nieregularne zamiast wielowymiarowych](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Nieregularna tablica to ta, której elementy są tablicami. Tablice, które tworzą elementów może mieć różne rozmiary, które mogą skutkować nieużywanego mniej miejsca na niektóre zestawy danych.|  
|[CA1815: Przesłoń metodę equals i operator równości dla typów wartości](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Dla typów wartości dziedziczona implementacja operatora Equas wykorzystuje bibliotekę odbić i porównuje zawartość wszystkich pól. Odbicie jest obliczeniowo kosztowne, a porównanie równości każdego pola może być niepotrzebne. Jeśli można się spodziewać, że użytkownicy będą porównywać lub sortować wystąpienia lub używać wystąpień jako kluczy tabel haszowanych, typ wartości powinien implementować Equals.|  
|[CA1816: Wywołaj poprawnie metodę GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Metody, która jest implementacją metody Dispose nie wywołuje GC. Metodę SuppressFinalize lub metodę, która nie jest implementacją wywołania metody Dispose GC. Metodę SuppressFinalize lub metoda wywołuje GC. Metodę SuppressFinalize i przekazuje inną niż to (mnie [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).|  
|[CA1819: Właściwości nie powinny zwracać tablic](../code-quality/ca1819-properties-should-not-return-arrays.md)|Tablice, które są zwracane przez właściwości nie są zabezpieczony przed zapisem, nawet jeśli właściwość jest tylko do odczytu. Aby zachować tablicę odporną na manipulacje, właściwość musi zwracać kopię tablicy. Zwykle użytkownicy nie rozumieją, jakie niekorzystne następstwa dla wydajności ma wywołanie takiej właściwości.|  
|[CA1820: Testuj obecność pustych ciągów przy użyciu długości ciągu](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Porównywanie ciągów za pomocą właściwości String.Length lub metody String.IsNullOrEmpty jest znacznie szybsze niż użycie operatora Equals.|  
|[CA1821: Usuwaj puste finalizatory](../code-quality/ca1821-remove-empty-finalizers.md)|Jeśli to tylko możliwe, należy unikać finalizatorów ze względu na dodatkowe obciążenie, które bierze udział w śledzeniu okresu istnienia obiektu. Wiąże się z pustą finalizator dodane koszty bez żadnych korzyści.|  
|[CA1822: Oznaczaj składowe jako statyczne](../code-quality/ca1822-mark-members-as-static.md)|Elementy członkowskie, które nie uzyskują dostęp do wystąpienia danych lub wywołanie metody wystąpienia może być oznaczony jako statyczne (Shared w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Po oznaczeniu metod jako statyczne kompilator wygeneruje niewirtualne wywołania do tych członków. To może dać wymierny zysk wydajnościowy dla kodu wrażliwego na wydajność.|  
|[CA1823: Unikaj nieużywanych pól prywatnych](../code-quality/ca1823-avoid-unused-private-fields.md)|Zostały wykryte pola prywatne, które w zestawie nie są widoczne jako dostępne.|  
|[CA1824: Oznaczaj zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|Atrybut NeutralResourcesLanguage informuje ResourceManager języka, który był używany do wyświetlania zasobów neutralnej kultury dla zestawu. To zwiększa wydajność wyszukiwania dla pierwszego zasobu, który się ładuje i może zmniejszyć zestaw roboczy.|