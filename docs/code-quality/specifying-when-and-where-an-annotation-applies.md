---
title: Określanie warunków pojawiania się adnotacji
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 9d99ebce3adc27039763e11ed4882a20199e8469
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>Określanie warunków pojawiania się adnotacji
W przypadku warunkowego adnotacji może wymagać innych adnotacji, aby określić, że do analizatora.  Na przykład, jeśli funkcja zmiennej, która może być synchroniczna lub asynchroniczna, funkcja działa w następujący sposób: W przypadku synchroniczne on zawsze ostatecznie zakończy się pomyślnie, ale w przypadku asynchroniczne go zgłasza błąd, jeśli nie powiedzie się natychmiast. Gdy funkcja jest wywoływana synchronicznie, sprawdzanie wartości wynik nie określa żadnej wartości do analizatora kodu, ponieważ nie będzie musiał zwrócić.  Jednak gdy funkcja jest wywoływana asynchronicznie, a wynik funkcji nie jest zaznaczone, może wystąpić po poważnym błędzie. W tym przykładzie pokazano sytuację, w której można użyć `_When_` adnotacji — opisane w dalszej części tego artykułu — Aby włączyć sprawdzanie.

## <a name="structural-annotations"></a>Adnotacje strukturalnych
 Aby kontrolować, kiedy i gdzie Zastosuj adnotacje, użyj następujących adnotacje strukturalnych.

|Adnotacja|Opis|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr` to wyrażenie zwracające l-wartością. Adnotacje w `anno-list` są stosowane do obiektu o nazwie przez `expr`. Dla każdego wpisu `anno-list`, `expr` jest interpretowana w warunku wstępnego, czy adnotacja jest interpretowane w warunku wstępnego, a w przypadku warunku po adnotacja jest w stanie po.|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` to wyrażenie zwracające l-wartością. Adnotacje w `anno-list` są stosowane do obiektu o nazwie przez `expr`. Dla każdego wpisu `anno-list`, `expr` jest interpretowana w warunku wstępnego, czy adnotacja jest interpretowane w warunku wstępnym, a w przypadku warunku po adnotacja jest w stanie po.<br /><br /> `iter` to nazwa zmiennej, która jest zakresem adnotacji (inclusive z `anno-list`). `iter` niejawne typ `long`. Zmienne o identycznej nazwie w dowolnym otaczającym zakresie są ukryte przed oceny.<br /><br /> `elem-count` to wyrażenie obliczane do wartości całkowitej.|
|`_Group_(anno-list)`|Adnotacje w `anno-list` są wszystkie uznana za wszelkie kwalifikatora dotyczy adnotacji grupy, która jest stosowana do każdej adnotacji.|
|`_When_(expr, anno-list)`|`expr` to wyrażenie, które mogą być konwertowane na `bool`. Jeśli jest niezerowa (`true`), adnotacje, które są określone w `anno-list` są uznawane za odpowiednie.<br /><br /> Domyślnie dla każdego wpisu `anno-list`, `expr` jest interpretowana jako przy użyciu wartości wejściowej, jeśli adnotacja jest warunku wstępnego, a jako przy użyciu wartości danych wyjściowych, jeśli adnotacja po warunku. Aby zastąpić domyślną, można użyć `_Old_` wewnętrzne podczas oceny po warunku, aby wskazać, że wartości wejściowe powinny być używane. **Uwaga:** różnych adnotacje może być włączone w wyniku przy użyciu `_When_` Jeśli wartość modyfikowalną — na przykład `*pLength`— uczestniczy ponieważ obliczony wynik `expr` w warunku wstępnym może różnić się od jego ocenione wynikiem po warunku.|

## <a name="see-also"></a>Zobacz też
 [Korzystanie z adnotacji SAL w celu redukowanie defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [opis SAL](../code-quality/understanding-sal.md) [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md) [.zachowaniefunkcjidodawaniaadnotacji](../code-quality/annotating-function-behavior.md) [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md) [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md) [funkcje wewnętrzne](../code-quality/intrinsic-functions.md) [najlepsze praktyki i przykłady](../code-quality/best-practices-and-examples-sal.md)