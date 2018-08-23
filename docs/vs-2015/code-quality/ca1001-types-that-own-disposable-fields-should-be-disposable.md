---
title: 'CA1001: Typy, które posiadają pola usuwalne powinny być usuwalne | Dokumentacja firmy Microsoft'
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
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bf86ab422851e27eafbb165968d4005cba7ecf5d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676557"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Typy, które posiadają pola usuwalne, powinny być usuwalne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|  
|CheckId|CA1001|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Bez podziału — Jeśli typ nie jest widoczna spoza zestawu.<br /><br /> Przerywanie — Jeśli typ jest widoczna spoza zestawu.|  
  
## <a name="cause"></a>Przyczyna  
 Klasa deklaruje i implementuje pole wystąpienia, która jest <xref:System.IDisposable?displayProperty=fullName> typ i klasa nie implementuje <xref:System.IDisposable>.  
  
## <a name="rule-description"></a>Opis reguły  
 Klasa implementuje <xref:System.IDisposable> interfejsu do usuwania niezarządzanych zasobów, w których jest właścicielem. Pole wystąpienia, która jest <xref:System.IDisposable> typu wskazuje, że pole posiada niezarządzany zasób. Klasa, która deklaruje <xref:System.IDisposable> pola pośrednio posiada niezarządzany zasób i powinna implementować <xref:System.IDisposable> interfejsu. Jeśli klasa bezpośrednio nie ma żadnych niezarządzanych zasobów, nie należy implementować finalizatora.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, należy zaimplementować <xref:System.IDisposable> i <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> wywołania metody <xref:System.IDisposable.Dispose%2A> metody pól.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano klasę, która narusza regułę określającą oraz klasę, która spełnia regułę poprzez implementację <xref:System.IDisposable>. Klasa nie implementuje finalizator, ponieważ klasa nie posiada bezpośrednio wszelkie niezarządzane zasoby.  
  
 [!code-csharp[FxCop.Design.DisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/cs/FxCop.Design.DisposableFields.cs#1)]
 [!code-vb[FxCop.Design.DisposableFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/vb/FxCop.Design.DisposableFields.vb#1)]  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA2213: Pola możliwe do likwidacji powinny zostać zlikwidowane](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2216: Typy możliwe do likwidacji powinny deklarować finalizator](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA2215: Metody Dispose powinny wywoływać metodę Dispose klasy podstawowej](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA1049: Typy z zasobami natywnymi powinny być możliwe do likwidacji](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

