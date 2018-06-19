---
title: 'CA1306: Należy ustawić ustawienia regionalne dla typów danych'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b9a7188f3679e04164411472fd2d53948466a30d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900406"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: Należy ustawić ustawienia regionalne dla typów danych
|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Metody lub konstruktora utworzony co najmniej jeden <xref:System.Data.DataTable?displayProperty=fullName> lub <xref:System.Data.DataSet?displayProperty=fullName> wystąpień i nie jawnie ustawiona właściwość locale (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> lub <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>).

## <a name="rule-description"></a>Opis reguły
 Ustawienia regionalne określa elementy prezentacji specyficzne dla kultury dla danych, takich jak formatowania użytego dla wartości liczbowe, symbol waluty i kolejności sortowania. Po utworzeniu <xref:System.Data.DataTable> lub <xref:System.Data.DataSet>, należy jawnie ustawić ustawień regionalnych. Domyślnie ustawienia regionalne dla tych typów jest bieżącej kultury. Dane są przechowywane w bazie danych lub pliku oraz są udostępniane globalnie, ustawienia regionalne zwykle powinien być ustawiony na kulturą niezmienną (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>). Gdy dane są udostępniane między kultur, przy użyciu domyślnych ustawień regionalnych może spowodować zawartość <xref:System.Data.DataTable> lub <xref:System.Data.DataSet> przedstawione lub nieprawidłowo interpretowane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, jawnie ustaw ustawienia regionalne <xref:System.Data.DataTable> lub <xref:System.Data.DataSet>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest to bezpieczne Pomiń ostrzeżenie od tej reguły, gdy biblioteki lub aplikacji jest ograniczony odbiorców lokalnych, danych nie jest udostępniana lub domyślne ustawienie zapewni żądane zachowanie we wszystkich obsługiwanych scenariuszach.

## <a name="example"></a>Przykład
 Poniższy przykład tworzy dwa <xref:System.Data.DataTable> wystąpień.

 [!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]

## <a name="see-also"></a>Zobacz też
 <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName> <xref:System.Globalization.CultureInfo?displayProperty=fullName> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>