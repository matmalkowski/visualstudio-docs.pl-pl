---
title: 'CA2149: Metody przezroczyste nie mogą wywoływać kodu natywnego | Dokumentacja firmy Microsoft'
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
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 887252eca86205858b168c7f5a4a6c33cb0cc67d
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42900196"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149: Jawne metody nie mogą wywoływać kodu natywnego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2149: metody przezroczyste nie mogą wywoływać kodu natywnego](https://docs.microsoft.com/visualstudio/code-quality/ca2149-transparent-methods-must-not-call-into-native-code).

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|CheckId|CA2149|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda wywołania funkcji macierzystej za pośrednictwem szkieletu metody, takie jak metody P/Invoke.

## <a name="rule-description"></a>Opis reguły
 Ta reguła jest uruchamiana dla każdej przezroczystej metody, która wywołuje bezpośrednio kod natywny, na przykład przez metodę P/Invoke. Naruszenie tej zasady prowadzi do <xref:System.MethodAccessException> w poziomie 2 modelu przezroczystości i pełnego żądania dla <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> w modelu przezroczystości poziomu 1.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy oznaczyć metody, która wywołuje kodu natywnego za pomocą <xref:System.Security.SecurityCriticalAttribute> lub <xref:System.Security.SecuritySafeCriticalAttribute> atrybutu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2149.transparentmethodsmustnotcallnativecode/cs/ca2149 - transparentmethodsmustnotcallnativecode.cs#1)]



