---
title: 'CA1415: Deklarowanie wywołuje P poprawnie'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 6a690baeb804d3722d442c30077cc07d260a8952
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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