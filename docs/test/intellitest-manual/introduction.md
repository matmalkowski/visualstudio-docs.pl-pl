---
title: Omówienie | Narzędzie Test Microsoft IntelliTest Developer
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9b8a83ec50ce724b0d62e83a4f8848f7d82f11ff
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="overview-of-microsoft-intellitest"></a>Omówienie programu Microsoft IntelliTest

IntelliTest umożliwia znalezienie usterki wczesne i zmniejsza koszty utrzymania testu. Za pomocą automatycznych i przejrzysty podejścia, IntelliTest można wygenerować candidate zestawu testów dla kodu platformy .NET. Generowanie zestawu testów można dodatkowo kierować się *poprawności właściwości* określisz. IntelliTest nawet rozpoczyna się zestaw testów automatycznie w miarę rozwoju środowisko testowanego kodu.

**Testy opisu** IntelliTest umożliwia określenie zachowania kodu pod względem zestawu testów jednostkowych tradycyjnych.
Zestaw testów może służyć jako mechanizm regresji, na podstawie dla rozwiązania problemu złożoności skojarzone z refaktoryzacji kodu starszych lub nieznane.

**Generowanie danych wejściowych z przewodnikiem testu** IntelliTest używa analizy kodu Otwórz i ograniczenie rozwiązywania podejście do automatycznego generowania wartości wejściowe testu dokładne; zazwyczaj bez potrzeby interwencji użytkownika. W przypadku złożonych obiektów automatycznie generuje fabryki. Przewodnik z wejściowych generowania testów, rozszerzanie i konfigurując fabryki ze swoimi potrzebami. Poprawność właściwości określone jako potwierdzenia w kodzie będą również automatycznie dalsze przewodnik wejściowych generowania testów.

**Integracja IDE** IntelliTest jest w pełni zintegrowany środowiska IDE programu Visual Studio. Wszystkie informacje zebrane podczas generowania zestawu testów (takie jak automatycznie generowanych danych wejściowych, dane wyjściowe z kodu wygenerowanego przypadków testowych i ich przebiegu lub niepowodzenie stanu) jest wyświetlana w środowisku IDE programu Visual Studio. Można łatwo powtarzać ustalania kodu i ponowne uruchomienie IntelliTest, bez opuszczania programu Visual Studio IDE.
Testy można zapisać do rozwiązania jako jednostkowy projekt testowy i będzie można automatycznie wykryć później przez narzędzia Eksplorator testów programu Visual Studio.

**Mogła uzupełniać istniejące rozwiązania w zakresie testowania** IntelliTest Użyj, aby mogła uzupełniać istniejące testowania rozwiązań, że może już wykonaj.

Jeśli chcesz przetestować:

* Algorytmy za pośrednictwem danych pierwotnych lub tablic danych pierwotnych:
  * zapis [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing)
* Algorytmy nad danymi złożonych, takie jak kompilatora:
  * Let IntelliTest najpierw Generowanie abstrakcyjny reprezentację danych i umieść go w algorytmie
  * Let IntelliTest tworzenia wystąpień przy użyciu [utworzenie niestandardowego obiektu](input-generation.md#objects) i invariants danych, a następnie wywołaj algorytm
* Kontenery danych:
  * zapis [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing)
  * Let IntelliTest tworzenia wystąpień przy użyciu [utworzenie niestandardowego obiektu](input-generation.md#objects) i invariants danych, a następnie wywołaj metodę kontenera i później ponownie sprawdzić invariants
  * zapis [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing) różne metody wdrażania, w zależności od wartości parametrów, które wywołują
* Istniejący kod podstawowej:
  * Rozpoczynanie pracy przez Generowanie zestawu za pomocą programu Visual Studio IntelliTest kreatora [sparametryzowanych testów jednostkowych (naraża)](test-generation.md#parameterized-unit-testing)

## <a name="the-hello-world-of-intellitest"></a>Witaj świecie IntelliTest

IntelliTest znajdzie wejść odpowiednich przetestowany program, który oznacza służy do generowania Słynne **Hello World!** Ciąg. przy założeniu, że utworzono projekt testowy na podstawie MSTest C# i dodać odwołanie do **Microsoft.Pex.Framework**. Jeśli używasz framework innym testem tworzenia biblioteki klas C# i zapoznaj się z dokumentacją framework testu na temat sposobu konfigurowania projektu.

Poniższy przykład tworzy dwa ograniczenia dla parametru o nazwie **wartość** tak, aby program IntelliTest zostanie wygenerowany wymagane parametry:

```csharp
using System;
using Microsoft.Pex.Framework;
using Microsoft.VisualStudio.TestTools.UnitTesting;

[TestClass]
public partial class HelloWorldTest {
    [PexMethod]
    public void HelloWorld([PexAssumeNotNull]string value) {
        if (value.StartsWith("Hello")
            && value.EndsWith("World!")
            && value.Contains(" "))
            throw new Exception("found it!");
    }
}
```

Po skompilowany i wykonywane, IntelliTest generuje zestawu testów, takie jak następujące:

1. ""
2. "\0\0\0\0\0"
3. Tekst "hello"
4. "\0\0\0\0\0\0"
5. "Hello\0"
6. "Hello\0\0"
7. "Hello\0World!"
8. "Witaj świecie!"

Odczyt [generowania testów jednostkowych z Intellitest](../../test/generate-unit-tests-for-your-code-with-intellitest.md) zrozumieć, w którym są zapisywane wygenerowane testy. Kod wygenerowany test powinien zawierać testu, takie jak następujący kod:

```csharp
[TestMethod]
[PexGeneratedBy(typeof(global::HelloWorldTest))]
[PexRaisedException(typeof(Exception))]
public void HelloWorldThrowsException167()
{
    this.HelloWorld("Hello World!");
}
```

To bardzo proste!

## <a name="limitations"></a>Ograniczenia

W tej sekcji opisano ograniczenia IntelliTest:

* [Nondeterminism](#nondeterminism)
* [Współbieżność](#concurrency)
* [Natywnego kodu platformy .NET](#native-code)
* [Platformy](#platform)
* [Język](#language)
* [Symbolicznych](#symbolic-reasoning)
* [Śladów stosu](#incorrect-stack)

### <a name="nondeterminism"></a>Nondeterminism

IntelliTest zakłada, że program przeanalizowane deterministyczna. Jeśli nie, IntelliTest zostanie cyklu aż osiągnie eksploracji powiązany.

IntelliTest uwzględnia program się z systemem innym niż determistic jeśli zależy od wejść, które nie może kontrolować IntelliTest.

IntelliTest formanty danych wejściowych dostarczonych do [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing) i uzyskane z [PexChoose](static-helper-classes.md#pexchoose).
W tym sensie wyniki wywołań do kodu niezarządzanego lub niezinstrumentowanej również są traktowane jako "dane wejściowe" dla instrumentowanych programu, ale IntelliTest nie można sterować nimi. Jeśli przepływ sterowania programu zależy od konkretnych wartości pochodzące z tych źródeł zewnętrznych, IntelliTest nie "kierowania" program kierunku wcześniej niepokrytego obszarów.

Ponadto program jest uważana z systemem innym niż determistic wartości ze źródeł zewnętrznych zmiany po ponownym uruchomieniu programu. W takich przypadkach program IntelliTest utraci kontrolę nad wykonywanie programu oraz wyszukiwanie jest nieefektywne.

Czasami nie jest jasne, w takim przypadku.
Rozważ następujące przykłady:

* Wynik **metoda GetHashCode()** metody są dostarczane przez kod niezarządzany, a nie jest przewidywalne.
* **System.Random** klasa korzysta bieżący czas systemowy, aby zapewnić naprawdę losowych wartości.
* **System.DateTime** klasa udostępnia bieżący czas, który nie jest pod kontrolą programu IntelliTest.

### <a name="concurrency"></a>Współbieżność

IntelliTest nie obsługuje programów wielowątkowych.

### <a name="native-code"></a>Kod natywny

IntelliTest nie rozpoznaje kodu natywnego, takich jak x86 instrukcje nazywane za pośrednictwem **P/Invoke**. Nie ma sposobu tłumaczenia takie połączenia do ograniczenia, które mogą zostać przekazane do [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver).
Nawet dla kodu platformy .NET go tylko analizę kodu, który wykonuje Instrumentację go. IntelliTest nie Instrumentacja niektórych części **mscorlib**, łącznie z biblioteki odbicia. **Elementu DynamicMethod** nie można go zinstrumentować.

Sugerowane rozwiązanie jest tryb testowy lokalizację tych metod w typach w zestawie dynamicznym. Jednak nawet w przypadku niektórych metod niezinstrumentowanej, IntelliTest spróbuje obejmują tyle instrumentowanych kodu, jak to możliwe.

### <a name="platform"></a>Platforma

IntelliTest jest obsługiwane tylko na X86, 32-bitowych. NETframework.

### <a name="language"></a>Język

W zasadzie IntelliTest można analizować dowolnego programy .NET, w dowolnym języku .NET. Jednak w programie Visual Studio obsługuje tylko C#.

### <a name="symbolic-reasoning"></a>Symbolicznych

Automatyczne używa IntelliTest [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver) można określić wartości, które są odpowiednie dla testu i program w ramach testu. Jednak możliwości moduł rozwiązywania ograniczeń są i zawsze będzie, ograniczone.

### <a name="incorrect-stack-traces"></a>Śladów stosu niepoprawne

Ponieważ program IntelliTest przechwytuje i "ponownie zgłasza wyjątek" wyjątki w każdej metodzie instrumentowanych numerów wierszy w śladów stosu nie będą poprawne. Jest to ograniczenie zgodnie z założeniami instrukcji "rethrow".

## <a name="further-reading"></a>Dalsze informacje

* [Wstępne wpis w blogu](https://blogs.msdn.microsoft.com/visualstudioalm/2014/11/19/introducing-smart-unit-tests/) w witrynie MSDN.
* [Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
