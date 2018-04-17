---
title: 'CA2002: Nie należy blokować obiektów z słabą tożsamością | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 01/31/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d509de487bd81b4401195a8e3564c165a2d50f0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002: Nie należy blokować obiektów z słabą tożsamością

|||
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|CheckId|CA2002|
|Kategoria|Microsoft.Reliability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Wątek próbuje uzyskać blokady obiektu, który ma słabej tożsamości.

## <a name="rule-description"></a>Opis reguły

Obiekt ma słabą tożsamość, gdy można uzyskać do niego bezpośredni dostęp poza granicami domeny aplikacji. Wątek, który próbuje uzyskać blokadę na obiekcie o słabej tożsamości, może zostać zablokowany przez drugi wątek w domenie innej aplikacji, która ma blokady dla tego samego obiektu.

Następujące typy mają słaby tożsamości i są oznaczone przez regułę:

- <xref:System.String>

- Tablice typów wartości, w tym [typów całkowitych](/dotnet/csharp/language-reference/keywords/integral-types-table), [typów zmiennoprzecinkowych](/dotnet/csharp/language-reference/keywords/floating-point-types-table), i <xref:System.Boolean>.

- <xref:System.MarshalByRefObject>

- <xref:System.ExecutionEngineException>

- <xref:System.OutOfMemoryException>

- <xref:System.StackOverflowException>

- <xref:System.Reflection.MemberInfo>

- <xref:System.Reflection.ParameterInfo>

- <xref:System.Threading.Thread>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby rozwiązać naruszenie tej reguły, użyj obiektu z typem, który nie jest na liście w sekcji Opis.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="related-rules"></a>Powiązanych reguł

[CA2213: Pola możliwe do likwidacji powinny zostać zlikwidowane](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono niektóre blokady obiektu, które naruszają zasady.

[!code-vb[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/VisualBasic/ca2002-do-not-lock-on-objects-with-weak-identity_1.vb)]
[!code-csharp[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/CSharp/ca2002-do-not-lock-on-objects-with-weak-identity_1.cs)]

## <a name="see-also"></a>Zobacz także

<xref:System.Threading.Monitor>  
<xref:System.AppDomain>  
[Lock — instrukcja (C#)](/dotnet/csharp/language-reference/keywords/lock-statement)  
[SyncLock — instrukcja (Visual Basic)](/dotnet/visual-basic/language-reference/statements/synclock-statement)