---
title: "CA2140: Jawny kod nie może odwoływać elementów krytycznych dla zabezpieczeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
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
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0970bd3a05975707cbbac3f79dbece234adb16ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Jawny kod nie może odwoływać się do elementów krytycznych dla zabezpieczeń
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|  
|CheckId|CA2140|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Metoda przezroczysty.  
  
-   obsługuje typ wyjątków krytycznych zabezpieczeń  
  
-   Parametr oznaczony jako typ krytyczne zabezpieczeń  
  
-   Parametr ogólny z ograniczeniami krytyczne zabezpieczeń  
  
-   ma zmiennej lokalnej typu krytycznego zabezpieczeń  
  
-   odwołuje się do typu, który jest oznaczony jako zabezpieczenia krytyczne  
  
-   wywołuje metodę, która jest oznaczona jako zabezpieczenia krytyczne  
  
-   odwołuje się do pola, który jest oznaczony jako zabezpieczenia krytyczne  
  
-   Zwraca typ, który jest oznaczony jako zabezpieczenia krytyczne  
  
## <a name="rule-description"></a>Opis reguły  
 Element kodu, który jest oznaczony atrybutem <xref:System.Security.SecurityCriticalAttribute> atrybut jest krytyczne dla zabezpieczeń. Przezroczysta metoda nie może użyć elementu krytycznego dla zabezpieczeń. Jeśli typem przezroczysty próbuje użyć zabezpieczenia krytyczne <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , lub <xref:System.FieldAccessException> jest wywoływane.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, wykonaj jedną z następujących czynności:  
  
-   Oznacz element kodu, który korzysta z kodu krytycznego dla zabezpieczeń z <xref:System.Security.SecurityCriticalAttribute> atrybutu  
  
     \-lub -  
  
-   Usuń <xref:System.Security.SecurityCriticalAttribute> atrybut z elementy kodu, które są oznaczone jako zabezpieczenia krytyczne i zamiast tego oznacz je za pomocą <xref:System.Security.SecuritySafeCriticalAttribute> lub <xref:System.Security.SecurityTransparentAttribute> atrybutu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach przezroczysty — metoda próbuje odwołać zabezpieczeń kolekcji ogólny krytycznych, pola krytyczne zabezpieczeń i krytyczne metodę zabezpieczeń.  
  
 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityCriticalAttribute>   
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityTreatAsSafeAttribute>   
 <xref:System.Security?displayProperty=fullName>