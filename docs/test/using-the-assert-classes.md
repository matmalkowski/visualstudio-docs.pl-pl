---
title: Używanie klas potwierdzenia w celu testowania w programie Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert statements
- unit tests, Assert statements
- unit tests, Assert classes
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2d56477822fa2d965902d9442d47e2c3ab24d656
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="use-the-assert-classes"></a>Korzystać z klas potwierdzeń

Aby sprawdzić określonych funkcji, należy użyć klas potwierdzeń UnitTestingFramework przestrzeni nazw. Kod metody w kodzie rozwoju wywiera metody testowej jednostki, ale tylko wtedy, gdy obejmują Assert-instrukcje zgłasza poprawność działania kodu.

## <a name="kinds-of-asserts"></a>Typy z potwierdzeń

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> Przestrzeń nazw zawiera kilka rodzajów klas potwierdzeń:

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

 W metodę testu można wywołać metody klasy Assert, takich jak Assert.AreEqual() dowolną liczbę. Klasa Assert ma wiele metod do wyboru, a wiele z tych metod ma kilka przeciążeń.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

 Porównywanie kolekcji obiektów i sprawdź stan co najmniej jednej kolekcji, należy użyć klasy CollectionAssert.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

 Klasa StringAssert służy do porównywania ciągów znaków. Ta klasa zawiera różne przydatne metody, takie jak StringAssert.Contains, StringAssert.Matches i StringAssert.StartsWith.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

 Wyjątek AssertFailedException jest generowany, gdy test zakończy się niepowodzeniem. Test zakończy się niepowodzeniem, jeśli upłynie limit czasu, nieoczekiwany wyjątek lub zawiera instrukcję Assert, który zwraca wynik nie powiodło się.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

 AssertInconclusiveException jest generowany, gdy test powstaje niejednoznacznego. Zwykle Dodaj instrukcję Assert.Inconclusive do testu, które są nadal działa na wskazująca, że nie jest jeszcze gotowy do uruchomienia.

> [!NOTE]
> Strategia alternatywnych jest aby oznaczyć testu, który nie jest gotowy do uruchomienia z atrybutem Ignoruj. Ma to jednak wadą, który nie może łatwo wygenerować raport liczby testów się, że masz jeszcze na wdrożenie.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

 Jeśli piszesz nowej klasy wyjątku Assert, o tej klasy, które dziedziczą z klasy podstawowej UnitTestAssertException ułatwia identyfikację wyjątku, ponieważ błąd potwierdzenia zamiast nieoczekiwany wyjątek w kodzie testowym lub produkcyjnym.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

 Dekoracji metody testowej z atrybutem ExpectedExceptionAttribute, jeśli chcesz, aby metody testowej, aby sprawdzić, czy wyjątek może zostać wygenerowany przez metody w kodzie Programowanie w rzeczywistości został zgłoszony w tej metodzie.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [Kod testu jednostkowego](../test/unit-test-your-code.md)
