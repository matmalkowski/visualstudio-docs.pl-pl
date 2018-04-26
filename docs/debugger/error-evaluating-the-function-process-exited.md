---
title: 'Błąd: Proces docelowy został zakończony z kodem &#39;kod&#39; podczas obliczania funkcji &#39;funkcja&#39; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 4/06/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5e9221ccf162180a89cc88b1ceebcf55be39eef
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>Błąd: Proces docelowy został zakończony z kodem &#39;kod&#39; podczas obliczania funkcji &#39;— funkcja&#39;

Pełny tekst komunikatu: Proces docelowy zostało zakończone przez kod "code" podczas obliczania funkcji "function".

Aby ułatwić sprawdzić stan obiektów platformy .NET, debuger automatycznie wymusza debugowanym procesie do uruchomienia dodatkowych kodu (zwykle metody pobierające właściwości i `ToString` funkcji). W większości przypadków te funkcje zakończyła się pomyślnie lub zgłaszają wyjątki, które mogą być przechwycony przez debuger. Istnieją jednak pewnych okolicznościach, w których nie można przechwycić wyjątki ponieważ między granicami jądra, wymagają przekazywania wiadomości użytkownika lub jest nieodwracalny. Jako wynik, metoda pobierająca właściwości lub metody ToString, która wykonuje kod dowolna jawnie kończy proces (na przykład `ExitProcess()`) lub zgłasza wyjątek Wystąpił nieobsługiwany wyjątek, który nie można przechwycić (na przykład `StackOverflowException`) zostanie zakończona debugowany proces i zakończenie sesji debugowania. Jeśli wystąpi ten komunikat o błędzie tego zdarzenia.
 
Jeden typową przyczyną tego problemu jest, że gdy debuger ocenia właściwość, która wywołuje się, co może spowodować wyjątek przepełnienia stosu. Nie można odzyskać wyjątek przepełnienia stosu i zakończy proces docelowy.
 
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd
 
Istnieją dwa możliwe rozwiązania tego problemu.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Rozwiązanie #1: Zapobiega debuger wywołanie metody pobierającej właściwości lub metody ToString 

Komunikat o błędzie informuje o nazwę funkcji, który debuger próbował wywołać. Nazwą funkcji, możesz spróbować ponownego obliczania tej funkcji z **Immediate** okno, aby debugować oceny. Debugowanie jest możliwe podczas obliczania z **Immediate** okna, ponieważ w odróżnieniu od niejawne obliczanie z **automatycznych/zmienne lokalne/oglądanie** systemu windows, debuger dzieli w przypadku nieobsługiwanych wyjątków.

Jeśli zmodyfikujesz tej funkcji, można zapobiec debuger podczas wywoływania metody pobierającej właściwości lub `ToString` metody. Wypróbuj jedną z następujących czynności:
 
* Zmień metodę do innego typu kodu oprócz metody pobierającej właściwości lub metody ToString i problem zniknie.
    —lub—
* (Dla `ToString`) Definiuj `DebuggerDisplay` atrybut na typ, może mieć debugera ocenić coś innego niż `ToString`.
    —lub—
* (Dla metody pobierającej właściwości) Umieść `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` atrybutu dla właściwości. Może to być przydatne w przypadku metody, która powinna być właściwości interfejsu API ze względu na zgodność, ale należy go naprawdę metody.

Jeśli nie można zmodyfikować tej metody, można przerwać proces docelowy w instrukcji alternatywny, a następnie spróbuj ponownie oceny.
 
### <a name="solution-2-disable-all-implicit-evaluation"></a>Rozwiązanie #2: Wyłącz wszystkie oceny niejawne
 
Jeśli poprzednie rozwiązania nie rozwiązują problemu, przejdź do **narzędzia** > **opcje**i usuń zaznaczenie opcji **debugowanie**  >   **Ogólne** > **Włącz obliczanie właściwości i inne niejawne wywołania funkcji**. To spowoduje wyłączenie większości Obliczanie funkcji niejawne i powinno rozwiązać problem.



  
