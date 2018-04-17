---
title: 'CA1009: Poprawnie zadeklarować obsługę zdarzenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9d207bff88129cb9cc6769cc47ae6e70cbe74d1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Należy poprawnie zadeklarować obsługę zdarzenia
|||  
|-|-|  
|TypeName|DeclareEventHandlersCorrectly|  
|CheckId|CA1009|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Delegata, który obsługuje zdarzenie publiczne lub chronione nie ma poprawnej sygnatury, zwracany typ lub nazwy parametrów.  
  
## <a name="rule-description"></a>Opis reguły  
 Metody obsługi zdarzeń przyjmują dwa parametry. Pierwsza to typu <xref:System.Object?displayProperty=fullName> i nosi nazwę "sender". Jest to obiekt, który wywołał zdarzenie. Drugi parametr jest typu <xref:System.EventArgs?displayProperty=fullName> i nosi nazwę "e". To dane, które są skojarzone ze zdarzeniem. Na przykład jeśli zdarzenie jest wywoływane zawsze, gdy plik jest otwarty, dane zdarzeń zwykle zawiera nazwę pliku.  
  
 Metody obsługi zdarzeń nie może zwracać wartości. W języku C# język programowania, jest to określane przez typ zwracany `void`. Program obsługi zdarzeń może wywołać wiele metod w wielu obiektów. Jeśli metody zostały może zwracać wartości, wiele wartości zwrotnych, może mieć miejsce dla każdego zdarzenia, a wartość ostatniego metody, która została wywołana będzie dostępna.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, popraw podpisu, zwracany typ lub nazwy parametrów delegata. Aby uzyskać więcej informacji zobacz poniższy przykład.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono delegata, który nadaje się do obsługi zdarzeń. Metody, które mogą być wywoływane przez ten program obsługi zdarzeń są zgodne z podpisie, który określono w wytycznych projektowych. `AlarmEventHandler` jest nazwą typu delegata. `AlarmEventArgs` pochodzi od klasy podstawowej dla danych zdarzenia <xref:System.EventArgs>, i blokad alarm danych zdarzenia.  
  
 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2109: Przejrzyj widoczne procedury obsługi zdarzeń](../code-quality/ca2109-review-visible-event-handlers.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.EventArgs?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>   
 [Obsługa i wywoływanie zdarzeń](/dotnet/standard/events/index)  