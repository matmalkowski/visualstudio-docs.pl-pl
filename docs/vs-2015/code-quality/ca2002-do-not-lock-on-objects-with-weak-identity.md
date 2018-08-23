---
title: 'CA2002: Nie blokuj obiektów o słabej tożsamości | Dokumentacja firmy Microsoft'
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
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
ms.assetid: 16100b39-c6fc-452b-8fca-8b459a26c286
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 95686c7e76fd1ed1dee442d914186ef2cc53bb7c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681225"
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002: Nie należy blokować obiektów z słabą tożsamością
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2002: nie blokuj obiektów o słabej tożsamości](https://docs.microsoft.com/visualstudio/code-quality/ca2002-do-not-lock-on-objects-with-weak-identity).  
  
Element TypeName | DoNotLockOnObjectsWithWeakIdentity |  
| CheckId | CA2002 |  
| Kategoria | Microsoft.Reliability|  
| Zmiana powodująca niezgodność | Bez podziału |  
  
## <a name="cause"></a>Przyczyna  
 Wątek próbuje uzyskać blokadę na obiekcie o słabej tożsamości.  
  
## <a name="rule-description"></a>Opis reguły  
 Obiekt ma słabą tożsamość, gdy można uzyskać do niego bezpośredni dostęp poza granicami domeny aplikacji. Wątek, który próbuje uzyskać blokadę na obiekcie o słabej tożsamości, może zostać zablokowany przez drugi wątek w domenie innej aplikacji, która ma blokady dla tego samego obiektu. Następujące typy ma słabą tożsamość i są oznaczone przez regułę:  
  
-   <xref:System.MarshalByRefObject>  
  
-   <xref:System.ExecutionEngineException>  
  
-   <xref:System.OutOfMemoryException>  
  
-   <xref:System.StackOverflowException>  
  
-   <xref:System.String>  
  
-   <xref:System.Reflection.MemberInfo>  
  
-   <xref:System.Reflection.ParameterInfo>  
  
-   <xref:System.Threading.Thread>  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, użyj obiektu z typem, który nie ma na liście w sekcji Opis.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA2213: Pola możliwe do likwidacji powinny zostać zlikwidowane](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia niektóre blokady obiektu, które naruszają reguły.  
  
 [!code-csharp[FxCop.Reliability.LockWeakObjects#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/cs/FxCop.Reliability.LockWeakObjects.cs#1)]
 [!code-vb[FxCop.Reliability.LockWeakObjects#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/vb/FxCop.Reliability.LockWeakObjects.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Monitor>   
 <xref:System.AppDomain>   
 [Lock — instrukcja](http://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42)   
 [SyncLock, instrukcja](http://msdn.microsoft.com/library/14501703-298f-4d43-b139-c4b6366af176)



