---
title: "CA1820: Zbadaj obecność pustych ciągów przy użyciu długości ciągu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d044f09ca26b65506bcfb7466f59da73acfad1e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Zbadaj pod kątem ciągów pustych przy użyciu długości ciągu
|||  
|-|-|  
|TypeName|TestForEmptyStringsUsingStringLength|  
|CheckId|CA1820|  
|Kategoria|Microsoft.Performance|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Ciąg jest porównywany z ciągiem pustym przy użyciu <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Opis reguły  
 Porównywanie ciągów za pomocą <xref:System.String.Length%2A?displayProperty=fullName> właściwości lub <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> metoda jest znacznie szybsza niż przy użyciu <xref:System.Object.Equals%2A>. Jest to spowodowane <xref:System.Object.Equals%2A> wykonuje znacznie więcej instrukcje MSIL niż albo <xref:System.String.IsNullOrEmpty%2A> lub liczbę instrukcji wykonywany w celu pobrania <xref:System.String.Length%2A> właściwości wartość i porównania go od zera.  
  
 Należy pamiętać, że <xref:System.Object.Equals%2A> i <xref:System.String.Length%2A> == 0 zachowywać się inaczej dla ciągów o wartości null. Jeśli spróbujesz uzyskać wartość <xref:System.String.Length%2A> właściwości na pusty ciąg, środowisko uruchomieniowe języka wspólnego zgłasza <xref:System.NullReferenceException?displayProperty=fullName>. Przeprowadzenie porównania pusty ciąg pusty ciąg, środowisko uruchomieniowe języka wspólnego nie zgłasza wyjątek; Zwraca wynik porównania `false`. Testowanie pod kątem wartości null nie znaczącego wpływu na te dwie metody względną wydajność. Jeśli celem [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], użyj <xref:System.String.IsNullOrEmpty%2A> metody. W przeciwnym razie użyj <xref:System.String.Length%2A> == porównania, jeśli to możliwe.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby usunąć naruszenie tej reguły, zmienić porównywania <xref:System.String.Length%2A> właściwości i test na pusty ciąg. Jeśli celem [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], użyj <xref:System.String.IsNullOrEmpty%2A> metody.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli wydajność nie ma problemu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia różne techniki, które są używane do wyszukania ciągiem pustym.  
  
 [!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]