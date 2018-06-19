---
title: Zachowanie funkcji dodawania adnotacji
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _On_failure_
- _Return_type_success_
- _Always_
- _Maybe_raises_SEH_exception_
- _Raises_SEH_exception_
- _Called_from_function_class_
- _Function_class_
- _Must_inspect_result_
- _Success_
- _Check_return_
- _Use_decl_annotations_
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 7ee46c277574b9ceec2c4b0a26685570d305990f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31899358"
---
# <a name="annotating-function-behavior"></a>Zachowanie funkcji dodawania adnotacji
Oprócz Dodawanie adnotacji do [parametry funkcji i wartości zwracane](../code-quality/annotating-function-parameters-and-return-values.md), może dodawać adnotacje do właściwości całej funkcji.

## <a name="function-annotations"></a>Adnotacje — funkcja
 Następujące adnotacje dotyczą funkcji jako całość i opisano sposób zachowania lub oczekuje jako true.

|Adnotacja|Opis|
|----------------|-----------------|
|`_Called_from_function_class_(name)`|Nie ma na celu autonomicznie; Zamiast tego jest predykat ma być używany z `_When_` adnotacji. Aby uzyskać więcej informacji, zobacz [określenie podczas i gdzie adnotacji stosuje](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> `name` Parametr jest dowolny ciąg, który jest także wyświetlany w `_Function_class_` adnotacji w deklaracji niektórych funkcji.  `_Called_from_function_class_` Zwraca wartość niezerową, jeśli funkcję, która jest aktualnie analizowany jest adnotowany przy użyciu `_Function_class_` mający taką samą wartość `name`; w przeciwnym razie zwraca wartość zero.|
|`_Check_return_`|Oznacza wartość zwracaną i Stany wywołującego należy sprawdzić go. Narzędzie do sprawdzania zgłasza błąd, jeśli funkcja jest wywoływana w kontekście void.|
|`_Function_class_(name)`|`name` Parametr jest dowolny ciąg, który został wybrany przez użytkownika.  Istnieje w przestrzeni nazw, która różni się od innych przestrzeniach nazw. Funkcja, wskaźnik funkcji, lub — najbardziej korzyścią — typ wskaźnika funkcji mogą być oznaczone jako należące do co najmniej jedna klasa funkcji.|
|`_Raises_SEH_exception_`|Oznacza funkcję, która zawsze zgłasza wyjątek strukturalnej obsługi wyjątków strukturalnych, podlegają `_When_` i `_On_failure_` warunki. Aby uzyskać więcej informacji, zobacz [określenie podczas i gdzie adnotacji stosuje](../code-quality/specifying-when-and-where-an-annotation-applies.md).|
|`_Maybe_raises_SEH_exception_`|Oznacza funkcję, która opcjonalnie mogą zgłaszać wyjątek SEH podlega `_When_` i `_On_failure_` warunki.|
|`_Must_inspect_result_`|Oznacza dowolną wartością wyjściowego, w tym wartości zwracanej, parametry i zmienne globalne.  Analizatora zgłasza błąd, jeśli wartość w obiekcie adnotacjami niepoddane jest następnie inspekcji. "Inspekcji" obejmuje, czy jest używany w wyrażeniu warunkowym, jest przypisany do parametru wyjściowego lub globalnego lub jest przekazywana jako parametr.  Dla wartości zwracanych `_Must_inspect_result_` oznacza `_Check_return_`.|
|`_Use_decl_annotations_`|Może być używany w definicji funkcji (nazywanego także treści funkcji) zamiast listy adnotacje w nagłówku.  Gdy `_Use_decl_annotations_` jest używana, adnotacje, które znajdują się w nagłówku w zakresie dla tej samej funkcji są używane tak, jakby są również obecne w definicji, które ma `_Use_decl_annotations_` adnotacji.|

## <a name="successfailure-annotations"></a>Adnotacje powodzeń/niepowodzeń
 Funkcja może zakończyć się niepowodzeniem, i tak, wyniki mogą być niekompletne lub różnią się od wyników, gdy funkcja zakończy się pomyślnie.  Adnotacje na poniższej liście umożliwiają express zachowanie awarii.  Aby korzystać z tych adnotacji, należy włączyć je, aby określić Powodzenie; w związku z tym `_Success_` adnotacji jest wymagana.  Zwróć uwagę, że `NTSTATUS` i `HRESULT` już `_Success_` adnotacji wbudowane; jednak jeśli możesz określić własne `_Success_` adnotacji na `NTSTATUS` lub `HRESULT`, zastępuje on wbudowanych adnotacji.

|Adnotacja|Opis|
|----------------|-----------------|
|`_Always_(anno_list)`|Odpowiednikiem `anno_list _On_failure_(anno_list)`; oznacza to, że adnotacje w `anno_list` zastosować czy funkcja zakończy się pomyślnie.|
|`_On_failure_(anno_list)`|Ma być używany tylko wtedy, gdy `_Success_` służy również do adnotacji funkcja — albo jawnie lub niejawnie za pośrednictwem `_Return_type_success_` na jako element typedef. Gdy `_On_failure_` adnotacji jest obecny w funkcji lub wartość zwrotną, każdej adnotacji w `anno_list` (roku) zachowuje się tak, jakby był on zakodowane jako `_When_(!expr, anno)`, gdzie `expr` jest parametrem wymaganym `_Success_` adnotacji. Oznacza to, że domniemanych stosowania `_Success_` na wszystkie warunki po nie ma zastosowania do `_On_failure_`.|
|`_Return_type_success_(expr)`|Mogą być stosowane jako element TypeDef. Wskazuje, że wszystkie funkcje zwracające, wpisz i jawnie nie mają `_Success_` mają adnotacje, jak gdyby `_Success_(expr)`. `_Return_type_success_` Nie można użyć funkcji lub typedef wskaźnika funkcji.|
|`_Success_(expr)`|`expr` to wyrażenie zwracające r-wartości. Gdy `_Success_` adnotacji jest obecny w deklaracji funkcji lub definicji, każdej adnotacji (`anno`) w funkcji i w stanie po zachowuje się tak, jakby był on zakodowane jako `_When_(expr, anno)`. `_Success_` Adnotacji mogą być używane tylko w funkcji, nie na jego parametrów lub typ zwrotny. Może istnieć co najwyżej jedna `_Success_` adnotacja dla funkcji, a nie może być w dowolnym `_When_`, `_At_`, lub `_Group_`. Aby uzyskać więcej informacji, zobacz [określenie podczas i gdzie adnotacji stosuje](../code-quality/specifying-when-and-where-an-annotation-applies.md).|

## <a name="see-also"></a>Zobacz też
 [Korzystanie z adnotacji SAL w celu redukowanie defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [opis SAL](../code-quality/understanding-sal.md) [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md) [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md) [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md) [określenie, kiedy i gdzie dotyczy adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md) [funkcje wewnętrzne](../code-quality/intrinsic-functions.md) [najlepsze rozwiązania i Przykłady](../code-quality/best-practices-and-examples-sal.md)