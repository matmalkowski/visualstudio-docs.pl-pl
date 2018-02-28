---
title: "Błąd: Obliczania funkcji &#39; funkcja &#39; Upłynął limit czasu i wymagane przerwanie w sposób niebezpieczny | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ff5dedb9bf0ffe44ec1a7c031d4c1d0eeeea08ec
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Błąd: Obliczania funkcji &#39; funkcja &#39; Upłynął limit czasu i wymagane przerwanie w sposób unsafe

Pełny tekst komunikatu: obliczania funkcji "function" Upłynął limit czasu i konieczne jest przerwana w sposób niebezpieczny. Może to uszkodzony procesu docelowego. 

Aby ułatwić sprawdzić stan obiektów platformy .NET, debuger automatycznie spowoduje wymuszenie debugowanym procesie do uruchomienia dodatkowych kodu (zwykle metody pobierające właściwości i ToString funkcji). W większości przypadków wszystkie te funkcje są wykonywane szybko i znacznie ułatwia debugowanie. Jednak debuger nie uruchamianie aplikacji w bibliotece. W związku z tym metody pobierającej właściwości lub metody ToString, który odwołuje się do natywnej funkcji, która jest używana do może prowadzić do długich limitów czasu, który może nie być możliwe do odzyskania. Jeśli wystąpi ten komunikat o błędzie tego zdarzenia.
 
Jeden typową przyczyną tego problemu jest podczas debuger właściwość tylko możliwość inspekcji do wykonania wątku. Dlatego jeśli właściwość oczekuje na innych wątków, aby uruchomić wewnątrz debugowanej aplikacji i oczekuje w taki sposób, aby środowisko uruchomieniowe platformy .NET nie jest w stanie przerwania, ten problem nastąpi.
 
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd
 
Istnieją trzy możliwe rozwiązania tego problemu.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Rozwiązanie #1: Zapobiega debuger wywołanie metody pobierającej właściwości lub metody ToString
 
Komunikat o błędzie informuje o nazwę funkcji, który debuger próbował wywołać. Jeśli można modyfikować tej funkcji, można uniemożliwić wywoływanie metody pobierającej właściwości lub metody ToString debugera. Wypróbuj jedną z następujących czynności:
 
* Zmień metodę do innego typu kodu oprócz metody pobierającej właściwości lub metody ToString i problem zniknie.
    —lub—
* (W przypadku ToString) Zdefiniuj atrybutu DebuggerDisplay w typie i może mieć debugera ocenić inną niż ToString.
    —lub—
* (Dla metody pobierającej właściwości) Umieść `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` atrybutu dla właściwości. Może to być przydatne w przypadku metody, która musi znajdować się właściwości interfejsu API ze względu na zgodność, ale należy go naprawdę metody.
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>#2 — rozwiązanie: Kodu docelowego debugera, aby przerwać oceny poproś ma
 
Komunikat o błędzie informuje o nazwę funkcji, który debuger próbował wywołać. Jeśli metoda pobierająca właściwości lub metody ToString niepowodzenia by działała poprawnie, szczególnie w sytuacjach, gdy problem jest, które kodu wymaga innego wątku do uruchomienia kodu, a następnie wywołać funkcję implementacji `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` poprosić debugera abort — funkcja Obliczanie. W tym rozwiązaniu jest nadal możliwe jawnie oceny tych funkcji, ale domyślne zachowanie to zatrzyma wykonywanie podczas wywołania NotifyOfCrossThreadDependency.
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>Rozwiązanie #3: Wyłącz wszystkie oceny niejawne
 
Jeśli poprzednie rozwiązania nie rozwiązują problemu, przejdź do *narzędzia* > *opcje*i usuń zaznaczenie opcji *debugowanie*  >   *Ogólne* > *Włącz obliczanie właściwości i inne niejawne wywołania funkcji*. To spowoduje wyłączenie większości Obliczanie funkcji niejawne i powinno rozwiązać problem.



  
