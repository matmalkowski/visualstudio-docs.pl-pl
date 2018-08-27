---
title: 'CA2201: Nie wywołuj zastrzeżonych typów wyjątku | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1971ccb2012794467a4fbdf661d55df61c934c90
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902336"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: Nie wywołuj zastrzeżonych typów wyjątków
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2201: Nie wywołuj zastrzeżonych typów wyjątku](https://docs.microsoft.com/visualstudio/code-quality/ca2201-do-not-raise-reserved-exception-types).

|||
|-|-|
|TypeName|DoNotRaiseReservedExceptionTypes|
|CheckId|CA2201|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda zgłasza typem wyjątku jest zbyt ogólne lub który jest zarezerwowana przez środowisko uruchomieniowe.

## <a name="rule-description"></a>Opis reguły
 Następujące typy wyjątków są zbyt ogólne, aby zapewnić wystarczającą ilość informacji do użytkownika:

-   <xref:System.Exception?displayProperty=fullName>

-   <xref:System.ApplicationException?displayProperty=fullName>

-   <xref:System.SystemException?displayProperty=fullName>

 Następujące typy wyjątków są zarezerwowane i powinien być zgłaszany tylko przez środowisko uruchomieniowe języka wspólnego:

-   <xref:System.ExecutionEngineException?displayProperty=fullName>

-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>

-   <xref:System.NullReferenceException?displayProperty=fullName>

-   <xref:System.OutOfMemoryException?displayProperty=fullName>

 **Nie zgłaszają Wyjątki ogólne**

 Jeśli typ ogólny wyjątek, takich jak zgłaszać <xref:System.Exception> lub <xref:System.SystemException> w bibliotekę lub strukturę, wymusza odbiorców w celu przechwytywania wszystkich wyjątków, łącznie z nieznanego wyjątki, które nie wiedzą, jak obsługiwać.

 Zamiast tego należy zgłaszać bardziej pochodnego typu, który już istnieje w ramach albo utworzyć swój własny typ, który pochodzi od klasy <xref:System.Exception>.

 **Throw określonych wyjątków**

 W poniższej tabeli przedstawiono parametry i wyjątków, które zgłaszają podczas sprawdzania poprawności parametru, w tym wartość parametru metody dostępu set właściwości:

|Opis parametru|Wyjątek|
|---------------------------|---------------|
|`null` Odwołanie|<xref:System.ArgumentNullException?displayProperty=fullName>|
|Poza dozwolonym zakresem wartości (np. indeks zbioru lub listy)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|Nieprawidłowy `enum` wartość|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|Zawiera formatu, który nie spełnia specyfikacji parametru metody (takie jak ciąg formatu w celu `ToString(String)`)|<xref:System.FormatException?displayProperty=fullName>|
|W przeciwnym razie jest nieprawidłowy|<xref:System.ArgumentException?displayProperty=fullName>|

 Jeśli operacja jest nieprawidłowa dla bieżącego stanu obiektu throw <xref:System.InvalidOperationException?displayProperty=fullName>

 Podczas wykonywania operacji na obiekcie, który został usunięty throw <xref:System.ObjectDisposedException?displayProperty=fullName>

 Jeśli operacja nie jest obsługiwana (takie jak zastąpione **Stream.Write** w Stream, otwarty do odczytu) throw <xref:System.NotSupportedException?displayProperty=fullName>

 Podczas konwersji mogłoby spowodować przepełnienie (np. przeciążenia operatora rzutowania jawnego) throw <xref:System.OverflowException?displayProperty=fullName>

 W innych sytuacjach należy rozważyć utworzenie swój własny typ, który pochodzi od klasy <xref:System.Exception> i który throw.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić typ wyrzuconego wyjątku dla określonego typu, który nie jest jednym z zastrzeżonych typów.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="related-rules"></a>Powiązane reguły
 [CA1031: Nie przechwytuj ogólnych typów wyjątków](../code-quality/ca1031-do-not-catch-general-exception-types.md)



