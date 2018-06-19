---
title: IntelliTest podręcznika | Narzędzia testowania Microsoft Developer
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest Reference Manual, IntelliTest
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: f9534668ef5cf07388d6eefec9ef37a28593daaa
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31977451"
---
# <a name="intellitest-reference-manual"></a>IntelliTest podręcznika

## <a name="contents"></a>Spis treści

* **[Omówienie programu IntelliTest](introduction.md)**
  - [Witaj świecie IntelliTest](introduction.md#the-hello-world-of-intellitest)
  - [Ograniczenia](introduction.md#limitations)
    * [Nondeterminism](introduction.md#nondeterminism)
    * [Współbieżność](introduction.md#concurrency)
    * [Kod natywny](introduction.md#native-code)
    * [Platformy](introduction.md#platform)
    * [Język](introduction.md#language)
    * [Symbolicznych](introduction.md#symbolic-reasoning)
    * [Śladów stosu niepoprawne](introduction.md#incorrect-stack-traces)
  - [Dalsze informacje](introduction.md#further-reading)<p>&nbsp;</p>

* **[Rozpoczynanie pracy z IntelliTest](getting-started.md)**
  - [Ważnych atrybutów](getting-started.md#important-attributes)
  - [Ważne pomocnika statycznych klas](getting-started.md#helper-classes)<p>&nbsp;</p>

* **[Generowanie testu](test-generation.md)**
  - [Generatory testu](test-generation.md#test-generators)
  - [Sparametryzowane testy jednostkowe](test-generation.md#parameterized-unit-testing)
  - [Ogólny sparametryzowane testy jednostkowe](test-generation.md#generic-parameterized)
  - [Zezwalanie na wyjątki](test-generation.md#allowing-exceptions)
  - [Testowanie typów wewnętrznych](test-generation.md#internal-types)
  - [Założenia i potwierdzeń](test-generation.md#assumptions-and-assertions)
  - [Warunek wstępny](test-generation.md#precondition)
  - [Warunku końcowego](test-generation.md#postcondition)
  - [Niepowodzenia testu](test-generation.md#test-failures)
  - [Konfigurowanie i zniszcz](test-generation.md#setup-teardown)
  - [Dalsze informacje](test-generation.md#further-reading)<p>&nbsp;</p>

* **[Generowanie wejściowych](input-generation.md)**
  - [Moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver)
  - [Pokrycie kodu dynamiczne](input-generation.md#dynamic-code-coverage)
  - [Liczby całkowite i elementów przestawnych](input-generation.md#integers-and-floats)
  - [Obiekty](input-generation.md#objects)
  - [Tworzenie wystąpień istniejących klas](input-generation.md#existing-classes)
  - [Widoczność](input-generation.md#visibility)
  - [Mocks sparametryzowane](input-generation.md#parameterized-mocks)
  - [Struktury](input-generation.md#structs)
  - [Tablice i ciągi](input-generation.md#arrays-and-strings)
  - [Uzyskiwanie dodatkowych danych wejściowych](input-generation.md#additional-inputs)
  - [Dalsze informacje](input-generation.md#further-reading)<p>&nbsp;</p>

* **[Granice eksploracji](exploration-bounds.md)**
  - [MaxConstraintSolverTime](exploration-bounds.md#maxconstraintsolvertime)
  - [MaxConstraintSolverMemory](exploration-bounds.md#maxconstraintsolvermemory)
  - [MaxBranches](exploration-bounds.md#maxbranches)
  - [MaxCalls](exploration-bounds.md#maxcalls)
  - [MaxStack](exploration-bounds.md#maxstack)
  - [MaxConditions](exploration-bounds.md#maxconditions)
  - [MaxRuns](exploration-bounds.md#maxruns)
  - [MaxRunsWithoutNewTests](exploration-bounds.md#maxrunswithoutnewtests)
  - [MaxRunsWithUniquePaths](exploration-bounds.md#maxrunswithuniquepaths)
  - [MaxExceptions](exploration-bounds.md#maxexceptions)
  - [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded)
  - [TestEmissionFilter](exploration-bounds.md#testemissionfilter)
  - [TestEmissionBranchHits](exploration-bounds.md#testemissionbranchhits)<p>&nbsp;</p>

* **[Słownik atrybutów](attribute-glossary.md)**
  - [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull)
  - [PexClass](attribute-glossary.md#pexclass)
  - [PexGenericArguments](attribute-glossary.md#pexgenericarguments)
  - [PexMethod](attribute-glossary.md#pexmethod)
  - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)
  - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
  - [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest)
  - [PexInstrumentAssemblyAttribute](attribute-glossary.md#pexinstrumentassemblyattribute)
  - [PexUseType](attribute-glossary.md#pexusetype)
  - [PexAllowedException](attribute-glossary.md#pexallowedexception)
  - [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly)
  - [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype)
  - [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest)<p>&nbsp;</p>

* **[Ustawienia wykresu kaskadowego](settings-waterfall.md)**

* **[Klasy statyczne pomocy](static-helper-classes.md)**
  - [PexAssume](static-helper-classes.md#pexassume)
  - [PexAssert](static-helper-classes.md#pexassert)
  - [PexChoose](static-helper-classes.md#pexchoose)
  - [PexObserve](static-helper-classes.md#pexobserve)
  - [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)<p>&nbsp;</p>

* **[Ostrzeżenia i błędy](warnings-and-errors.md)**
  - [Przekroczono MaxBranches](warnings-and-errors.md#maxbranches-exceeded)
  - [Przekroczono MaxConstraintSolverTime](warnings-and-errors.md#maxconstraintsolvertime-exceeded)
  - [Przekroczono MaxConditions](warnings-and-errors.md#maxconditions-exceeded)
  - [Przekroczono MaxCalls](warnings-and-errors.md#maxcalls-exceeded)
  - [Przekroczono MaxStack](warnings-and-errors.md#maxstack-exceeded)
  - [Przekroczono MaxRuns](warnings-and-errors.md#maxruns-exceeded)
  - [Przekroczono MaxRunsWithoutNewTests](warnings-and-errors.md#maxrunswithoutnewtests-exceeded)
  - [Nie można skonkretyzować rozwiązania](warnings-and-errors.md#cannot-concretize-solution)
  - [Potrzebujesz pomocy do konstruowania obiektu](warnings-and-errors.md#help-construct)
  - [Potrzebujesz pomocy w celu odnalezienia typów](warnings-and-errors.md#help-types)
  - [Można używać typu odgadnąć](warnings-and-errors.md#usable-type-guessed)
  - [Nieoczekiwany błąd podczas eksploracji](warnings-and-errors.md#unexpected-exploration)
  - [TargetInvocationException](warnings-and-errors.md#targetinvocationexception)
  - [Niezinstrumentowanej metody o nazwie](warnings-and-errors.md#uninstrumented-method-called)
  - [Wywołano metodę zewnętrznych](warnings-and-errors.md#external-method-called)
  - [Wywołuje metody niemożliwej](warnings-and-errors.md#uninstrumentable-method-called)
  - [Problem testowania](warnings-and-errors.md#testability-issue)
  - [Ograniczenia](warnings-and-errors.md#limitation)
  - [Zaobserwowano niezgodność wywołań](warnings-and-errors.md#observed-call-mismatch)
  - [Wartość przechowywana w polu statycznym](warnings-and-errors.md#value-static-field)<p>&nbsp;</p>

## <a name="got-feedback"></a>Masz opinię?

Publikowania własnych pomysłów i funkcji żądań na  **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
