---
title: "Funkcje wewnętrzne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _String_length_
- _Param_
- _Curr_
- _Old_
- _Nullterm_length_
- _Inexpressible_
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c25c76ba43c983a6029c8d50e183ccf839ef08bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="intrinsic-functions"></a>Funkcje wewnętrzne
Wyrażenie w SAL może być wyrażenie C/C++, pod warunkiem, że wyrażenie ma efekty uboczne — na przykład ++,--i mieć skutki uboczne w tym kontekście wywołania funkcji.  SAL zapewnia jednak niektóre obiekty typu funkcji i niektóre zastrzeżone symbole, których można używać w wyrażeniach SAL. Są one określane jako *funkcje wewnętrzne*.  
  
## <a name="general-purpose"></a>Ogólnego przeznaczenia  
 Następujące adnotacje funkcja instrinsic zapewniają ogólne narzędzie SAL.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|`_Curr_`|Synonim dla obiekt, który jest obecnie adnotacji.  Gdy `_At_` adnotacji jest w użyciu, `_Curr_` jest taka sama jak pierwszy parametr `_At_`.  W przeciwnym razie jest parametr lub wartość całej funkcji/powrotu, z którym jest skojarzona lexically adnotacji.|  
|`_Inexpressible_(expr)`|Wyrażenie w sytuacji, gdy rozmiar buforu jest zbyt złożone, aby reprezentować za pomocą wyrażenia adnotacji — na przykład, jeśli jest obliczana przez skanowanie wejściowy zestaw danych, a następnie zliczania wybranych składników.|  
|`_Nullterm_length_(param)`|`param`jest to liczba elementów w buforze do, ale nie włącznie z terminatorem null. Można stosować do dowolnego buforu typu niezagregowanym, inny niż void.|  
|`_Old_(expr)`|Gdy jest obliczane w warunku wstępnym, `_Old_` zwraca wartość wejściowa `expr`.  Podczas szacowania w po warunek, zwracana jest wartość `expr` będzie mieć obliczonego w warunku wstępnym.|  
|`_Param_(n)`|`n`Parametru do funkcji, licząc od 1 do `n`, i `n` jest literałem stałej całkowitej. Jeśli parametr ma nazwę, ta adnotacja jest identyczna jak uzyskiwanie dostępu do parametru według nazwy. **Uwaga:** `n` mogą odwoływać się do parametrów pozycyjnych, które są definiowane przez wielokropek lub mogą być używane w prototypy funkcji gdzie nazwy nie są używane.|  
|`return`|C/C++ zastrzeżone słowa kluczowego `return` można użyć w wyrażeniu SAL wskaż wartość zwracaną przez funkcję.  Wartość jest dostępna tylko w stanie post; Błąd składni, aby użyć go w stan sprzed jest.|  
  
## <a name="string-specific"></a>Określonego ciągu  
 Następujące adnotacje Wewnętrzna funkcja Włącz manipulowanie ciągami. Wszystkie cztery funkcje te służą do celów tego samego: do zwrócenia z liczbą elementów typu, która znajduje się przed terminatorem null. Różnice są rodzaje danych w elementach, które są określone. Należy pamiętać, że jeśli chcesz określić długość zakończonym znakiem null buforu, który nie składa się z znaków, użyj `_Nullterm_length_(param)` adnotacji z poprzedniej sekcji.  
  
|Adnotacja|Opis|  
|----------------|-----------------|  
|`_String_length_(param)`|`param`jest to liczba elementów w ciągu maksymalnie, ale nie włącznie z terminatorem null. Ta adnotacja jest zarezerwowana dla typów "ciągu znaków".|  
|`strlen(param)`|`param`jest to liczba elementów w ciągu maksymalnie, ale nie włącznie z terminatorem null. Ta adnotacja jest zarezerwowany do użycia na znak stałych i podobny funkcja C Runtime [strlen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|  
|`wcslen(param)`|`param`jest to liczba elementów w ciągu maksymalnie (z wyjątkiem) terminatorem null. Ta adnotacja jest zarezerwowany do użycia na znaków typu wide stałych i podobny funkcja C Runtime [wcslen()](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l).|  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z adnotacji SAL w celu redukowanie defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Poznanie SAL](../code-quality/understanding-sal.md)   
 [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)   
 [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)   
 [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)   
 [Określanie, kiedy i gdzie dotyczy adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Najlepsze praktyki i przykłady](../code-quality/best-practices-and-examples-sal.md)