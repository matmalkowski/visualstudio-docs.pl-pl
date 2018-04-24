---
title: 'CA1001: Typy, które posiadają pola usuwalne, powinny być usuwalne'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3def21cf32dd45c006045a5301293da2a5d0f70
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Typy, które posiadają pola usuwalne, powinny być usuwalne
|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału — Jeśli typ nie jest widoczna poza zestaw.<br /><br /> Przerywanie — Jeśli typ jest widoczna poza zestaw.|

## <a name="cause"></a>Przyczyna
 Klasa deklaruje i implementuje pole wystąpienia, który jest <xref:System.IDisposable?displayProperty=fullName> typu i klasa nie implementuje <xref:System.IDisposable>.

## <a name="rule-description"></a>Opis reguły
 Implementuje klasę <xref:System.IDisposable> interfejsu zlikwidować niezarządzane zasoby, które jest właścicielem. Pole wystąpienia, który jest <xref:System.IDisposable> typ wskazuje, że pole jest właścicielem niezarządzanego zasobu. Klasa, która deklaruje <xref:System.IDisposable> pola pośrednio jest właścicielem niezarządzanego zasobu i powinien implementować <xref:System.IDisposable> interfejsu. Jeśli klasa nie ma bezpośredniego wszelkie niezarządzane zasoby, powinny implementuje finalizator.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać naruszenie tej reguły, zaimplementuj <xref:System.IDisposable> i z <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> wywołanie metody <xref:System.IDisposable.Dispose%2A> metody pola.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono klasę, która narusza zasady i klasy, która spełnia reguły zaimplementowanie <xref:System.IDisposable>. Klasa nie implementuje finalizator, ponieważ klasa nie ma bezpośredniego żadnych niezarządzanych zasobów.

 [!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
 [!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA2213: Pola możliwe do likwidacji powinny zostać zlikwidowane](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216: Typy możliwe do likwidacji powinny deklarować finalizator](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215: Metody Dispose powinny wywoływać metodę Dispose klasy podstawowej](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049: Typy z zasobami natywnymi powinny być możliwe do likwidacji](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)