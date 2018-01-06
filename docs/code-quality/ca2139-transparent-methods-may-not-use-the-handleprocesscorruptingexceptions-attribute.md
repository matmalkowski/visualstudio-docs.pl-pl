---
title: "CA2139: Jawne metody nie mogą używać atrybutu HandleProcessCorruptingExceptions | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3852955704bb218ac252d4c4c5edbbf1a0f5927c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: Jawne metody mogą nie używać atrybutu HandleProcessCorruptingExceptions
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|  
|CheckId|CA2139|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Przezroczysty metoda jest oznaczona atrybutem <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atrybutu.  
  
## <a name="rule-description"></a>Opis reguły  
 Ta zasada wyzwala dowolnej metody, która działa w sposób niewidoczny i próbuje przeprowadzić obsługi procesu uszkodzenia wyjątek przy użyciu <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atrybutu. Proces uszkodzenia wyjątku jest klasyfikację wyjątków CLR w wersji 4.0 wyjątków takich <xref:System.AccessViolationException>. Atrybut HandleProcessCorruptedStateExceptionsAttribute może być używany tylko przez metody krytyczne pod względem bezpieczeństwa i będzie ignorowany, jeśli zostanie zastosowany do metody przezroczystej. Do obsługi wyjątków błędny procesu, ta metoda musi stać się krytyczne lub bezpieczne-krytyczne.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, Usuń <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atrybutu lub Oznacz metodę z <xref:System.Security.SecurityCriticalAttribute> lub <xref:System.Security.SecuritySafeCriticalAttribute> atrybutu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przezroczysty metoda jest oznaczona atrybutem <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atrybutu i reguła nie zostanie ukończona. Metoda również powinien być oznaczony przez <xref:System.Security.SecurityCriticalAttribute> lub <xref:System.Security.SecuritySafeCriticalAttribute> atrybutu.  
  
 [!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../code-quality/codesnippet/CSharp/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute_1.cs)]