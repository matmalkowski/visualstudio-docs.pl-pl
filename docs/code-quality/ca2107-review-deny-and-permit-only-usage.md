---
title: "CA2107: Przejrzyj deny i PermitOnly tylko użycia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: edd0bd14a75dfd58ca043bfaa663e2cfb2660e75
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Przejrzyj użycie akcji Deny i Permit Only
|||  
|-|-|  
|TypeName|ReviewDenyAndPermitOnlyUsage|  
|CheckId|CA2107|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Metoda zawiera kontrola zabezpieczeń, określająca akcji zabezpieczeń PermitOnly lub Odmów.  
  
## <a name="rule-description"></a>Opis reguły  
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> Zabezpieczeń akcji powinna być używana tylko przez tych, którzy mają zaawansowanej wiedzy na temat programu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zabezpieczeń. Kod, który używa tych akcji zabezpieczeń, należy poddać przeglądowi zabezpieczeń.  
  
 Odmów zmienia domyślne zachowanie przeszukiwania stosu, który występuje w odpowiedzi na żądanie zabezpieczeń. Umożliwia określenie uprawnień, które nie udziela na czas trwania odmawia metody, niezależnie od uprawnień wywołań w stosie wywołań. Jeśli przeszukiwana stosu wykrywa metody, która jest chroniony przez Odmów i żądane uprawnienie jest uwzględniony w odmówiono uprawnień, przeszukiwania stosu nie powiedzie się. PermitOnly również zmienia domyślne zachowanie przeszukiwania stosu. Dzięki temu kod, aby określić tylko te uprawnienia, które można otrzymać, niezależnie od uprawnień do wywoływania. Jeśli przeszukiwania stosu wykrywa metody, która jest chroniony przez PermitOnly i uprawnienia, które są określone przez PermitOnly nie ma wymaganego uprawnienia, przeszukiwania stosu nie powiedzie się.  
  
 Kod, który korzysta z tych akcji powinny być dokładnie oceniane pod kątem luk w zabezpieczeniach ze względu na ich ograniczone użyteczność i zachowanie niewielkie. Rozważ następujące opcje:  
  
-   [Link zapotrzebowanie](/dotnet/framework/misc/link-demands) nie dotyczy Deny i PermitOnly.  
  
-   Jeśli w tym samym ramki stosu jako żądanie, która powoduje występowanie przeszukiwania stosu występuje Deny i PermitOnly, akcje zabezpieczeń nie mają wpływu.  
  
-   Zazwyczaj można określić wartości, które są używane do konstruowania uprawnień na podstawie ścieżki na wiele sposobów. Odmowa dostępu do tego samego formularza ścieżki nie odmowa dostępu do wszystkich formularzy. Na przykład jeśli udział plików \\\Server\Share jest mapowany dysk sieciowy X:, aby odmówić dostępu do pliku w udziale, musi Odmów \\\Server\Share\File, X:\File i co ścieżki, który uzyskuje dostęp do pliku.  
  
-   <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> Przed osiągnięciem Deny i PermitOnly może zakończyć przeszukiwania stosu.  
  
-   Jeśli odmowy ma wpływ, a mianowicie, gdy obiekt wywołujący ma uprawnienia, które jest zablokowana z powodu odmowy, wywołujący można dostępu do chronionego zasobu bezpośrednio, pomijanie Odmów. Podobnie jeśli element wywołujący nie ma odmówiono uprawnienia, przeszukiwania stosu nie powiedzie się bez Odmów.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Naruszenie spowoduje, że każde korzystanie z tych akcji zabezpieczeń. Aby naprawić naruszenie, nie należy używać tych akcji zabezpieczeń.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Pomiń ostrzeżenie od tej reguły, dopiero po zakończeniu weryfikacji zabezpieczeń.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano kilka ograniczeń Odmów.  
  
 Następująca biblioteka zawiera klasy, która ma dwie metody, które są identyczne z wyjątkiem żądania kontroli zabezpieczeń, które je chronić.  
  
 [!code-csharp[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]  
  
## <a name="example"></a>Przykład  
 Następującej aplikacji pokazuje skutków Odmów zabezpieczonych metod z biblioteki.  
  
 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
 **Żądanie: Odmów wywołującego nie ma wpływu na żądanie z uprawnieniem potwierdzone.**  
**Żądanie LinkDemand: Odmów wywołującego nie ma wpływu na żądanie LinkDemand z uprawnieniem potwierdzone.**  
**Żądanie LinkDemand: Odmów wywołującego nie ma znaczenia kodem chronionej przez żądanie LinkDemand.**  
**LinkDemand: Ten Odmów nie ma znaczenia kodem chronionej przez żądanie LinkDemand.**   
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>   
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>   
 [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)   

