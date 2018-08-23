---
title: 'CA1033: Metody interfejsu powinny móc przez typy podrzędne | Dokumentacja firmy Microsoft'
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
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 206a2095fe457044353f6002e9b6bd468de4f306
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42628793"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: Typy potomne powinny móc wywoływać metody interfejsu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1033: metody interfejsu powinny być wywołane przez typy podrzędne](https://docs.microsoft.com/visualstudio/code-quality/ca1033-interface-methods-should-be-callable-by-child-types).  
  
Element TypeName | InterfaceMethodsShouldBeCallableByChildTypes |  
| CheckId | CA1033 |  
| Kategoria | Microsoft.Design|  
| Zmiana powodująca niezgodność | Bez podziału |  
  
## <a name="cause"></a>Przyczyna  
 Niezapieczętowany typ widoczny na zewnątrz zapewnia jawną implementację metody interfejsu publicznego i nie dostarcza alternatywnej metody widocznej z zewnątrz o tej samej nazwie.  
  
## <a name="rule-description"></a>Opis reguły  
 Należy wziąć pod uwagę typu podstawowego, który jawnie implementuje metodę interfejsu publicznego. Typ, który pochodzi od typu podstawowego mogą uzyskiwać dostęp do metody dziedziczony interfejs wyłącznie za pośrednictwem odwołanie do bieżącego wystąpienia (`this` w języku C#), jest rzutowane na interfejs. Jeśli typ pochodny implementuje (jawne) ponownie metodę dziedziczony interfejs, Podstawowa implementacja nie jest już możliwy. Wywołanie przez odwołanie do bieżącego wystąpienia wywoła pochodnej; Powoduje to rekursji i przepełnienie stosu ostateczną.  
  
 Ta zasada zgłasza naruszenie dla jawnych implementacji <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> gdy jest to widoczne na zewnątrz `Close()` lub `System.IDisposable.Dispose(Boolean)` podana metoda.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, zaimplementuj nową metodę uwidacznia taką samą funkcjonalność, która jest widoczna dla typów pochodnych, lub zmień niejawne implementacji. Jeśli istotną zmianę, alternatywą jest zapewnienie typu zapieczętowany.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli metoda widoczna na zewnątrz, ma taką samą funkcjonalność, ale inną nazwę niż metoda jawnie implementowane.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano typu, `ViolatingBase`, który narusza regułę i typu `FixedBase`, który zawiera poprawkę rozwiązującą naruszenia.  
  
 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExplicitMethodImplementations/cs/FxCop.Design.ExplicitMethodImplementations.cs#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy](http://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)



