---
title: 'CA2220: Finalizatory powinny wywoływać finalizatory klasy bazowej'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7f4fc620e55c2f8d5e32e2f2faa94a31d5fe271e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Finalizatory powinny wywoływać finalizatory klasy bazowej
|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ, który zastępuje <xref:System.Object.Finalize%2A?displayProperty=fullName> nie wywołuje <xref:System.Object.Finalize%2A> metody w klasie podstawowej.

## <a name="rule-description"></a>Opis reguły
 Finalizacja musi być powielana w hierarchii dziedziczenia. Aby to zapewnić, typów należy wywołać klasy podstawowej <xref:System.Object.Finalize%2A> metodę z własnych <xref:System.Object.Finalize%2A> metody. Kompilator języka C#, które automatycznie dodaje wywołanie finalizator klasy podstawowej.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, wywołanie typu podstawowego <xref:System.Object.Finalize%2A> metody z Twojej <xref:System.Object.Finalize%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Niektóre kompilatory, których miejscem docelowym jest środowisko uruchomieniowe języka wspólnego Wstawianie wywołania do finalizator typu podstawowego na język pośredni firmy Microsoft (MSIL). Jeśli ostrzeżenie od tej reguły jest zgłaszany, kompilujący nie wstawia wywołania i należy go dodać do kodu.

## <a name="example"></a>Przykład
 Typ przedstawiono w poniższym przykładzie w języku Visual Basic `TypeB` poprawnie wywołującym <xref:System.Object.Finalize%2A> metody w klasie podstawowej.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>Zobacz też
 [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)