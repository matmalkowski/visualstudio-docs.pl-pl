---
title: 'CA1031: Nie przechwytuj wyjątków typów ogólnych'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9cbc03edf93c6b4977fe62d72a4df0d60dff035d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Nie przechwytuj wyjątków typów ogólnych
|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Wyjątek ogólny, takich jak <xref:System.Exception?displayProperty=fullName> lub <xref:System.SystemException?displayProperty=fullName> zostanie przechwycony w `catch` instrukcji lub klauzuli catch ogólne, takie jak `catch()` jest używany.

## <a name="rule-description"></a>Opis reguły
 Ogólne wyjątki nie powinny być przechwytywane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, przechwycić bardziej konkretny wyjątek, albo ponownie Zgłoś wyjątek ogólny jako ostatnią instrukcją w `catch` bloku.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Przechwytywanie typów wyjątków ogólnych można ukryć problemów w czasie wykonywania przed użytkownikiem biblioteki i może utrudnić debugowania.

> [!NOTE]
>  Począwszy od [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], środowisko uruchomieniowe języka wspólnego (CLR) dostarcza już uszkodzony wyjątków, które występują w systemie operacyjnym i kod zarządzany, np. naruszenia zasad dostępu w [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)], mają być obsługiwane przez kod zarządzany. Jeśli chcesz skompilować aplikację w [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] lub nowszy i obsługa obsługi wyjątków uszkodzony, możesz zastosować <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atrybut do metody, która obsługuje wyjątek stanie uszkodzenia.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono typu, który narusza tę regułę i typu, który implementuje poprawnie `catch` bloku.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA2200: Zgłoś ponownie wyjątek, aby zachować szczegóły stosu](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)