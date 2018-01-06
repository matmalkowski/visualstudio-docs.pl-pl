---
title: "Testowanie w generacji | Narzędzie Test Microsoft IntelliTest dewelopera | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Test generation
ms.assetid: B6CADFD1-42C7-4FC0-B41F-0E9F8291A702
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: d44b3972e3060626c6f8f0780d8c05948704d258
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="test-generation"></a>Generowanie testu

W tradycyjnych testy jednostkowe wymaga kilku składników opracować testu:

```
[Test]
void MyTest() {
    // data
    ArrayList a = new ArrayList();

    // method sequence
    a.Add(5);

    // assertions
    Assert.IsTrue(a.Count==1);
    Assert.AreEqual(a[0], 5);
}
```

Uruchomienie testu zawiera różne aspekty:

* Naprawia on [sekwencję wywołań — metoda](test-generation.md#test-generators)
* Naprawia on argumenty, które metody są wywoływane; argumenty [test dane wejściowe](input-generation.md)
* Sprawdza poprawność to oczekiwane zachowanie aplikacji przetestowane przez zestaw z informacją o [potwierdzeń](#assumptions-and-assertions)

IntelliTest często automatycznie można określić wartości argumentów istotne dla ogólnej [sparametryzowanych testów jednostkowych](#parameterized-unit-testing), które zapewniają sekwencję wywołań metody i potwierdzenia.

<a name="test-generators"></a>
## <a name="test-generators"></a>Generatory testu

IntelliTest generuje przypadków testowych, wybierając sekwencję metod wdrażania w ramach testu do wykonania i generować dane wejściowe dla metody podczas sprawdzania potwierdzeń za pośrednictwem pochodnej danych.

A [sparametryzowanego testu jednostkowego](#parameterized-unit-testing) bezpośrednio stanów sekwencję metoda wywołuje w jego treści.

Gdy program IntelliTest musi utworzyć obiekty, wywołania konstruktory i metody fabryki zostaną dodane automatycznie do sekwencji zgodnie z wymaganiami.

<a name="parameterized-unit-testing"></a>
## <a name="parameterized-unit-testing"></a>Sparametryzowane testy jednostkowe

*Sparametryzowanych testów jednostkowych* (naraża) są testów, które przyjmują parametrów. W przeciwieństwie do testów jednostkowych tradycyjnych, które są zazwyczaj zamknięte metod, naraża zająć dowolny zbiór parametrów. Jest to proste? Tak — stamtąd IntelliTest spróbuje [Generowanie zestawu (minimalny) danych wejściowych](input-generation.md) który [pełni obejmują](input-generation.md#dynamic-code-coverage) kodu dostępny z testu.

Naraża są definiowane przy użyciu [PexMethod](attribute-glossary.md#pexmethod) atrybutu niestandardowego w sposób podobny do MSTest (lub NUnit, xUnit). Naraża są logicznie pogrupowane w klasach z metody wystąpienia [PexClass](attribute-glossary.md#pexclass). W poniższym przykładzie przedstawiono prosty PUT przechowywane w **MyPexTest** klasy:

```
[PexMethod]
void ReplaceFirstChar(string target, char c) {

    string result = StringHelper.ReplaceFirstChar(target, c);

    Assert.AreEqual(result[0], c);
}
```

gdzie **ReplaceFirstChar** to metoda, która zastępuje pierwszego znaku ciągu:

```
class StringHelper {
    static string ReplaceFirstChar(string target, char c) {
        if (target == null) throw new ArgumentNullException();
        if (target.Length == 0) throw new ArgumentOutOfRangeException();
        return c + target.Substring(1);
    }
}
```

Z tego testu IntelliTest może automatycznie [wygenerowanie danych wejściowych](input-generation.md) dla PUT, obejmujący wiele ścieżek wykonywania kodu przetestowane. Każdy danych wejściowych, który obejmuje wykonanie inną ścieżkę pobiera "serializacji" jako testu jednostkowego:

```
[TestMethod, ExpectedException(typeof(ArgumentNullException))]
void ReplaceFirstChar0() {
    this.ReplaceFirstChar(null, 0);
}
...
[TestMethod]
void ReplaceFirstChar10() {
    this.ReplaceFirstChar("a", 'c');
}
```

<a name="generic-parameterized"></a>
## <a name="generic-parameterized-unit-testing"></a>Ogólny sparametryzowane testy jednostkowe

Sparametryzowanych testów jednostkowych może być metody ogólne. W takim przypadku użytkownik musi określić typy służy do tworzenia wystąpienia metody przy użyciu [PexGenericArguments](attribute-glossary.md#pexgenericarguments).

```
[PexClass]
public partial class ListTest {
    [PexMethod]
    [PexGenericArguments(typeof(int))]
    [PexGenericArguments(typeof(object))]
    public void AddItem<T>(List<T> list, T value)
    { ... }
}
```

<a name="allowing-exceptions"></a>
## <a name="allowing-exceptions"></a>Zezwalanie na wyjątki

IntelliTest zawiera wiele atrybutów sprawdzania poprawności ułatwia wyjątki klasyfikacji do oczekiwane wyjątki i nieoczekiwanego wyjątku.

Oczekiwano wyjątki wygenerowania ujemna przypadków testowych z odpowiednią adnotacją, taką jak  **ExpectedException (typeof (*xxx*)) ** podczas generowania wyjątków nieoczekiwany w przypadku braku przypadków testowych.

```
[PexMethod, PexAllowedException(typeof(ArgumentNullException))]
void SomeTest() {...}
```

Moduły weryfikacji są:

* [PexAllowedException](attribute-glossary.md#pexallowedexception): umożliwia typu określonego wyjątku z dowolnego miejsca
* [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly): umożliwia typu określonego wyjątku z określonego zestawu
* [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype): umożliwia typu określonego wyjątku z określonego typu
* [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest): umożliwia typu wyjątku określonego typu w ramach testu

<a name="internal-types"></a>
## <a name="testing-internal-types"></a>Testowanie typów wewnętrznych

IntelliTest można "test" wewnętrzne typy, tak długo, jak widzą je. IntelliTest wyświetlić typy następującego atrybutu został dodany do projektu produktu lub testu za pomocą kreatorów Visual Studio IntelliTest:

```
[assembly: InternalsVisibleTo("Microsoft.Pex, PublicKey=002400000480000094000000060200000024000052534131000400000100010007d1fa57c4aed9f0a32e84aa0faefd0de9e8fd6aec8f87fb03766c834c99921eb23be79ad9d5dcc1dd9ad236132102900b723cf980957fc4e177108fc607774f29e8320e92ea05ece4e821c0a5efe8f1645c4c0c93c1ab99285d622caa652c1dfad63d745d6f2de5f17e5eaf0fc4963d261c8a12436518206dc093344d5ad293
```

<a name="assumptions-and-assertions"></a>
## <a name="assumptions-and-assertions"></a>Założenia i potwierdzeń

Użytkownicy mogą używać założenia i potwierdzeń Express [warunki wstępne](#precondition) (założenia) i [postconditions](#postcondition) (potwierdzenia) dotyczących ich testów. Gdy program IntelliTest generuje zestaw wartości parametrów, a "Eksploruje" kod, mogą naruszają zasady przyjmuje testu. W takim przypadku nie będzie już generował testu dla tej ścieżki, ale dyskretne ignorowanie go.

Potwierdzenia są dobrze znanych pojęciem platform testów jednostkowych regularnie, więc IntelliTest już "rozumie" wbudowane **Assert** klas dostarczonych przez platformę poszczególnych obsługiwanych badania. Jednak większość struktur nie udostępniają **Przyjmij** klasy. W takim przypadku zapewnia IntelliTest [PexAssume](static-helper-classes.md#pexassume) klasy. Jeśli nie chcesz używać istniejącej struktury testowej, IntelliTest ma również [PexAssert](static-helper-classes.md#pexassert) klasy.

```
[PexMethod]
public void Test1(object o) {
    // precondition: o should not be null
    PexAssume.IsNotNull(o);

    ...
}
```

W szczególności założeń nullness nie mogą być kodowane jako atrybut niestandardowy:

```
[PexMethod]
public void Test2([PexAssumeNotNull] object o)
// precondition: o should not be null
{
   ...
}
```

<a name="precondition"></a>
## <a name="precondition"></a>Warunek wstępny

Warunek wstępny metody wyraża warunki, zgodnie z którymi powiedzie metody.

Zazwyczaj warunki wstępne są realizowane przez sprawdzanie parametry i stan obiektu i zgłaszanie **ArgumentException** lub **InvalidOperationException** jeśli jego naruszenia.

W IntelliTest, warunek wstępny z [sparametryzowanego testu jednostkowego](#parameterized-unit-testing) określony przez [PexAssume](static-helper-classes.md#pexassume).

<a name="postcondition"></a>
## <a name="postcondition"></a>Warunku końcowego

Warunku końcowego metody wyraża warunki, które powinno zawierać podczas i po wykonaniu metody, przy założeniu, że jego warunki wstępne są początkowo prawidłowe.

Zwykle, warunku końcowego jest wymuszana przez wywołania **Assert** metody.

Z IntelliTest, warunku końcowego z [sparametryzowanego testu jednostkowego](#parameterized-unit-testing) określony przez [PexAssert](static-helper-classes.md#pexassert).

<a name="test-failures"></a>
## <a name="test-failures"></a>Niepowodzenia testu
Gdy powiedzie wygenerowanego przypadek testowy

1. Jeśli nie zakończy się w obrębie [skonfigurowane ścieżce zakresem](exploration-bounds.md), jest traktowane jako błąd, chyba że [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded) ustawiono opcję

1. Jeśli test zgłasza **PexAssumeFailedException**, próba powiedzie się. Jednak jest zwykle filtrowane się, chyba że [TestEmissionFilter](exploration-bounds.md#testemissionfilter) ustawiono **wszystkie**

1. Jeśli test narusza [potwierdzenia](#assumptions-and-assertions), np. przez Zgłaszanie wyjątku naruszenie potwierdzenia jednostki testowania framework, działanie nie powiodło się

Jeśli żaden z powyższych utworzyć decyzji, test zakończy się powodzeniem, tylko wtedy, gdy nie zgłasza wyjątek. Potwierdzenie naruszeń są traktowane w taki sam sposób jak wyjątków.

<a name="setup-teardown"></a>
## <a name="setup-and-tear-down"></a>Konfigurowanie i zniszcz

W ramach integracji z platform testów obsługuje IntelliTest wykrywania i uruchamiania instalacji i zerwanie metody.

**Przykład**

```
using Microsoft.Pex.Framework;
using NUnit.Framework;

namespace MyTests
{
    [PexClass]
    [TestFixture]
    public partial class MyTestClass
    {
        [SetUp]
        public void Init()
        {
            // monitored
        }

        [PexMethod]
        public void MyTest(int i)
        {
        }

        [TearDown]
        public void Dispose()
        {
            // monitored
        }
    }
}

```

<a name="further-reading"></a>
## <a name="further-reading"></a>Dalsze informacje

* [Testy w celu powiązania kodu](https://blogs.msdn.microsoft.com/visualstudioalm/2015/04/18/smart-unit-tests-test-to-code-binding-test-case-management/)
* [Jeden test do wszystkich reguł](https://blogs.msdn.microsoft.com/visualstudioalm/2015/07/05/intellitest-one-test-to-rule-them-all/)

## <a name="got-feedback"></a>Masz opinię?

Publikowania własnych pomysłów i funkcji żądań na  **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
