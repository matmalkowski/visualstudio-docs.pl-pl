---
title: "CA2111: Wskaźniki nie powinny być widoczne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 31ae25892b6b5a153a0a4d1e52047eb5be2368d1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Wskaźniki nie powinny być widoczne
|||  
|-|-|  
|TypeName|PointersShouldNotBeVisible|  
|CheckId|CA2111|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 A public lub protected <xref:System.IntPtr?displayProperty=fullName> lub <xref:System.UIntPtr?displayProperty=fullName> pole nie jest tylko do odczytu.  
  
## <a name="rule-description"></a>Opis reguły  
 <xref:System.IntPtr>i <xref:System.UIntPtr> typów wskaźnika, które są używane do uzyskiwania dostępu do pamięci niezarządzanej. Jeśli wskaźnik nie jest prywatny, wewnętrzny lub tylko do odczytu, złośliwy kod może zostać zmieniona wartość wskaźnika potencjalnie zezwalania na dostęp do dowolnego miejsca w pamięci lub powodujące błędy aplikacji lub systemu.  
  
 Jeśli zamierzasz bezpieczny dostęp do typu, który zawiera pole wskaźnika, zobacz [CA2112: typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Zabezpiecz wskaźnik czyniąc ją tylko do odczytu, wewnętrzny ani prywatny.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Pomiń ostrzeżenie od tej reguły, jeśli użytkownik nie należy polegać na wartość wskaźnika.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia wskaźniki narusza, które spełniają reguły. Powiadomienie, że wskaźniki-prywatnych również narusza regułę [CA1051: nie deklaruj widocznych pól wystąpień](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).  
  
 [!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2112: Typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA1051: Nie deklaruj widocznych pól wystąpienia](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>