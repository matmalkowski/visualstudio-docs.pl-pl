---
title: 'CA1810: Zainicjuj wbudowane pola statyczne typu referencyjnego | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 113d5206d2b4827902cf83827efd5b8738387755
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Zainicjuj wbudowane pola statyczne typu referencyjnego
|||  
|-|-|  
|TypeName|InitializeReferenceTypeStaticFieldsInline|  
|CheckId|CA1810|  
|Kategoria|Microsoft.Performance|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Typ referencyjny deklaruje jawny Konstruktor statyczny.  
  
## <a name="rule-description"></a>Opis reguły  
 Podczas gdy typ deklaruje jawny, statyczny konstruktor, kompilator just in time (JIT) do każdej metody statycznej dodaje sprawdzenie i konstruktora wystąpienia, aby upewnić się, że konstruktor statyczny został wcześniej wywołany. Inicjowanie statyczne jest wywoływane podczas uzyskiwania dostępu do dowolnego statyczny element członkowski lub gdy tworzone jest wystąpienie tego typu. Jednak inicjowania statycznych nie zostanie wywołany, jeśli zadeklarować zmiennej typu, ale nie jest używana, które mogą być istotne, jeśli inicjowanie zmieni stan globalny.  
  
 Gdy wszystkie dane statyczne są wbudowane zainicjowane i jawny Konstruktor statyczny nie jest zadeklarowana, Dodaj Kompilatory języka pośredniego (MSIL) firmy Microsoft `beforefieldinit` flagę i niejawnego konstruktora statycznych, który inicjuje dane statyczne, typ MSIL Definicja. Gdy wystąpi przy użyciu kompilatora JIT `beforefieldinit` Flaga w większości przypadków kontroli Konstruktor statyczny nie zostaną dodane. Inicjowanie statyczne jest gwarantowane wystąpić na pewien czas, przed uzyskaniem dostępu do dowolnego pola statyczne, ale nie przed Konstruktor statyczny metody lub wystąpienia jest wywoływany. Należy zauważyć, że ten statycznego inicjowania może występować w dowolnym momencie po deklaracji zmiennej typu.  
  
 Sprawdzenia konstruktora statycznego mogą obniżyć wydajność. Często Konstruktor statyczny służy tylko do pól statycznych, w których przypadku należy tylko się upewnić, że statycznego inicjowania występuje przed pierwszym dostępie pola statycznego inicjowania. `beforefieldinit` Zachowanie jest odpowiednia dla tych i innych typów. Nie należy tylko podczas inicjowania statycznych ma wpływ na stan globalny oraz jest spełniony jeden z następujących czynności:  
  
-   Wpływ na stan globalny jest kosztowne i nie jest wymagane, jeśli typ nie jest używany.  
  
-   Globalny stan efekty są dostępne bez uzyskiwania dostępu do dowolnego pola statyczne typu.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, zainicjuj wszystkie dane statyczne, gdy jest on zadeklarowany, i usuń konstruktor statyczny.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Można bezpiecznie pominąć ostrzeżenie od tej reguły, jeśli wydajność nie ma znaczenia; lub jeśli stan globalny zmiany, które są spowodowane statycznego inicjowania jest dość kosztowna lub musi zapewniona przed metodą statyczną typu jest wywoływana lub tworzone jest wystąpienie typu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono typu, `StaticConstructor`, który narusza regułę i typ, `NoStaticConstructor`, który zastępuje Konstruktor statyczny inicjowanie wbudowanego spełniają reguły.  
  
 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]  
  
 Należy pamiętać, dodanie `beforefieldinit` Flaga w definicji MSIL `NoStaticConstructor` klasy.  
  
 **.class publicznego automatycznie ansi StaticConstructor**  
 **Rozszerza [mscorlib]System.Object**  
**{**  
**} / / koniec klasy StaticConstructor**  
**.class publicznego automatycznie ansi beforefieldinit NoStaticConstructor**  
 **Rozszerza [mscorlib]System.Object**  
**{**  
**} / / koniec klasy NoStaticConstructor**   
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2207: Zainicjuj wbudowane pola statyczne typu wartości](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)