---
title: 'CA1406: Unikaj argumentów Int64 dla klientów programu Visual Basic 6'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f6eeda13b8dc7a05622613f719a6b2a85b61835a
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546879"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Unikaj argumentów Int64 dla klientów programu Visual Basic 6

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ, który jest specjalnie oznaczony jako widoczny na Component Object Model (COM) deklaruje element członkowski tego przyjmuje <xref:System.Int64?displayProperty=fullName> argumentu.

## <a name="rule-description"></a>Opis reguły
 Klienci Visual Basic 6 COM nie może uzyskać dostęp do 64-bitowych liczb całkowitych.

 Domyślnie widoczny dla modelu COM są następujące: zestawy, typy publiczne, składowe publiczne wystąpienia w publicznych typach i wszystkich elementów członkowskich typów publicznych wartości. Aby zmniejszyć liczbę fałszywych alarmów, ta reguła wymaga jednak widoczność COM typu, który ma być jawnie określony; muszą być oznaczone zawierające zestaw <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> równa `false` i typ musi być oznaczony przez <xref:System.Runtime.InteropServices.ComVisibleAttribute> równa `true`.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady dla parametru, którego wartość, zawsze może być wyrażona jako całkowite 32-bitowych, Zmień typ parametru na <xref:System.Int32?displayProperty=fullName>. Jeśli wartość parametru może być większy niż może być wyrażona jako całkowite 32-bitowych, Zmień typ parametru na <xref:System.Decimal?displayProperty=fullName>. Należy pamiętać, że oba <xref:System.Single?displayProperty=fullName> i <xref:System.Double?displayProperty=fullName> tracić dokładność w prawym górnym zakresy <xref:System.Int64> typu danych. Jeśli element członkowski nie jest przeznaczona do być widoczne dla modelu COM, oznacz ją za pomocą <xref:System.Runtime.InteropServices.ComVisibleAttribute> równa `false`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli ma pewności, czy klienci Visual Basic 6 COM nie będą miały dostęp typu.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Unikaj składowych statycznych w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Zobacz także

- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)
- [Long, typ danych](/dotnet/visual-basic/language-reference/data-types/long-data-type)