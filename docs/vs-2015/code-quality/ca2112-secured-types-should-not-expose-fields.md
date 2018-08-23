---
title: 'CA2112: Typy zabezpieczone nie powinny ujawniać pól | Dokumentacja firmy Microsoft'
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
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a7fc26780ffb3015c71ecac934e217d50eb81452
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679047"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: Typy zabezpieczone nie powinny uwidaczniać pól
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2112: typy zabezpieczone nie powinny ujawniać pól](https://docs.microsoft.com/visualstudio/code-quality/ca2112-secured-types-should-not-expose-fields).  
  
Element TypeName | SecuredTypesShouldNotExposeFields |  
| CheckId | CA2112 |  
| Kategoria | Microsoft.Security|  
| Zmiana powodująca niezgodność | Przerwanie |  
  
## <a name="cause"></a>Przyczyna  
 Typ publiczny lub chroniony zawiera pola publiczne i jest zabezpieczony przez [zapotrzebowania na łącza](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).  
  
## <a name="rule-description"></a>Opis reguły  
 Jeśli kod ma dostęp do wystąpienia typu zabezpieczonego przez żądanie łącza, kod nie musi spełniać zapotrzebowania na łącza, aby uzyskać dostęp do pól typu.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, ustawianie niepublicznych pól i dodać publiczny właściwości lub metody, które zwracają pola danych. Kontrole zabezpieczeń żądanie LinkDemand dla typów ochrony dostępu do właściwości i metod typu. Zabezpieczenia dostępu kodu nie ma zastosowania do pól.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Zarówno związane z zabezpieczeniami i dobrego projektowania należy naprawić naruszenia, wprowadzając nonpublic pola publiczne. Ostrzeżenie od tej reguły można pominąć, jeśli pole nie zawiera informacje, które powinny być zabezpieczone. Ponadto nie należy polegać na zawartości pola.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład składa się z typu biblioteki (`SecuredTypeWithFields`) z polami niezabezpieczone, typu (`Distributor`), można utworzyć wystąpienia typu biblioteki i przekazuje omyłkowe wystąpień typów nie masz uprawnień do ich utworzenia i kodu aplikacji może odczytywać pól wystąpień, nawet jeśli nie ma uprawnienia, które zabezpiecza typu.  
  
 Poniższy kod biblioteki narusza regułę.  
  
 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]  
  
## <a name="example"></a>Przykład  
 Aplikacja nie można utworzyć wystąpienia ze względu na żądanie łącza, które chroni zabezpieczonego typu. Następujące klasy umożliwia aplikacji, aby uzyskać wystąpienia typu zabezpieczonego.  
  
 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]  
  
## <a name="example"></a>Przykład  
 Następująca aplikacja ilustruje, jak to zrobić, bez uprawnienia dostępu metody zabezpieczonego typu, kod może uzyskać dostęp jej pola.  
  
 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]  
  
 Ten przykład generuje następujące dane wyjściowe.  
  
 **Tworzenie wystąpienia SecuredTypeWithFields.**  
**Typ pola zabezpieczone: 22, 33**  
**Zmienianie pola zabezpieczonego typu...**  
**Buforowane pola obiektu: 99, 33**   
## <a name="related-rules"></a>Powiązane reguły  
 [CA1051: Nie deklaruj widocznych pól wystąpienia](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zapotrzebowanie na łącza](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)   
 [Dane i modelowanie](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



