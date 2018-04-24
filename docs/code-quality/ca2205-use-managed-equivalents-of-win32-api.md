---
title: 'CA2205: Użyj zarządzanych odpowiedników interfejsu API Win32'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8e38a985db524b3d95c4f33a4eb4f31c909fd08c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Użyj zarządzanych odpowiedników interfejsu API Win32
|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Wywołanie platformy metoda jest zdefiniowana i metody z równoważne funkcje istnieje w [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] biblioteki klas.

## <a name="rule-description"></a>Opis reguły
 Platforma wywołania metody są używane do wywoływania funkcji niezarządzanej DLL i jest definiowana za pomocą <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atrybutu, lub `Declare` słów kluczowych w języku Visual Basic. Niepoprawnie określonych platform wywołania metody może prowadzić do obsługi wyjątków z powodu problemów, takich jak funkcja misnamed błędny mapowania typów danych wartości parametru i wrócić i specyfikacje niepoprawne pola, takie jak Konwencja wywołania i znak zestaw. Jeśli jest dostępna, zazwyczaj jest prostsza i mniej podatna wywołać równoważne metody zarządzanych niż do definiowania i bezpośrednio wywołać metodę niezarządzane. Wywołanie platformy wywołania metody również może prowadzić do problemów dodatkowe zabezpieczenia, które należy rozważyć.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zastąp wywołanie funkcji niezarządzanej przy użyciu wywołania na jej odpowiednik zarządzanych.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie od tej reguły, jeśli metoda sugerowane zastępczy nie zawiera funkcje.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano, a platforma wywołania definicję metody, która narusza zasady. Ponadto wywołania platformy wywołania metody i są wyświetlane równoważne zarządzaną metodę.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]

## <a name="related-rules"></a>Powiązanych reguł
 [Ca1404: należy Wywołać GetLastError natychmiast po P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: Przenieś P/Invokes do klasy NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: Powinny istnieć punkty wejścia P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P/Invoke nie powinny być widoczne](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Należy określić marshaling dla argumentów ciągu P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)