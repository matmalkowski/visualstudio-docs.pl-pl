---
title: 'CA2147: Jawne metody nie mogą używać zabezpieczeń potwierdzeń | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 75d841da0c738ff7504e95b372ecd4e06f9c77f2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Jawne metody nie mogą używać potwierdzeń zabezpieczeń
|||  
|-|-|  
|TypeName|SecurityTransparentCodeShouldNotAssert|  
|CheckId|CA2147|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Kod, który jest oznaczony jako <xref:System.Security.SecurityTransparentAttribute> nie udzielono uprawnień wystarczających do potwierdzenia.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta zasada analizuje wszystkie metody i typów w zestawie, który jest albo 100% przezroczysty lub mieszane przezroczysty/krytycznych, a wszelkie deklaratywne lub konieczne użycie flagi <xref:System.Security.CodeAccessPermission.Assert%2A>.  
  
 W czasie, wszelkie wywołania wykonywania <xref:System.Security.CodeAccessPermission.Assert%2A> z kod o przezroczystym spowoduje <xref:System.InvalidOperationException> zostanie wygenerowany. Taka sytuacja może wystąpić w obu zestawach przezroczysty 100%, a także w zestawy mieszane przezroczysty/krytycznych, w którym jest zadeklarowany jako przezroczysty metody lub typu, ale zawiera Assert deklaratywne lub imperatywnych.  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 wprowadzono funkcję o nazwie *przezroczystość*. Indywidualne metody, pola, interfejsów, klas i typów może być przezroczysty lub krytyczny.  
  
 Kod o przezroczystym jest niedozwolone podniesienia uprawnień zabezpieczeń. W związku z tym wszystkie uprawnienia przyznane lub żądać go są automatycznie przekazywane do kodu do domeny aplikacji obiektu wywołującego lub hosta. Wybierającym przykłady potwierdzenia, LinkDemands, SuppressUnmanagedCode, i `unsafe` kodu.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać ten problem, albo oznaczenie kod, który wywołuje Assert z <xref:System.Security.SecurityCriticalAttribute>, lub usuń Assert.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj wiadomości z tej reguły.  
  
## <a name="example"></a>Przykład  
 Ten kod zakończy się niepowodzeniem, jeśli `SecurityTestClass` jest niewidoczny, gdy `Assert` metoda zgłasza <xref:System.InvalidOperationException>.  
  
 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]  
  
## <a name="example"></a>Przykład  
 Jedną z opcji do przeglądu kodu w poniższym przykładzie metody SecurityTransparentMethod oraz czy metoda jest uznawane za bezpieczne dla podniesienia uprawnień, oznacz SecurityTransparentMethod z bezpieczny krytyczny takie rozwiązanie wymaga zabezpieczeń szczegółowe, kompletne i błędów inspekcji należy wykonać dla metody wraz z dowolnego wywołania danych ukazane znajdujących się w metodzie, w obszarze Assert:  
  
 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]  
  
 Innym rozwiązaniem jest usunięcie Assert z kodu i umożliwić dowolnego pliku kolejnych operacji We/Wy przepływu żądania uprawnień poza SecurityTransparentMethod do obiektu wywołującego. Dzięki temu kontroli zabezpieczeń. W takim przypadku nie inspekcji zabezpieczeń nie jest zazwyczaj konieczne, ponieważ żądania uprawnień będą przepływać do wywołującego i/lub domeny aplikacji. Żądania uprawnień ściśle są kontrolowane przez zasady zabezpieczeń, hostowania środowiska i Udziel uprawnień kodu źródłowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Ostrzeżenia dotyczące zabezpieczeń](../code-quality/security-warnings.md)