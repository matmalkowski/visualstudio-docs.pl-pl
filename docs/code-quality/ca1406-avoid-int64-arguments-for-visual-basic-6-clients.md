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
ms.workload:
- multiple
ms.openlocfilehash: e4455373338cda463623c75ff099a1c706f589dc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31897636"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Unikaj argumentów Int64 dla klientów programu Visual Basic 6
|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 W szczególności oznaczony jako widoczna do składnika modelu COM (Object) typu deklaruje element członkowski tego przyjmuje <xref:System.Int64?displayProperty=fullName> argumentu.

## <a name="rule-description"></a>Opis reguły
 Visual Basic 6 COM klienci nie mają dostępu 64-bitowych liczb całkowitych.

 Domyślnie widoczne dla modelu COM są następujące: zestawy, typy publiczne elementów członkowskich wystąpienia publicznego w publicznych typach i wszystkie elementy członkowskie typów publicznych wartości. Aby ograniczyć liczbę fałszywych alarmów, ta zasada wymaga jednak widoczność modelu COM typu, który ma być jawnie podanym; muszą być oznaczone zestawu zawierającego <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> ustawioną `false` i typ musi być oznaczone <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawioną `true`.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby usunąć naruszenie tej reguły dla parametru o wartości zawsze może być wyrażona jako całkowite 32-bitowych, należy zmienić typ parametru do <xref:System.Int32?displayProperty=fullName>. Jeśli wartość parametru może być większy niż może zostać wyrażona jako całkowite 32-bitowych, należy zmienić typ parametru na <xref:System.Decimal?displayProperty=fullName>. Należy pamiętać, że oba <xref:System.Single?displayProperty=fullName> i <xref:System.Double?displayProperty=fullName> tracić dokładność w górnym zakresy <xref:System.Int64> — typ danych. Jeśli element członkowski ma nie być widoczne dla modelu COM, oznacz go z <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawioną `false`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli ma pewności, że klienci Visual Basic 6 COM nie uzyska dostępu do typu.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typu, który narusza zasady.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Unikaj składowych statycznych w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Zobacz też
 [Współdziałanie z niezarządzanych kodu](/dotnet/framework/interop/index) [Long — typ danych](/dotnet/visual-basic/language-reference/data-types/long-data-type)