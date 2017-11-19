---
title: "CA2230: Użyj parametrów dla zmiennych argumentów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 10920c4ff9083b52e2d35f7fa151644b89bb1102
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Użyj parametrów dla zmiennych argumentów
|||  
|-|-|  
|TypeName|UseParamsForVariableArguments|  
|CheckId|CA2230|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Typu publiczne lub chronione zawiera publiczne lub chronione metody, która używa `VarArgs` konwencji wywoływania.  
  
## <a name="rule-description"></a>Opis reguły  
 `VarArgs` Konwencji wywoływania jest używany z definicjami niektórych metod, przyjmujących zmienną liczbą parametrów. Przy użyciu metody `VarArgs` konwencji wywoływania nie jest typowe Language Specification () zgodny z CLS i mogą nie być dostępne w językach programowania.  
  
 W języku C# `VarArgs` konwencji wywoływania jest używany po liście parametrów metody kończy się wyrazem `__arglist` — słowo kluczowe. Język Visual Basic nie obsługuje `VarArgs` wywoływanie Konwencji i Visual C++ umożliwia wykorzystanie przez niego tylko za pomocą kodu niezarządzanego, który używa elipsy `...` notacji.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły w języku C#, użyj [params](/dotnet/csharp/language-reference/keywords/params) słowa kluczowego zamiast `__arglist`.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono dwie metody, które naruszają tę regułę i spełniająca reguły.  
  
 [!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>   
 [Niezależność od języka i elementy niezależne od języka](http://msdn.microsoft.com/Library/4f0b77d0-4844-464f-af73-6e06bedeafc6)