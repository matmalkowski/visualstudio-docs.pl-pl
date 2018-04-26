---
title: 'CA1024: Używaj właściwości wszędzie, gdzie jest to odpowiednie'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 58f27aebba0bd8a126928e01f13c65bec3381742
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Używaj właściwości wszędzie, gdzie jest to odpowiednie
|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metody publiczne lub chronione ma nazwę, która rozpoczyna się od `Get`nie przyjmuje żadnych parametrów i zwraca wartość, która nie jest tablicą.

## <a name="rule-description"></a>Opis reguły
 W większości przypadków właściwości zawierają dane i metod wykonania akcji. Właściwości są dostępne, takich jak pola, które ułatwia ich używać. Metody są odpowiednimi kandydatami zostać właściwości, jeśli występuje jeden z następujących warunków:

-   Nie przyjmuje żadnych argumentów i zwraca informacje o stanie obiektu.

-   Akceptuje jeden argument można ustawić część stanu obiektu.

 Właściwości powinny działać tak, jakby są pola; Jeśli metoda nie, nie należy zmienić właściwości. Metody są lepsze niż właściwości w następujących sytuacjach:

-   Metoda przeprowadza czasochłonna operacja. Metoda jest perceivably wolniej niż czas, który jest wymagany, aby ustawić lub pobrać wartości pola.

-   Metoda przeprowadza konwersji. Uzyskiwanie dostępu do pola nie zwraca skonwertowaną wersję danych, które są przechowywane.

-   Metoda Get ma ubocznym zauważalne. Pobieranie wartości pola nie tworzy żadnych efektów ubocznych.

-   Ważna jest kolejność wykonywania. Ustawianie wartości pola nie bazuje na występowanie innych operacji.

-   Wywołanie metody dwa razy pod rząd daje różne wyniki.

-   Metoda jest statyczna, ale zwraca obiekt, który może zostać zmieniona przez obiekt wywołujący. Pobieranie wartości pola nie zezwala na obiekt wywołujący, aby zmiany danych, który jest przechowywany przez pole.

-   Metoda zwraca tablicę.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, zmień metodę do właściwości.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie od tej reguły, jeśli metoda spełnia co najmniej jedną z wcześniej podanych kryteriów.

## <a name="controlling-property-expansion-in-the-debugger"></a>Kontrolowanie właściwości rozszerzenia w debugerze
 Jednego powodu programistów unikać właściwości jest, ponieważ nie ma debugera automatycznie rozwijać go. Na przykład właściwość mogą dotyczyć przydzielanie dużego obiektu lub wywoływania P/Invoke, ale może nie faktycznie mieć żadnych zauważalne efekty uboczne.

 Debuger uniemożliwia automatyczne rozwijanie właściwości, stosując <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. W poniższym przykładzie przedstawiono ten atrybut jest stosowany do właściwości wystąpienia.

```vb
Imports System
Imports System.Diagnostics

Namespace Microsoft.Samples

    Public Class TestClass

        ' [...]

        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _
        Public ReadOnly Property LargeObject() As LargeObject
            Get
                ' Allocate large object
                ' [...]
            End Get
        End Property

    End Class

End Namespace
```

```csharp

      using System;
using System.Diagnostics;

namespace Microsoft.Samples
{
    publicclass TestClass
    {
        // [...]

        [DebuggerBrowsable(DebuggerBrowsableState.Never)]
        public LargeObject LargeObject
        {
            get
            {
                // Allocate large object
                // [...]

        }
    }
}
```

## <a name="example"></a>Przykład
 Poniższy przykład zawiera kilka metod powinny być konwertowane do właściwości, oraz kilka który powinna nie, ponieważ nie zachowują się podobnie jak pola.

 [!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]