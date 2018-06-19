---
title: 'CA2202: Nie należy usuwać obiektów wiele razy'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c7eb35e556e8edd6e840f2fbd6701e182895706
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920152"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Nie należy usuwać obiektów wiele razy
|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Implementacja metody zawiera ścieżki kodu, które mogły spowodować wielu wywołań <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> lub równoważnej metodę Dispose, na przykład metody Close() dla niektórych typów, na tym samym obiekcie.

## <a name="rule-description"></a>Opis reguły
 Poprawnie zaimplementowana A <xref:System.IDisposable.Dispose%2A> metoda może być wywołana wiele razy bez generowania wyjątku. Jednak to nie jest gwarantowana i aby uniknąć generowania <xref:System.ObjectDisposedException?displayProperty=fullName> nie należy wywoływać <xref:System.IDisposable.Dispose%2A> więcej niż jeden raz w obiekcie.

## <a name="related-rules"></a>Powiązanych reguł
 [CA2000: Likwiduj obiekty przed utratą zakresu](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać problem naruszenie tej reguły, zmień implementację tak, to niezależnie od ścieżki kodu <xref:System.IDisposable.Dispose%2A> jest wywoływana tylko jeden raz dla obiekt.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Nawet jeśli <xref:System.IDisposable.Dispose%2A> dla obiekt jest znany jako, można bezpiecznie wywołać wiele razy, implementacja mogą ulec zmianie w przyszłości.

## <a name="example"></a>Przykład
 Zagnieżdżone `using` instrukcje (`Using` w języku Visual Basic) może spowodować naruszenia CA2202 ostrzeżenia. Jeśli zasób IDisposable zagnieżdżonych wewnętrzny `using` instrukcja zawiera zasobu zewnętrznego `using` instrukcji `Dispose` metody zagnieżdżonych zasobów zwalnia zawartego zasobu. Jeśli ta sytuacja występuje, `Dispose` metody zewnętrznego `using` instrukcji podejmie próbę usunięcia jego zasobów raz drugi.

 W poniższym przykładzie <xref:System.IO.Stream> obiekt, który jest tworzony w zewnętrznej za pomocą instrukcji zwolnieniu na końcu wewnętrzny przy użyciu instrukcji w metodzie Dispose <xref:System.IO.StreamWriter> obiekt, który zawiera `stream` obiektu. Na koniec zewnętrznego `using` instrukcji `stream` obiektu zwolnieniu po raz drugi. Drugie wydanie stanowi to naruszenie CA2202.

```
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}

```

## <a name="example"></a>Przykład
 Aby rozwiązać ten problem, należy użyć `try` / `finally` bloku zamiast zewnętrznego `using` instrukcji. W `finally` bloków, upewnij się, że `stream` zasobu nie jest zerowa.

```
Stream stream = null;
try
{
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);
    using (StreamWriter writer = new StreamWriter(stream))
    {
        stream = null;
        // Use the writer object...
    }
}
finally
{
    if(stream != null)
        stream.Dispose();
}

```

## <a name="see-also"></a>Zobacz też
 <xref:System.IDisposable?displayProperty=fullName> [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)