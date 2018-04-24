---
title: 'CA1407: Unikaj statycznych elementów członkowskich w typach widocznych dla modelu COM'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f14e3b2577d182db432402a267e8bd6979736186
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Unikaj statycznych elementów członkowskich w typach widocznych dla modelu COM
|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ, w szczególności oznaczony jako widoczna do składnika modelu COM (Object) zawiera `public``static` metody.

## <a name="rule-description"></a>Opis reguły
 Model COM nie obsługuje `static` metody.

 Ta zasada powoduje ignorowanie właściwości i metod dostępu zdarzeń, przeładowanie metody lub metody, które są oznaczone za pomocą operatora <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atrybutu lub <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atrybutu.

 Domyślnie widoczne dla modelu COM są następujące: zestawy, typy publiczne elementów członkowskich wystąpienia publicznego w publicznych typach i wszystkie elementy członkowskie typów publicznych wartości.

 Dla tej reguły występuje na poziomie zestawu <xref:System.Runtime.InteropServices.ComVisibleAttribute> musi mieć ustawioną `false` i klasa - <xref:System.Runtime.InteropServices.ComVisibleAttribute> musi mieć ustawioną `true`, jak pokazano w następującym kodem.

```csharp
using System;
using System.Runtime.InteropServices;

[assembly: ComVisible(false)]
namespace Samples
{
    [ComVisible(true)]
    public class MyClass
    {
        public static void DoSomething()
        {
        }
    }
}
```

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby usunąć naruszenie tej reguły, zmienić projektu przy użyciu metody wystąpienia, która zapewnia te same funkcje co `static` metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie od tej reguły, jeśli klient modelu COM nie wymagają dostępu do funkcjonalności zapewnianej przez `static` metody.

## <a name="example-violation"></a>Przykład naruszenie

### <a name="description"></a>Opis
 W poniższym przykładzie przedstawiono `static` metodę, która narusza tę regułę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]

### <a name="comments"></a>Komentarze
 W tym przykładzie **Book.FromPages** nie można wywołać metody z modelu COM.

## <a name="example-fix"></a>Przykład poprawki

### <a name="description"></a>Opis
 Aby naprawić naruszenie w poprzednim przykładzie, można zmienić metodę do metody wystąpienia, ale które nie mają sensu w tym wystąpieniu. Lepszym rozwiązaniem jest zastosowanie jawnie `ComVisible(false)` do metody, aby była Wyczyść, aby inni deweloperzy, że metoda mogą być niewidoczne z modelu COM.

 Następujący przykład dotyczy <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> do metody.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]

## <a name="related-rules"></a>Powiązanych reguł
 [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: Unikaj argumentów typu Int64 w przypadku klientów programu Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Zobacz też
 [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)