---
title: 'CA1027: Oznaczaj wyliczenia za pomocą FlagsAttribute | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 702bc45001f1d545fab6e6a3d54d58b552408402
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Oznaczaj wyliczenia za pomocą FlagsAttribute
|||  
|-|-|  
|TypeName|MarkEnumsWithFlags|  
|CheckId|CA1027|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Wartości Wyliczenie publiczne są potęgami liczby dwa lub kombinacji innych wartości, które są zdefiniowane w wyliczeniu, i <xref:System.FlagsAttribute?displayProperty=fullName> atrybut nie jest obecny. Aby ograniczyć liczbę fałszywych alarmów, ta zasada nie raportuje naruszenie dla wyliczenia, których wartości ciągłe.  
  
## <a name="rule-description"></a>Opis reguły  
 Wyliczenie to typ wartości, który definiuje zestaw powiązanych, nazwanych stałych. Zastosuj <xref:System.FlagsAttribute> na wyliczenie w jego stałe nazwane można uzyskać wiarygodny połączeniu. Rozważmy na przykład wyliczenie dni tygodnia w aplikacji, która przechowuje informacje o dostępnych zasobów, który dzień. Jeśli dostępność każdego zasobu jest zakodowany przy użyciu wyliczenia, które ma <xref:System.FlagsAttribute> może być reprezentowany obecnie dowolną kombinację dni. Bez atrybutu może być reprezentowany tylko jeden dzień tygodnia.  
  
 W przypadku pól przechowujących łączonymi wyliczenia wartości wyliczenia poszczególnych są traktowane jako grup bitów w polu. W związku z tym takie pola są czasami określane jako *pól bitowych*. Aby połączyć wartości wyliczenia dla magazynu w pola bitowego, należy używać operatorów logicznych warunkowego. Aby przetestować pola bitowego, aby określić, czy występuje wartość wyliczenia określonych, użyj operatorów logicznych Boolean. Pola bitowego do przechowywania i pobierania wartości wyliczenia Scalonej poprawnie każda wartość, która jest zdefiniowana w wyliczeniu musi być potęgą liczby dwa. Jeśli tak jest, logiczna operatorów logicznych nie będzie można wyodrębnić wartości poszczególnych wyliczenia, które są przechowywane w tym polu.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Dodaj <xref:System.FlagsAttribute> do wyliczenia.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Ostrzeżenie od tej zasady należy pominąć, jeśli nie chcesz łączonymi wartości wyliczenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `DaysEnumNeedsFlags` jest wyliczeniem, który spełnia wymagania dotyczące korzystania z <xref:System.FlagsAttribute>, ale nie ma. `ColorEnumShouldNotHaveFlag` Wyliczanie nie ma wartości, które są potęgami liczby dwa, ale niepoprawnie Określa <xref:System.FlagsAttribute>. Ta regułą [CA2217: nie oznaczaj typów wyliczeniowych atrybutem FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).  
  
 [!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2217: Nie oznaczaj wyliczeń za pomocą atrybutu FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.FlagsAttribute?displayProperty=fullName>