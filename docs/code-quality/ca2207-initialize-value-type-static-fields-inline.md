---
title: 'CA2207: Inicjowanie pól statycznych typu wartościowego'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 883e5d842346a0821b54b2b4eacad3cbc92028b6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: Inicjowanie pól statycznych typu wartościowego
|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ wartości deklaruje jawny Konstruktor statyczny.

## <a name="rule-description"></a>Opis reguły
 Po zadeklarowaniu jest typem wartości, ulega on inicjowanie domyślnych, gdzie wszystkie pola typu wartości zostaną ustawione na zero, a wszystkie pola typu odwołania są ustawione na `null` (`Nothing` w języku Visual Basic). Jawny Konstruktor statyczny jest gwarantowaną jedynie do uruchomienia przed konstruktora wystąpienia lub statyczny element członkowski tego typu jest nazywana. W związku z tym jeśli typ zostanie utworzona bez wywoływania konstruktora wystąpienia, Konstruktor statyczny nie jest gwarantowana do uruchomienia.

 Jeśli wszystkie dane statyczne są wbudowane zainicjowane i zadeklarowano nie jawny Konstruktor statyczny, Dodaj Kompilatory języka C# i Visual Basic `beforefieldinit` flagi do definicji klasy MSIL. Kompilatory również dodać prywatnej Konstruktor statyczny zawierający kod inicjujący statycznych. Ten statyczny Konstruktor prywatny jest gwarantowana do uruchomienia przed uzyskaniem dostępu do dowolnego pola statyczne typu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać naruszenie tej reguły zainicjować wszystkie dane statyczne, kiedy zadeklarowano i Usuń Konstruktor statyczny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="related-rules"></a>Powiązanych reguł
 [CA1810: Inicjuj pola statyczne typu referencyjnego śródwierszowo](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)