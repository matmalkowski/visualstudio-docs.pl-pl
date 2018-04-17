---
title: 'CA1057: Ciąg URI wywołują przeciążenia System.Uri | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 18b38dab9ad7a2a3065b78a1d73bbadee2c28f28
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Przeciążenia identyfikatora URI, który jest ciągiem, wywołują przeciążenia System.Uri
|||  
|-|-|  
|TypeName|StringUriOverloadsCallSystemUriOverloads|  
|CheckId|CA1057|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Typ deklaruje przeciążenia metody, które różnią się tylko przez zastąpienie parametr typu string z <xref:System.Uri?displayProperty=fullName> parametr i przeciążenia, które przyjmuje parametr ciągu nie mogą wywoływać przeciążenia, które przyjmuje <xref:System.Uri> parametru.  
  
## <a name="rule-description"></a>Opis reguły  
 Ponieważ przeciążeń różnią się tylko ciąg /<xref:System.Uri> parametru ciągu zakłada się, że reprezentuje identyfikator uniform resource identifier (URI). Reprezentacja ciągu identyfikatora URI jest podatna na analizowanie i kodowanie błędów i może prowadzić do powstawania luk w zabezpieczeniach. <xref:System.Uri> Klasa udostępnia tych usług w sposób bezpieczny i bezpieczne. Do czerpania korzyści z <xref:System.Uri> klasy, powinny wywoływać przeciążenia dla typu string <xref:System.Uri> przeciążenia przy użyciu argumentu ciągu.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Ponownej implementacji metody, która używa reprezentację ciągu identyfikatora URI, dzięki czemu tworzy wystąpienie <xref:System.Uri> przy użyciu argument ciągu, a następnie przekazuje <xref:System.Uri> obiekt do przeciążenia, które ma <xref:System.Uri> parametru.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli parametr ciągu nie reprezentuje identyfikator URI.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono przeciążenia ciągu poprawnie zaimplementowana.  
  
 [!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
 [!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2234: Przekaż obiekty System.Uri zamiast ciągów](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1056: Właściwości identyfikatora URI nie powinny być ciągami](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: Wartości zwracane identyfikatora URI nie powinny być ciągami](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)