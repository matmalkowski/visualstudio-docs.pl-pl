---
title: "CA1025: Zastąp powtarzalne argumenty tablicą params | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 910be06a7d9897f306b6bb2b89ca99b733623faf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Zastąp powtarzające się argumenty tabelą parametrów
|||  
|-|-|  
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|  
|CheckId|CA1025|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Publiczne lub chronione metody w typie publicznego ma więcej niż trzy parametry, a jego ostatnie trzy parametry są tego samego typu.  
  
## <a name="rule-description"></a>Opis reguły  
 Użyj tablicy parametrów zamiast powtarzane argumenty liczbą argumentów jest nieznany i zmiennymi argumentami są tego samego typu, lub mogą być przekazywane jako tego samego typu. Na przykład <xref:System.Console.WriteLine%2A> metoda zapewnia przeciążenia ogólnego przeznaczenia, który używa tablicy parametrów przyjąć dowolną liczbę <xref:System.Object> argumentów.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Zastąp powtarzające się argumenty tablicy parametrów.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Zawsze jest bezpiecznie pominąć ostrzeżenie od tej reguły; Ten projekt może jednak spowodować problemów z użytecznością.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia typu, który narusza tę regułę.  
  
 [!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]