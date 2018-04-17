---
title: 'CA2112: Typy zabezpieczone nie powinny ujawniać pól | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 050aa2a5048ed4d58e6b5a285f584eda330f178f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: Typy zabezpieczone nie powinny uwidaczniać pól
|||  
|-|-|  
|TypeName|SecuredTypesShouldNotExposeFields|  
|CheckId|CA2112|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Typu publiczne lub chronione zawiera pola publiczne i jest chroniony przez [Linkdemand](/dotnet/framework/misc/link-demands).  
  
## <a name="rule-description"></a>Opis reguły  
 Jeśli kod ma dostęp do wystąpienia typu zabezpieczonego przez żądanie łącza, kod nie musi spełniać zapotrzebowania na łącza, aby uzyskać dostęp do pól typu.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, ustawianie niepublicznych pól i dodać publicznej właściwości lub metody, które zwracają dane pola. Kontrole zabezpieczeń LinkDemand dla typów ochrony dostępu do właściwości i metod typu. Jednak zabezpieczenia dostępu kodu nie ma zastosowania do pól.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Zarówno w przypadku problemów z zabezpieczeniami i dobrej projektu należy naprawić naruszeń dokonując nonpublic pola publiczne. Ostrzeżenie od tej reguły można pominąć, jeśli pole nie zawiera informacje, które powinny pozostać zabezpieczonych i nie należy polegać na zawartość tego pola.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład składa się z typu biblioteki (`SecuredTypeWithFields`) z polami niezabezpieczoną, typem (`Distributor`) który można utworzyć wystąpienia typu biblioteki i przekazuje omyłkowo wystąpiła wystąpień typów nie ma uprawnienia do tworzenia ich i kodu aplikacji mogą odczytywać pól wystąpień, nawet jeśli nie ma uprawnień, która zabezpiecza typu.  
  
 Poniższy kod biblioteki naruszają tę regułę.  
  
 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]  
  
## <a name="example"></a>Przykład  
 Aplikacji nie można utworzyć wystąpienia z powodu linkdemand, która chroni zabezpieczonych typu. Następujące klasy umożliwia aplikacji można uzyskać wystąpienia typu zabezpieczonych.  
  
 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]  
  
## <a name="example"></a>Przykład  
 Następującej aplikacji przedstawiono, jak, bez uprawnienia do zabezpieczonej typu metody dostępu kodu można uzyskać dostęp do swoich pól.  
  
 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
 **Tworzenie wystąpienia SecuredTypeWithFields.**  
**Typ pola zabezpieczone: 22, 33**  
**Zmienianie typu zabezpieczonych pól...**  
**Pola obiektu w pamięci podręcznej: 99, 33**   
## <a name="related-rules"></a>Powiązanych reguł  
 [CA1051: Nie deklaruj widocznych pól wystąpienia](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Żądania łączy](/dotnet/framework/misc/link-demands)   
 [Dane i modelowanie](/dotnet/framework/data/index)