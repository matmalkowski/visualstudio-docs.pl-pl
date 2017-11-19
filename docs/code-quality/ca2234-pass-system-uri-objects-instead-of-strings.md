---
title: "CA2234: Przekaż obiekty System.Uri zamiast ciągów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 99001a5406ce4e70e0e76670eba250073ce030b2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: Przekaż obiekty System.Uri zamiast ciągów
|||  
|-|-|  
|TypeName|PassSystemUriObjectsInsteadOfStrings|  
|CheckId|CA2234|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Wywołanie metody, która ma parametr typu string, których nazwa zawiera "uri", "Identyfikator Uri", "urn", "Urn", "url" lub "Url"; i typ deklarujący metodzie zawiera odpowiednie przeciążenie metody, która ma <xref:System.Uri?displayProperty=fullName> parametru.  
  
## <a name="rule-description"></a>Opis reguły  
 Nazwa parametru jest podzielony na tokeny na podstawie Konwencji mieszanej wielkości liter, a następnie każdy token jest sprawdzane pod kątem Zobacz, czy ma on wartość równą "uri", "Identyfikator Uri", "urn", "Urn", "url" lub "Url". Jeśli istnieje dopasowanie, parametr przyjęto, że do reprezentowania identyfikator uniform resource identifier (URI). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. <xref:System.Uri> Klasa udostępnia tych usług w sposób bezpieczny i bezpieczne. Gdy istnieje wybór między dwa przeciążenia, które różnią się tylko dotyczące reprezentację identyfikatora URI, użytkownik powinien wybrać przeciążenia, które przyjmuje <xref:System.Uri> argumentu.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, wywoływać przeciążenia przyjmuje <xref:System.Uri> argumentu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli parametr ciągu nie reprezentuje identyfikator URI.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono metodę, `ErrorProne`, który narusza regułę, a także metodę `SaferWay`, który prawidłowo wywołuje <xref:System.Uri> przeciążenia.  
  
 [!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
 [!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
 [!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1057: Ciąg URI wywołują przeciążenia System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)  
  
 [CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: Zwracane identyfikatora URI wartości nie powinny być ciągami](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)