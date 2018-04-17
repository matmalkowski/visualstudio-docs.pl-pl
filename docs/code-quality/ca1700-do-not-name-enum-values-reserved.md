---
title: 'CA1700: Nie należy nadawać wartościom enum &#39;zastrzeżone&#39; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c9a779915bc086b11b461acebd9fe4d0117f4b40
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: Nie należy nadawać wartościom enum &#39;zastrzeżone&#39;
|||  
|-|-|  
|TypeName|DoNotNameEnumValuesReserved|  
|CheckId|CA1700|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Nazwa elementu członkowskiego wyliczenia zawiera słowo "reserved".  
  
## <a name="rule-description"></a>Opis reguły  
 Ta reguła zakłada, że element członkowski wyliczenia o nazwie, która zawiera „reserved”, nie jest obecnie używany, ale jest symbolem zastępczym do zmiany nazwy lub usunięcia w przyszłej wersji. Zmiana nazwy lub usuwanie członka jest zmianą przerywającą. Nie należy oczekiwać użytkownikom Ignoruj członka tak, ponieważ jego nazwa zawiera "reserved", ani nie mogą polegać na użytkowników do odczytu lub przestrzegać dokumentacji. Ponadto ponieważ zastrzeżone elementy członkowskie są wyświetlane w przeglądarki obiektów i środowisk deweloperskich zintegrowane inteligentne, może spowodować pomyłek o tym, które elementy członkowskie są rzeczywiście używane.  
  
 Zamiast korzystać z zastrzeżonym członkiem, Dodaj nowy element członkowski do wyliczenia w przyszłych wersjach. W większości przypadków dodanie nowego elementu członkowskiego nie jest na istotne zmiany, tak długo, jak dodanie nie powoduje, że wartości oryginalnej składników, aby zmienić.  
  
 Ograniczona liczba przypadków dodawania elementu członkowskiego jest istotne zmiany nawet wtedy, gdy oryginalne członkowie zachować oryginalnych wartości. Przede wszystkim nowy element członkowski nie może być zwracany z istniejących ścieżek kodu bez przerywania wywołań, które używają `switch` (`Select` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) instrukcji wartości zwracanej obejmujący cały element członkowski listy i który zgłosić wyjątek domyślne działanie case. Dodatkowej dotyczą jest, że kod klienta może nie obsługiwać zmiana w porównaniu z metody odbicia takich jak <xref:System.Enum.IsDefined%2A?displayProperty=fullName>. W związku z tym jeśli nowy element członkowski ma zostać zwrócone z istniejących metod lub występuje niezgodność aplikacji z powodu użycia niską odbicia, tylko nierozdzielający rozwiązanie to:  
  
1.  Dodaj nowe wyliczanie zawierający oryginalne i nowe elementy członkowskie.  
  
2.  Oznacz wyliczenie oryginalnego z <xref:System.ObsoleteAttribute?displayProperty=fullName> atrybutu.  
  
 Postępuj zgodnie z tym samym typy widoczne na zewnątrz lub elementów członkowskich, które udostępniają oryginalnego wyliczenia.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, usuń lub zmień nazwę elementu członkowskiego.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły dla elementu członkowskiego, który jest obecnie używany lub bibliotek, które wcześniej zostały dostarczone.  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2217: Nie oznaczaj wyliczeń za pomocą atrybutu FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1712: Nie poprzedzaj wartości wyliczenia nazwą typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028: Magazyn typu wyliczeniowego powinien być typu Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1008: Wyliczenia powinny zawierać wartość zero](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027: Oznacz typy wyliczeniowe atrybutem Flags](../code-quality/ca1027-mark-enums-with-flagsattribute.md)