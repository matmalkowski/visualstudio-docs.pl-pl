---
title: 'CA2140: Kod przezroczysty nie może odwoływać się elementów krytycznych dla zabezpieczeń | Dokumentacja firmy Microsoft'
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
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f27cf2fdefc8d3ea6e9e513aef729fc32198b722
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679215"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Jawny kod nie może odwoływać się do elementów krytycznych dla zabezpieczeń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2140: kod przezroczysty nie może odwoływać się elementów krytycznych dla zabezpieczeń](https://docs.microsoft.com/visualstudio/code-quality/ca2140-transparent-code-must-not-reference-security-critical-items).  
  
Element TypeName | TransparentMethodsMustNotReferenceCriticalCode |  
| CheckId | CA2140 |  
| Kategoria | Microsoft.Security|  
| Zmiana powodująca niezgodność | Przerwanie |  
  
## <a name="cause"></a>Przyczyna  
 Metoda przezroczysty.  
  
-   obsługuje typ wyjątków krytycznych zabezpieczeń  
  
-   ma parametr, który jest oznaczony jako typu krytycznego dla zabezpieczeń  
  
-   ma parametr ogólny z ograniczeniami krytyczne zabezpieczeń  
  
-   ma zmiennej lokalnej typu krytycznego dla zabezpieczeń  
  
-   odwołuje się do typu, która jest oznaczona jako zabezpieczeń krytycznych  
  
-   wywołuje metodę, która jest oznaczona jako zabezpieczeń krytycznych  
  
-   odwołuje się do pola, która jest oznaczona jako zabezpieczeń krytycznych  
  
-   Zwraca typ, który jest oznaczony jako zabezpieczeń krytycznych  
  
## <a name="rule-description"></a>Opis reguły  
 Element kodu, który jest oznaczony za pomocą <xref:System.Security.SecurityCriticalAttribute> atrybutu jest krytyczny dla bezpieczeństwa. Przezroczysta metoda nie może użyć elementu krytycznego dla zabezpieczeń. Jeśli przezroczysty typ próbuje użyć typu krytycznego dla zabezpieczeń <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , lub <xref:System.FieldAccessException> jest wywoływane.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, wykonaj jedną z następujących czynności:  
  
-   Oznacz element kodu, który korzysta z kodu krytycznego zabezpieczeń za pomocą <xref:System.Security.SecurityCriticalAttribute> atrybutu  
  
     \- lub —  
  
-   Usuń <xref:System.Security.SecurityCriticalAttribute> atrybut od elementów kodu, które są oznaczone jako zabezpieczeń krytycznych i zamiast tego oznacz je za pomocą <xref:System.Security.SecuritySafeCriticalAttribute> lub <xref:System.Security.SecurityTransparentAttribute> atrybutu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach metoda przezroczysta pod względem próbuje odwołania zabezpieczeń krytycznych kolekcji ogólnych, zabezpieczeń krytycznych pola i metody krytycznej zabezpieczeń.  
  
 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityCriticalAttribute>   
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityTreatAsSafeAttribute>   
 <xref:System.Security?displayProperty=fullName>



