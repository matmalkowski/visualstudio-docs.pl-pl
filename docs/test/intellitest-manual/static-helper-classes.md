---
title: "Klasy statyczne pomocy | Narzędzie Test Microsoft IntelliTest dewelopera | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Static helper classes
ms.assetid: 1EE26913-E498-492E-BB90-BB0D6E8A097C
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: e429de9ae91f7899bbf936db7483006739d1404d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="static-helper-classes"></a>Klasy statyczne pomocy

IntelliTest zapewnia zbiór statyczną klasę pomocy używaną podczas tworzenia [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing):

* [PexAssume](#pexassume): umożliwia zdefiniowanie założeń na dane wejściowe i przydaje się do filtrowania niepożądanych danych wejściowych
* [PexAssert](#pexassert): klasy proste potwierdzenia do użycia, jeśli Twoje struktury testowej nie zawiera
* [PexChoose](#pexchoose): strumienia danych wejściowych dodatkowy test, zarządzanych przez program IntelliTest
* [PexObserve](#pexobserve): rejestruje konkretnych wartości i optionaly, weryfikuje je w wygenerowanym kodzie

Niektóre klasy umożliwiają interakcję z aparatem rozsądkiem IntelliTest w niskiego poziomu:

* [PexSymbolicValue](#pexsymbolicvalue): narzędzia Inspekcja lub modyfikowanie symboliczne ograniczenia dotyczące zmiennych

<a name="pexassume"></a>
## <a name="pexassume"></a>PexAssume

Klasa statyczna stosowany w celu założenia, takich jak [warunki wstępne](test-generation.md#precondition)w [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing).
Metody tej klasy można odfiltrować dane wejściowe testu niepożądane.

Jeśli nie ma warunku zakładanego niektórych testów danych wejściowych, **PexAssumeFailedException** jest generowany. To spowoduje, że test, aby dyskretnie zignorowane.

**Przykład**

Nie będzie uwzględniać następujące test sparametryzowany **j = 0**:

```
public void TestSomething(int i, int j) {
     PexAssume.AreNotEqual(j, 0);
     int k = i/j;
     ...
}
```

**Uwagi**

Powyższy kod jest niemal odpowiednikiem:

```
     if (j==0)
          return;
```

z wyjątkiem przerwane **PexAssume** powoduje żadnych przypadków testowych. W przypadku liczby **Jeśli** instrukcji IntelliTest generuje oddzielny przypadek testowy, aby pokrywał **następnie** gałęzi **Jeśli** instrukcji.

**PexAssume** zawiera również klasy specialzed zagnieżdżone dla założenia na ciąg, tablic i kolekcji.

<a name="pexassert"></a>
## <a name="pexassert"></a>PexAssert

Klasa statyczna stosowany w celu potwierdzenia, takich jak [postconditions](test-generation.md#postcondition)w [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing).

Jeśli warunek potwierdzona nie dysponuje dla niektórych testów danych wejściowych, **PexAssertFailedException** jest zgłaszany, co powoduje, że test, aby zakończyć się niepowodzeniem.

**Przykład**

Następujące potwierdza, że ma dodatnią wartość bezwzględna liczby całkowitej:

```
public void TestSomething(int i) {
     int j = Maths.Abs(i);
     PexAssert.IsTrue(j >= 0);
     ...
}
```

<a name="pexchoose"></a>
## <a name="pexchoose"></a>PexChoose

Statyczne klasy, która dostarcza pomocnicze wartości wejściowych do testu, który może służyć do zaimplementowania [sparametryzowana Mocks](input-generation.md#parameterized-mocks).

**PexChoose** klasy nie jest pomocne w określeniu, czy test przekazuje lub dla określonej wartości wejściowe. **PexChoose** po prostu zawiera wartości wejściowej, które są również nazywane *opcji*. Jest nadal użytkownika do ograniczania wartości wejściowych oraz do zapisywania potwierdzenia określające podczas testu przekazuje lub kończy się niepowodzeniem.

**Tryby pracy**

**PexChoose** klasy mogą pracować w dwóch trybach:

* Gdy IntelliTest wykonuje symboliczne analizy testu i przetestowanej kod podczas [wejściowych generowania](input-generation.md), wybór zwraca dowolne wartości i IntelliTest śledzi używania każdej wartości w teście i przetestowany kodu. IntelliTest wygeneruje odpowiednie wartości, aby wyzwolić wykonywanie różnych ścieżek w teście i przetestowany kodu.

* Wygenerowany kod dla konkretnego przypadków testowych konfiguruje dostawcy wybór w określony sposób, aby ponowne wykonanie przypadkiem testowym będzie podejmować decyzje określonych wyzwalanie wykonywania określonej ścieżki.

**Użycie**

* Proste wywołania **PexChoose.Value** aby wygenerować nową wartość:

```
public int Foo() {
    return PexChoose.Value<int>("foo");
}
```

<a name="pexobserve"></a>
## <a name="pexobserve"></a>PexObserve

Klasa statyczna logowania nazwanych wartości.

Gdy program IntelliTest Eksploruje kodu, **PexObserve** jest używana do rejestrowania obliczonych wartości przy użyciu ich oświadczenia sformatowanego ciągu. Wartości są skojarzone z unikatowe nazwy.

```
PexObserve.Value<string>("result", result);
```

**Przykład**

```
// product code
public static class MathEx {
     public static int Square(int value) { return value * value; }
}


// fixture
[TestClass]
public partial class MathExTests {
     [PexMethod]
     public int SquareTest(int a) {
        int result = MathEx.Square(a); 
        // storing result
        return result;
     }
}
```

<a name="pexsymbolicvalue"></a>
## <a name="pexsymbolicvalue"></a>PexSymbolicValue

Klasa statyczna używane do ignorowania ograniczenia dotyczące parametrów i drukowanie symboliczne informacji związanych z wartościami.

**Użycie**

Zwykle IntelliTest próbuje obejmują wszystkie ścieżki wykonywania kodu podczas wykonywania. Jednak szczególnie w przypadku przetwarzania założeń i potwierdzenia warunki, nie należy go Eksploruj wszystkich możliwych przypadków.

**Przykład**

Ten przykład przedstawia implementację **PexAssume.Arrays.ElementsAreNotNull** metody. W metodzie możesz zignorować ograniczenia długości tablicy wartości w celu uniknięcia IntelliTest próby generowania różne rozmiary tablicy. Ograniczenia są ignorowane, tylko w tym miejscu. Jeśli testowany kod zachowuje się inaczej dla długości tablicy różnych IntelliTest nie można wygenerować różnych tablic o rozmiarze z ograniczenia testowany kod.

```
public static void AreElementsNotNull<T>(T[] value)
    where T : class
{
    PexAssume.NotNull(value);
    // the followings prevents the exploration of all array lengths
    int len = PexSymbolicValue.Ignore<int>(value.Length);

    // building up a boolean value as follows prevents exploration
    // of all combinations of non-null (instead, there are just two cases)
    bool anyNull = false;
    for (int i = 0; i < len; ++i)
        anyNull |= value[i] == null;

    // was any element null?
    if (anyNull)
        PexAssume.Fail("some element of array is a null reference");
}
```

## <a name="got-feedback"></a>Masz opinię?

Publikowania własnych pomysłów i funkcji żądań na  **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
