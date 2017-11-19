---
title: "CA1700: Nie nazwy wartości wyliczenia &#39; Zarezerwowane &#39; | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2acfafaec213f619dbe8c3077ab5cc72bdfde88d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: Nie nazwy wartości wyliczenia &#39; Zarezerwowane &#39;
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
 [CA2217: Nie oznaczaj typów wyliczeniowych atrybutem FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1712: Nie dodawaj prefiksu wartości enum nazwą typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028: Pamięć wyliczenia powinna być Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1008: Wyliczenia powinny mieć wartości zerowej](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027: Oznaczaj wyliczenia za pomocą FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)