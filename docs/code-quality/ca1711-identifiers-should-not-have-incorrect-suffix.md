---
title: "CA1711: Identyfikatory nie powinny mieć nieprawidłowych sufiksów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
helpviewer_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6cde73eeec2b6a73f25f714c41976d3d0513e939
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711: Identyfikatory powinny mieć poprawny przyrostek
|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|  
|CheckId|CA1711|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Identyfikator ma nieprawidłowy sufiks.  
  
## <a name="rule-description"></a>Opis reguły  
 Według Konwencji szczególnych zarezerwowane sufiksy powinna kończyć tylko nazwy typów, które rozszerzać niektórych typów podstawowych lub zawierają implementację niektórych interfejsów lub typy pochodzące z tych typów. Inne nazwy typów nie powinny używać tych zarezerwowanych sufiksów.  
  
 W poniższej tabeli wymieniono zastrzeżonych sufiksów i typy podstawowe i interfejsy, które są skojarzone.  
  
|Sufiks|Interfejs podstawowy|  
|------------|--------------------------|  
|Atrybut|<xref:System.Attribute?displayProperty=fullName>|  
|Kolekcja|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|  
|Słownik|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|  
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|  
|EventHandler|Obiekt delegowany obsługi zdarzeń|  
|Wyjątek|<xref:System.Exception?displayProperty=fullName>|  
|Uprawnienie|<xref:System.Security.IPermission?displayProperty=fullName>|  
|Kolejki|<xref:System.Collections.Queue?displayProperty=fullName>|  
|Stos|<xref:System.Collections.Stack?displayProperty=fullName>|  
|Strumień|<xref:System.IO.Stream?displayProperty=fullName>|  
  
 Ponadto następujące sufiksy powinny **nie** można użyć:  
  
-   Delegate  
  
-   Wyliczenie  
  
-   Impl — zamiast tego użyj "Core"  
  
-   Ex lub podobne sufiks odróżniający go od wcześniejszej wersji tego samego typu  
  
 Konwencje nazewnictwa Podaj wygląd wspólnej dla bibliotek przeznaczonych środowisko uruchomieniowe języka wspólnego. Zmniejsza to nauki jest wymagany dla nowej biblioteki oprogramowania, którą można tworzyć bardziej niezawodne klienta, czy biblioteka został opracowany przez osobę, która ma doświadczenia w rozwijającym się kodu zarządzanego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Usuń sufiks z nazwą typu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżenia od tej reguły, chyba że sufiks ma znaczenie jednoznaczne w domenie aplikacji.  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1710: Identyfikatory powinny mieć poprawny sufiks](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty](/dotnet/standard/design-guidelines/attributes)   
 [Obsługa i wywoływanie zdarzeń](/dotnet/standard/events/index)  