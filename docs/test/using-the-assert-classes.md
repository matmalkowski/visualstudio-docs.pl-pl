---
title: MSTest assert klasy i metody
ms.date: 06/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert methods
- unit tests, Assert classes
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 91198e9b7048b384bf2095840abbd012042025ed
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844263"
---
# <a name="use-assert-classes-for-unit-testing"></a>Użyj klas potwierdzeń w celu przeprowadzania testów jednostkowych

Użyj klasy Assert <xref:Microsoft.VisualStudio.TestTools.UnitTesting> przestrzeni nazw, aby sprawdzić określonych funkcji. Metody testowej jednostki wykonuje kod metody w kodzie aplikacji, ale tylko wtedy, gdy obejmują Assert-instrukcje zgłasza poprawność działania kodu.

## <a name="kinds-of-asserts"></a>Typy z potwierdzeń

<xref:Microsoft.VisualStudio.TestTools.UnitTesting> Przestrzeń nazw zawiera kilka rodzajów klas potwierdzeń.

W Twojej metody testowej, można wywołać żadnych metod <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName> klas, takich jak <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType>. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> Klasa ma wiele metod do wyboru, a wiele metod ma kilka przeciążeń.

### <a name="compare-strings-and-collections"></a>Porównywanie ciągów i kolekcji

Użyj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert> klasy porównywanie kolekcji obiektów lub Sprawdź stan kolekcji.

Użyj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert> klasę, aby porównać i sprawdź, czy ciągi. Ta klasa zawiera różne przydatne metody <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType>, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType>, i <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType>.

### <a name="exceptions"></a>Wyjątki

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException> Wyjątek zawsze, gdy test zakończy się niepowodzeniem. Test kończy się niepowodzeniem, jeśli przekroczy limit czasu, wygeneruje nieoczekiwany wyjątek lub zawiera instrukcję assert, która powoduje **niepowodzenie**.

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException> Jest zgłaszany, gdy test daje w wyniku **niejednoznacznego**. Zazwyczaj dodaje się <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType> instrukcji do testu, który użytkownik nadal pracuje, aby wskazać, nie jest jeszcze gotowy do uruchomienia.

> [!NOTE]
> Strategia alternatywnych jest oznaczenie testu, który nie jest gotowy do uruchomienia z <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute> atrybutu. Ma to jednak wadą, który nie może łatwo wygenerować raport liczby testów, które nie są zaimplementowane.

Podczas pisania nowy assert klasy wyjątku, dziedziczą z klasy podstawowej <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException> aby ułatwić identyfikację wyjątku, ponieważ błąd potwierdzenia zamiast nieoczekiwany wyjątek w kodzie testowym lub produkcyjnym.

Dekoracji metody testowej z <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> atrybut, jeśli chcesz, aby metody testowej, można zweryfikować, że faktycznie jest zgłaszany wyjątek może zostać zgłoszony przez metodę w kodzie aplikacji.

## <a name="see-also"></a>Zobacz także

- [Kod testu jednostkowego](../test/unit-test-your-code.md)