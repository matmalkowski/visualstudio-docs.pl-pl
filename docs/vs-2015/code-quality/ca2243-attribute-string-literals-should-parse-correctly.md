---
title: 'CA2243: Literałów typu string atrybutów powinna przebiegać poprawnie | Dokumentacja firmy Microsoft'
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
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f9224d458e6fd61e597b8ab51393e2e6feb7aaf9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682254"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: Literały ciągu atrybutu powinny być analizowane poprawnie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2243: literałów typu string atrybutów powinna przebiegać poprawnie](https://docs.microsoft.com/visualstudio/code-quality/ca2243-attribute-string-literals-should-parse-correctly).  
  
Element TypeName | AttributeStringLiteralsShouldParseCorrectly |  
| CheckId | CA2243 |  
| Kategoria | Microsoft.Usage|  
| Zmiana powodująca niezgodność | Inne niż powodująca niezgodność |  
  
## <a name="cause"></a>Przyczyna  
 Parametr literału ciągu atrybutu nie analizuje poprawnie adresu URL, identyfikator GUID lub wersji.  
  
## <a name="rule-description"></a>Opis reguły  
 Ponieważ atrybuty są uzyskiwane z <xref:System.Attribute?displayProperty=fullName>i atrybuty są używane w czasie kompilacji, tylko wartości stałych można przekazać do ich konstruktory. Parametry atrybutów reprezentujące musi wersji, identyfikatory GUID i adresy URL nie może być typizowana jako <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName>, i <xref:System.Version?displayProperty=fullName>, ponieważ te typy nie może być reprezentowana jako stałe. Zamiast tego musi być reprezentowana przez parametry.  
  
 Ponieważ parametru zostanie podana jako ciąg znaków, jest możliwe, że w czasie kompilacji można przekazać parametr niepoprawnie sformatowany.  
  
 Ta reguła używa heurystyki nazewnictwa w celu odnalezienia parametry, które reprezentują jednolity identyfikator zasobów (URI), globalnie unikatowy identyfikator (GUID) lub wersji i sprawdza, czy przekazana wartość jest poprawna.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Zmień ciąg parametru na poprawnie sformułowany adres URL, identyfikator GUID lub wersji.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli parametr nie reprezentuje adres URL, identyfikator GUID lub wersji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera kod dla AssemblyFileVersionAttribute, który narusza tę regułę.  
  
 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]  
  
 Reguła jest wyzwalana, wykonując następujące czynności:  
  
-   Parametry, które zawierają "version" i nie można przeanalizować System.Version.  
  
-   Parametry, które zawierają "guid" i nie można przeanalizować System.Guid.  
  
-   Parametry, które zawierają "uri", "urn" lub "url" i nie można przeanalizować na System.Uri.  
  
## <a name="see-also"></a>Zobacz też  
 [CA1054: Parametry identyfikatora URI nie powinny być ciągami](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)



