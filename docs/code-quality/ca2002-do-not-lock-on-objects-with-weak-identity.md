---
title: "CA2002: Nie należy blokować obiektów z słabą tożsamością | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
ms.assetid: 16100b39-c6fc-452b-8fca-8b459a26c286
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 55bc495f116b4a7be8c118b47c71a9fed9f85777
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002: Nie należy blokować obiektów z słabą tożsamością
|||  
|-|-|  
|TypeName|DoNotLockOnObjectsWithWeakIdentity|  
|CheckId|CA2002|  
|Kategoria|Microsoft.Reliability|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Wątek próbuje uzyskać blokady obiektu, który ma słabej tożsamości.  
  
## <a name="rule-description"></a>Opis reguły  
 Obiekt ma słabą tożsamość, gdy można uzyskać do niego bezpośredni dostęp poza granicami domeny aplikacji. Wątek, który próbuje uzyskać blokadę na obiekcie o słabej tożsamości, może zostać zablokowany przez drugi wątek w domenie innej aplikacji, która ma blokady dla tego samego obiektu. Następujące typy mają słaby tożsamości i są oznaczone przez regułę:  
  
-   <xref:System.MarshalByRefObject>  
  
-   <xref:System.ExecutionEngineException>  
  
-   <xref:System.OutOfMemoryException>  
  
-   <xref:System.StackOverflowException>  
  
-   <xref:System.String>  
  
-   <xref:System.Reflection.MemberInfo>  
  
-   <xref:System.Reflection.ParameterInfo>  
  
-   <xref:System.Threading.Thread>  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, użyj obiektu z typem, który nie jest na liście w sekcji Opis.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="related-rules"></a>Powiązanych reguł  
 [CA2213: Pola możliwe do likwidacji powinny zostać zlikwidowane](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono niektóre blokady obiektu, które naruszają zasady.  
  
 [!code-vb[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/VisualBasic/ca2002-do-not-lock-on-objects-with-weak-identity_1.vb)]
 [!code-csharp[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/CSharp/ca2002-do-not-lock-on-objects-with-weak-identity_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Monitor>   
 <xref:System.AppDomain>   
 [Lock — instrukcja](/dotnet/csharp/language-reference/keywords/lock-statement)   
 [SyncLock, instrukcja](/dotnet/visual-basic/language-reference/statements/synclock-statement)