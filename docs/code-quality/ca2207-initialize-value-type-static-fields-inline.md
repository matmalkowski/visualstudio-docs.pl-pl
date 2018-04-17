---
title: 'CA2207: Zainicjuj wbudowane pola statyczne typu wartości | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: f5d063cda94451feef28aba9715033234d9adaa1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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