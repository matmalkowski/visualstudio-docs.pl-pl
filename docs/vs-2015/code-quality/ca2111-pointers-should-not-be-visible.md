---
title: 'CA2111: Wskaźniki nie powinny być widoczne | Dokumentacja firmy Microsoft'
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
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 196d0f378164c2ee9109afa0fae53d79211653c7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42627978"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Wskaźniki nie powinny być widoczne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2111: wskaźniki nie powinny być widoczne](https://docs.microsoft.com/visualstudio/code-quality/ca2111-pointers-should-not-be-visible).  
  
Element TypeName | PointersShouldNotBeVisible |  
| CheckId | CA2111 |  
| Kategoria | Microsoft.Security|  
| Zmiana powodująca niezgodność | Przerwanie |  
  
## <a name="cause"></a>Przyczyna  
 Publiczny lub chroniony <xref:System.IntPtr?displayProperty=fullName> lub <xref:System.UIntPtr?displayProperty=fullName> pole nie jest tylko do odczytu.  
  
## <a name="rule-description"></a>Opis reguły  
 <xref:System.IntPtr> i <xref:System.UIntPtr> są typami wskaźnika, które są używane do uzyskiwania dostępu do niezarządzanej pamięci. Jeżeli wskaźnik nie jest prywatny, wewnętrzny ani tylko do odczytu, złośliwy kod może zmienić wartość wskaźnika, potencjalnie umożliwiając dostęp do dowolnego miejsca w pamięci lub powodując błędy aplikacji lub systemu.  
  
 Jeśli zamierzasz bezpieczny dostęp do typu, która zawiera pole wskaźnika, zobacz [CA2112: typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Zabezpiecz wskaźnik, czyniąc ją tylko do odczytu, wewnętrzny lub prywatny.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Pomijaj ostrzeżeń dla tej reguły, jeśli użytkownik nie należy polegać na wartość wskaźnika.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia wskaźników, które naruszają i spełniać reguły. Zwróć uwagę, że wskaźniki nieprywatny również narusza regułę [CA1051: nie deklaruj widocznych pól wystąpień](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).  
  
 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA2112: Typy zabezpieczone nie powinny ujawniać pól](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA1051: Nie deklaruj widocznych pól wystąpienia](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>



