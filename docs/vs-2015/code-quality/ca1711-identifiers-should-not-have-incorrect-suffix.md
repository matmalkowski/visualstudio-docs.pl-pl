---
title: 'CA1711: Identyfikatory nie powinny mieć niepoprawnego sufiksu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
helpviewer_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ee349aac7b0f4c93502e392e060e4b4636ccf21a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42684181"
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711: Identyfikatory powinny mieć poprawny przyrostek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1711: identyfikatory nie powinny mieć niepoprawnego sufiksu](https://docs.microsoft.com/visualstudio/code-quality/ca1711-identifiers-should-not-have-incorrect-suffix).  
  
Element TypeName | IdentifiersShouldNotHaveIncorrectSuffix |  
| CheckId | CA1711 |  
| Kategoria | Microsoft.Naming|  
| Zmiana powodująca niezgodność | Przerwanie |  
  
## <a name="cause"></a>Przyczyna  
 Identyfikator ma niepoprawnego sufiksu.  
  
## <a name="rule-description"></a>Opis reguły  
 Według Konwencji nazwy typów, które rozszerzają pewne typy podstawowe lub implementują określone interfejsy lub typy pochodzące z tych typów, powinien kończyć się określonym zarezerwowanym sufiksem. Inne nazwy typów nie powinny używać tych zarezerwowanych sufiksów.  
  
 W poniższej tabeli wymieniono zarezerwowanym sufiksem i typy podstawowe i interfejsy, z którymi są skojarzone.  
  
|Suffix|Interfejs podstawowy|  
|------------|--------------------------|  
|Atrybut|<xref:System.Attribute?displayProperty=fullName>|  
|Kolekcja|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|  
|Słownik|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|  
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|  
|EventHandler|Delegat programu obsługi zdarzeń|  
|Wyjątek|<xref:System.Exception?displayProperty=fullName>|  
|Uprawnienie|<xref:System.Security.IPermission?displayProperty=fullName>|  
|kolejki|<xref:System.Collections.Queue?displayProperty=fullName>|  
|Stos|<xref:System.Collections.Stack?displayProperty=fullName>|  
|Strumień|<xref:System.IO.Stream?displayProperty=fullName>|  
  
 Ponadto następujące sufiksy powinny **nie** można użyć:  
  
-   Delegate  
  
-   Wyliczenie  
  
-   Impl — zamiast tego użyj "Podstawowe"  
  
-   Na przykład lub podobne sufiksu, w odróżnieniu od starszej wersji tego samego typu  
  
 Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Zmniejsza to nauki, jest wymagany dla nowe biblioteki oprogramowania, która zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Usuń sufiks z nazwą typu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły, chyba że sufiksem ma jednoznaczną znaczenie w domenie aplikacji.  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA1710: Identyfikatory powinny mieć poprawny sufiks](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)   
 [NIB: Zdarzenia i delegatów](http://msdn.microsoft.com/en-us/d98fd58b-fa4f-4598-8378-addf4355a115)



