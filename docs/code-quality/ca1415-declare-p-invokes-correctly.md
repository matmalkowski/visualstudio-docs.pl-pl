---
title: 'CA1415: Deklarowanie wywołuje P poprawnie'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb03f6a5e0242af79242f2b3ae735fa4df694c20
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: Należy poprawnie zadeklarować P/Invokes
|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Nie można zobaczyć podziału non - Jeśli P/Invoke, który deklaruje parametr poza zestaw. Przerywanie — Jeśli P/Invoke, który deklaruje parametru może być widoczny spoza zestawu.|

## <a name="cause"></a>Przyczyna
 Platforma wywołania metody jest niepoprawnie zadeklarowany.

## <a name="rule-description"></a>Opis reguły
 Platforma wywołania metody uzyskuje dostęp do niezarządzanego kodu i jest definiowana za pomocą `Declare` — słowo kluczowe w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] lub <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Obecnie ta reguła szuka deklaracje metody, przeznaczonych funkcje Win32, które mają wskaźnik do parametru struktury OVERLAPPED wywołanie platformy i odpowiadającego mu parametru zarządzanego nie jest wskaźnikiem do <xref:System.Threading.NativeOverlapped?displayProperty=fullName> struktury.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, poprawnie zadeklarować platformy wywołania metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono platformy wywoływania metod, które naruszają zasady i spełniać reguły.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>Zobacz też
 [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)