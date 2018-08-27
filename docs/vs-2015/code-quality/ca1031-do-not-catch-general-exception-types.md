---
title: 'CA1031: Nie Przechwytuj wyjątków typów ogólnych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fee08bdc2b93687a5415fdbd137c48f816f4acbb
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42901712"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Nie przechwytuj wyjątków typów ogólnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1031: nie Przechwytuj typów wyjątków ogólnych](https://docs.microsoft.com/visualstudio/code-quality/ca1031-do-not-catch-general-exception-types).

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Ogólny wyjątek, takie jak <xref:System.Exception?displayProperty=fullName> lub <xref:System.SystemException?displayProperty=fullName> padł w `catch` instrukcji lub Ogólna klauzula catch takich jak `catch()` jest używany.

## <a name="rule-description"></a>Opis reguły
 Ogólne wyjątki nie powinny być przechwytywane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, przechwycić wyjątek bardziej precyzyjny lub Zgłoś ponownie ogólny wyjątek jako ostatnią instrukcję w `catch` bloku.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Przechwytywanie typów wyjątków ogólnych może ukryć problemów w czasie wykonywania przed użytkownikiem biblioteki oraz może utrudnić debugowanie.

> [!NOTE]
>  Począwszy od [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)], środowisko uruchomieniowe języka wspólnego (CLR) dostarcza już wyjątki uszkodzony, które występują w systemie operacyjnym i kodu zarządzanego, takie jak naruszenia zasad dostępu w [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)], aby zostać obsłużony przez kod zarządzany. Jeśli chcesz skompilować aplikację w [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] lub nowszy i obsługa obsługi wyjątków uszkodzony, możesz zastosować <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atrybutu do metody, która obsługuje wyjątek stanie uszkodzenia.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typ, który narusza tę regułę i typu, który implementuje prawidłowo `catch` bloku.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2200: Zgłoś ponownie wyjątek, aby zachować szczegóły stosu](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)



