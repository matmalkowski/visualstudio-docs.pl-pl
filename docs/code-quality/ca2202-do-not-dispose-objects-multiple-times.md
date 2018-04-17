---
title: 'CA2202: Nie Likwiduj wielokrotnie obiektów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: e8d7132f9f4ac935b49ad61a7b3e4df307395e73
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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
 <xref:System.IDisposable?displayProperty=fullName>   
 [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)