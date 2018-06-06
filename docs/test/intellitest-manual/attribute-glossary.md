---
title: Słownik atrybutu | Narzędzie Test Microsoft IntelliTest Developer
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Attribute glossary
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 64e02cae39497a14cc087791a60b4f61c9bcd8fd
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815915"
---
# <a name="attribute-glossary"></a>Słownik atrybutów

## <a name="attributes-by-namespace"></a>Atrybuty według przestrzeni nazw

* **Microsoft.Pex.Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
     - [PexExplorationAttributeBase](#pexexplorationattributebase)<p />

* **Microsoft.Pex.Framework.Settings**
  * [PexAssemblySettings](#pexassemblysettings)<p />

* **Microsoft.Pex.Framework.Instrumentation**
  * [PexAssemblyUnderTest](#pexassemblyundertest)
  * [PexInstrumentAssembly](#pexinstrumentassemblyattribute)<p />

* **Microsoft.Pex.Framework.Using**
  * [PexUseType](#pexusetype)<p />

* **Microsoft.Pex.Framework.Validation**
  * [PexAllowedException](#pexallowedexception)
  * [PexAllowedExceptionFromAssembly](#pexallowedexceptionfromassembly)
  * [PexAllowedExceptionFromType](#pexallowedexceptionfromtype)
  * [PexAllowedExceptionFromTypeUnderTest](#pexallowedexceptionfromtypeundertest)

<a name="pexassumenotnull"></a>
## <a name="pexassumenotnull"></a>PexAssumeNotNull

Ten atrybut potwierdza, że nie może być wartością, której działalność **null**. Może zostać dołączony do:

* **parametr** metody test sparametryzowany

  ```csharp
  // assume foo is not null
  [PexMethod]
  public void SomeTest([PexAssumeNotNull]IFoo foo, ...) {}
  ```

* **pola**

  ```csharp
  public class Foo {
     // this field should not be null
     [PexAssumeNotNull]
     public object Bar;
  }
  ```

* A **typu**

  ```csharp
  // never consider null for Foo types
  [PexAssumeNotNull]
  public class Foo {}
  ```

Ponadto można dołączyć do zestawu testowego, testów osprzętu lub metody testowej; w takim przypadku pierwszy argument musi wskazywać, do którego pole lub typ zastosować założeń. Stosuje atrybut do typu, zastosowanie do wszystkich pól z tym typem formalnych.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

Ten atrybut oznacza klasę, która zawiera *eksploracji*. Jest to równoważne MSTest **TestClassAttribute** (lub NUnit **TestFixtureAttribute**). Ten atrybut jest opcjonalne.

Klasy oznaczonej [PexClass](#pexclass) musi być *domyślne umożliwia konstrukcji*:

* publicznie wyeksportowanego typu
* konstruktor domyślny
* nie jest abstrakcyjna

Jeśli klasa nie spełniają tych wymagań, jest zgłaszany błąd i badań nie powiedzie się.

Również zdecydowanie zaleca się dokonanie tych klas **częściowe** tak, aby IntelliTest mogą generować nowe testy, które należą do klasy, ale w oddzielnym pliku. Takie podejście rozwiązuje wiele problemów z powodu [widoczność](input-generation.md#visibility) i to technika typowe w języku C#.

**Pakiet dodatkowe i kategorie**:

```csharp
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**Określanie typu testowanej**:

```csharp
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

Klasa może zawierać metod opatrzoną [PexMethod](#pexmethod). Rozumie także IntelliTest [ustawiania i zniszcz metody](test-generation.md#setup-teardown).

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

Ten atrybut zapewnia krotka typu dla wystąpienia [ogólnego sparametryzowanego testu jednostkowego](test-generation.md#generic-parameterized).

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

Ten atrybut oznacza metodę jako [sparametryzowanego testu jednostkowego](test-generation.md#parameterized-unit-testing).
Metoda musi znajdować się w klasie oznaczonej przez [PexClass](#pexclass) atrybutu.

Program IntelliTest zostanie wygenerowany testy tradycyjnych, bez parametrów, które wymagają [sparametryzowanego testu jednostkowego](test-generation.md#parameterized-unit-testing) z innymi parametrami.

Sparametryzowanego testu jednostkowego:

* musi być metodą wystąpienia
* musi być [widoczne](input-generation.md#visibility) do klasy testu, w którym umieszczane są generowane testy, zgodnie z [ustawienia wykresu kaskadowego](settings-waterfall.md)
* może potrwać dowolną liczbę parametrów
* mogą być ogólne

**Przykład**

```csharp
[PexClass]
public partial class MyTests {
     [PexMethod]
     public void MyTest(int i)
     { ... }
}
```

<a name="pexexplorationattributebase"></a>
## <a name="pexexplorationattributebase"></a>PexExplorationAttributeBase

[Więcej informacji](https://msdn.microsoft.com/library/microsoft.pex.framework.pexexplorationattributebase.aspx)

<a name="pexassemblysettings"></a>
## <a name="pexassemblysettings"></a>PexAssemblySettings

Ten atrybut można określać na poziomie zestawu, aby zastąpić wartości domyślne ustawienia dla wszystkich eksploracji.

```csharp
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "Naked")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

Ten atrybut określa zestaw, który jest poddawana testom w bieżącym projekcie testowym. 

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

Ten atrybut służy do określania zestawu się.

**Przykład**

```csharp
using Microsoft.Pex.Framework;

// the assembly containing ATypeFromTheAssemblyToInstrument should be instrumented
[assembly: PexInstrumentAssembly(typeof(ATypeFromTheAssemblyToInstrument))]

// the assembly name can be used as well
[assembly: PexInstrumentAssembly("MyAssemblyName")]
```

<a name="pexusetype"></a>
## <a name="pexusetype"></a>PexUseType

Ten atrybut informuje program IntelliTest, że można użyć określonego typu można utworzyć wystąpienia typów podstawowych (abstrakcyjny) lub do interfejsów.

**Przykład**

```csharp
[PexMethod]
[PexUseType(typeof(A))]
[PexUseType(typeof(B))]
public void MyTest(object testParameter)
{
     ... // IntelliTest will consider types A and B to instantiate 'testParameter'
}
```

<a name="pexallowedexception"></a>
## <a name="pexallowedexception"></a>PexAllowedException

Jeśli ten atrybut jest dołączony do [PexMethod](#pexmethod) (lub [PexClass](#pexclass), zmienia domyślna logika IntelliTest, wskazującą, jeśli testy nie powiodło się. Test nie zostanie uwzględniony jako zakończony niepowodzeniem, nawet jeśli zgłasza określony wyjątek.

**Przykład**

Następującego testu określa, że konstruktora **stosu** może zgłaszać **ArgumentOutOfRangeException**:

```csharp
class Stack {
  int[] _elements;
  int _count;
  public Stack(int capacity) {
    if (capacity<0) throw new ArgumentOutOfRangeException();
    _elements = new int[capacity];
    _count = 0;
  }
  ...
}
```

Filtr jest dołączony do osprzętu w następujący sposób (go może być także definiowane na poziomie zestawu lub testowym):

```csharp
[PexMethod]
[PexAllowedException(typeof(ArgumentOutOfRangeException))]
class CtorTest(int capacity) {
  Stack s = new Stack(capacity); // may throw ArgumentOutOfRangeException
}
```

<a name="pexallowedexceptionfromassembly"></a>
## <a name="pexallowedexceptionfromassembly"></a>PexAllowedExceptionFromAssembly

[Więcej informacji](https://msdn.microsoft.com/library/microsoft.pex.framework.validation.pexallowedexceptionfromassemblyattribute.aspx)

<a name="pexallowedexceptionfromtype"></a>
## <a name="pexallowedexceptionfromtype"></a>PexAllowedExceptionFromType

[Więcej informacji](https://msdn.microsoft.com/library/microsoft.pex.framework.validation.pexallowedexceptionfromtypeattribute.aspx)

<a name="pexallowedexceptionfromtypeundertest"></a>
## <a name="pexallowedexceptionfromtypeundertest"></a>PexAllowedExceptionFromTypeUnderTest

[Więcej informacji](https://msdn.microsoft.com/library/microsoft.pex.framework.validation.pexallowedexceptionfromtypeundertestattribute.aspx)

## <a name="got-feedback"></a>Masz opinię?

Publikowania własnych pomysłów i funkcji żądań na  **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
