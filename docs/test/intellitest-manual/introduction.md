---
title: "Omówienie | Narzędzie Test Microsoft IntelliTest dewelopera | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 65f14d96bd495a1b3f8ca138176fbf805fdfeb67
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="overview-of-microsoft-intellitest"></a>Omówienie programu Microsoft IntelliTest

IntelliTest umożliwia znalezienie usterki wczesne i zmniejsza koszty utrzymania testu. Za pomocą automatycznych i przejrzysty podejścia, IntelliTest można wygenerować candidate zestawu testów dla kodu platformy .NET. Generowanie zestawu testów można dodatkowo kierować się *poprawności właściwości* określisz. IntelliTest nawet rozpoczyna się zestaw testów automatycznie w miarę rozwoju środowisko testowanego kodu.

**Testy opisu**  
IntelliTest umożliwia określenie zachowania kodu pod względem zestawu testów jednostkowych tradycyjnych. Zestaw testów może służyć jako mechanizm regresji, na podstawie dla rozwiązania problemu złożoności skojarzone z refaktoryzacji kodu starszych lub nieznane.

**Generowanie wejściowych z przewodnikiem testu**  
IntelliTest używa analizy kodu Otwórz i ograniczenie rozwiązywania podejście do automatycznego generowania dokładne testowania wartości wejściowe; zazwyczaj bez potrzeby interwencji użytkownika. W przypadku złożonych obiektów automatycznie generuje fabryki. Przewodnik z wejściowych generowania testów, rozszerzanie i konfigurując fabryki ze swoimi potrzebami. Poprawność właściwości określone jako potwierdzenia w kodzie będą również automatycznie dalsze przewodnik wejściowych generowania testów.

**Integracja środowiska IDE**  
IntelliTest jest w pełni zintegrowana w programie Visual Studio IDE. Wszystkie informacje zebrane podczas generowania zestawu testów (takie jak automatycznie generowanych danych wejściowych, dane wyjściowe z kodu wygenerowanego przypadków testowych i ich przebiegu lub niepowodzenie stanu) jest wyświetlana w środowisku IDE programu Visual Studio. Można łatwo powtarzać ustalania kodu i ponownie uruchomić program IntelliTest, bez opuszczania programu Visual Studio IDE. Testy można zapisać do rozwiązania jako jednostkowy projekt testowy i będzie można automatycznie wykryć później przez narzędzia Eksplorator testów programu Visual Studio.

**Uzupełniać istniejące rozwiązania w zakresie testowania**  
Użyj IntelliTest, aby mogła uzupełniać istniejące rozwiązania, które mogą już wykonać testowanie.

Jeśli chcesz przetestować:

* Algorytmy za pośrednictwem danych pierwotnych lub tablic danych pierwotnych:
  * zapis [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing)
* Algorytmy nad danymi złożonych, takie jak kompilatora:
  * Let IntelliTest najpierw Generowanie abstrakcyjny reprezentację danych i umieść go w algorytmie
  * Let IntelliTest tworzenia wystąpień przy użyciu [utworzenie niestandardowego obiektu](input-generation.md#objects) i invariants danych, a następnie wywołaj algorytm
* Kontenery danych:
  * zapis [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing)
  * Let IntelliTest tworzenia wystąpień przy użyciu [utworzenie niestandardowego obiektu](input-generation.md#objects) i invariants danych, a następnie wywołaj metodę invariants kontenera i sprawdź ponownie później
  * zapis [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing) różne metody wdrażania, w zależności od wartości parametrów, które wywołują
* Istniejący kod podstawowej:
  * Rozpoczynanie pracy przez Generowanie zestawu za pomocą programu Visual Studio IntelliTest kreatora [sparametryzowanych testów jednostkowych (naraża)](test-generation.md#parameterized-unit-testing)

<a name="hello-world"></a>
## <a name="the-hello-world-of-intellitest"></a>Witaj świecie IntelliTest

IntelliTest znajdzie wejść odpowiednich przetestowany program, który oznacza służy do generowania Słynne **Hello World!** Ciąg. przy założeniu, że utworzono projekt testowy na podstawie MSTest C# i dodać odwołanie do **Microsoft.Pex.Framework**. Jeśli używasz framework innym testem tworzenia biblioteki klas C# i zapoznaj się z dokumentacją framework testu na temat sposobu konfigurowania projektu.

Poniższy przykład tworzy dwa ograniczenia dla parametru o nazwie **wartość** tak, aby program IntelliTest zostanie wygenerowany wymagany ciąg.

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

Odczyt [generowania testów jednostkowych z Intellitest](../../test/generate-unit-tests-for-your-code-with-intellitest.md) zrozumieć, w którym są zapisywane wygenerowane testy. Kod wygenerowany test powinien zawierać testu, takie jak następujące:

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

<a name="nondeterminism"></a>
### <a name="nondeterminism"></a>Nondeterminism

IntelliTest zakłada, że program przeanalizowane deterministyczna. Jeśli nie, IntelliTest zostanie cyklu aż osiągnie eksploracji powiązany.

IntelliTest uwzględnia program się z systemem innym niż determistic jeśli zależy od wejść, które nie może kontrolować IntelliTest.

IntelliTest formanty danych wejściowych dostarczonych do [sparametryzowanych testów jednostkowych](test-generation.md#parameterized-unit-testing) i uzyskane z [PexChoose](static-helper-classes.md#pexchoose). W tym sensie wyniki wywołań do kodu niezarządzanego lub niezinstrumentowanej również są traktowane jako "dane wejściowe" dla instrumentowanych programu, ale IntelliTest nie można sterować nimi. Jeśli przepływ sterowania programu zależy od konkretnych wartości pochodzące z tych źródeł zewnętrznych, IntelliTest nie "kierowania" program kierunku wcześniej niepokrytego obszarów. 

Ponadto program jest uważana z systemem innym niż determistic wartości ze źródeł zewnętrznych zmiany po ponownym uruchomieniu programu. W takich przypadkach program IntelliTest utraci kontrolę nad wykonywanie programu i wyszukiwanie staje się bardzo mało wydajne.

Czasami nie jest jasne, w takim przypadku. Rozważ następujące przykłady:

* Wynik **metoda GetHashCode()** metody są dostarczane przez kod niezarządzany, a nie jest przewidywalne.
* **System.Random** klasa korzysta bieżący czas systemowy, aby zapewnić naprawdę losowych wartości.
* **System.DateTime** klasa udostępnia bieżący czas nie oczywiście jest pod kontrolą programu IntelliTest.

<a name="concurrency"></a>
### <a name="concurrency"></a>Współbieżność

IntelliTest nie obsługuje programów wielowątkowych.

<a name="native-code"></a>
### <a name="native-code-net-code-that-is-not-instrumented"></a>Kodu natywnego kodu platformy .NET, która nie została zinstrumentowana

IntelliTest nie rozpoznaje kodu natywnego, takich jak x86 instrukcje nazywane za pośrednictwem **P/Invoke**. Nie ma sposobu tłumaczenia takie połączenia do ograniczenia, które mogą zostać przekazane do [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver). Nawet dla kodu platformy .NET go analizować tylko kod, który wykonuje Instrumentację go. IntelliTest nie Instrumentacja niektórych części **mscorlib**, łącznie z biblioteki odbicia. **Elementu DynamicMethod** nie można go zinstrumentować. 

Sugerowane rozwiązanie jest tryb testowy lokalizację tych metod w typach w zestawie dynamicznym. Jednak nawet w przypadku niektórych metod niezinstrumentowanej, IntelliTest spróbuje obejmują tyle instrumentowanych kodu, jak to możliwe.

<a name="platform"></a>
### <a name="platform"></a>Platforma

IntelliTest jest obsługiwane tylko na X86, 32-bitowych. NETframework.

<a name="language"></a>
### <a name="language"></a>Język

W zasadzie IntelliTest można analizować dowolnego programy .NET, w dowolnym języku .NET. Jednak w programie Visual Studio obsługuje tylko C#.

<a name="symbolic-reasoning"></a>
### <a name="symbolic-reasoning"></a>Symbolicznych

Automatyczne używa IntelliTest [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver) można określić wartości, które są odpowiednie dla testu i program w ramach testu. Jednak możliwości moduł rozwiązywania ograniczeń są i zawsze będzie, ograniczone.

<a name="incorrect-stack"></a>
### <a name="slightly-incorrect-stack-traces"></a>Śladów stosu (nieco) jest niepoprawny

Ponieważ program IntelliTest przechwytuje i "ponownie zgłasza wyjątek" wyjątki w każdej metodzie instrumentowanych numerów wierszy w śladów stosu nie będą poprawne. Jest to ograniczenie zgodnie z założeniami instrukcji "rethrow".

<a name="further-reading"></a>
## <a name="further-reading"></a>Dalsze informacje

* [Wstępne wpis w blogu](https://blogs.msdn.microsoft.com/visualstudioalm/2014/11/19/introducing-smart-unit-tests/) w witrynie MSDN.
* [Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest](../../test/generate-unit-tests-for-your-code-with-intellitest.md)

## <a name="got-feedback"></a>Masz opinię?

Publikowania własnych pomysłów i funkcji żądań na  **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
