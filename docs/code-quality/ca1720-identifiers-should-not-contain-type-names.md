---
title: 'CA1720: Identyfikatory nie powinny zawierać nazw typów'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a8f86037b54b2b7ad5cce1ea683341ca6656c2b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915632"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Identyfikatory nie powinny zawierać nazw typów
|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa parametru w widoczne na zewnątrz elementu członkowskiego zawiera nazwę typu danych.

 —lub—

 Nazwa elementu członkowskiego widoczne na zewnątrz zawiera nazwę typu dane specyficzne dla języka.

## <a name="rule-description"></a>Opis reguły
 Nazwy parametrów i elementów członkowskich lepiej są używane do komunikacji ich znaczenie niż na Opisz ich typu, co powinno być dostarczone przez narzędzia deweloperskie. Nazwy elementów członkowskich Jeśli stosuje się nazwę typu danych, należy użyć nazwy niezależny od języka zamiast specyficzny dla języka. Na przykład zamiast C# typ nazwy "int", należy użyć danych niezależny od języka nazwy typu Int32.

 Każdy token odrębny nazwy parametru lub elementu członkowskiego porównywany następujące nazwy typów dane specyficzne dla języka, w sposób, bez uwzględniania wielkości liter:

-   wartość logiczna

-   WChar

-   Int8

-   UInt8

-   krótki

-   UShort

-   int

-   UInt

-   Liczba całkowita

-   Uinteger —

-   długa

-   ULong

-   Bez znaku

-   Podpisany

-   Float

-   Float32

-   Float64

 Ponadto nazwy parametru również są porównywane z następujące nazwy typów danych niezależny od języka, w sposób, bez uwzględniania wielkości liter:

-   Obiekt

-   Obj

-   Boolean

-   Char

-   String

-   SByte

-   Byte

-   UByte

-   Int16

-   UInt16

-   Int32

-   UInt32

-   Int64

-   UInt64

-   IntPtr

-   PTR

-   Wskaźnik

-   UInptr

-   UPtr

-   UPointer

-   Single

-   Double

-   Wartość dziesiętna

-   Identyfikator GUID

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 **Jeśli uruchamiany przed parametr:**

 Dla identyfikatora typu danych w nazwie parametru Zamień termin lepiej znaczenia lub terminem bardziej ogólnym, na przykład "value".

 **Jeśli uruchamiany przed elementem członkowskim:**

 Zastąp dane specyficzne dla języka identyfikatora typu nazwy elementu członkowskiego termin lepiej znaczenia, odpowiednik niezależny od języka lub terminem bardziej ogólnym, na przykład "value".

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Do czasu korzystania z typu nazwy parametru i element członkowski może być odpowiednie. Jednak w przypadku nowych wdrożeń, Brak znanego scenariusze wystąpić, gdy ma pomijać ostrzeżenie od tej reguły. Dla bibliotek, które mają poprzedniej wysłane może być konieczne pominąć ostrzeżenie od tej reguły.

## <a name="related-rules"></a>Powiązanych reguł
 [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Identyfikatory nie powinny zawierać podkreśleń](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: Nazwy parametrów nie powinny odpowiadać nazwom składowych](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)