---
title: 'CA1025: Zastąp powtarzające się argumenty tablicą params | Dokumentacja firmy Microsoft'
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
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e51f92c46d3d8ac75e6de7b6d5b8b505c8b25503
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681836"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Zastąp powtarzające się argumenty tabelą parametrów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1025: Zastąp powtarzające się argumenty tablicą params](https://docs.microsoft.com/visualstudio/code-quality/ca1025-replace-repetitive-arguments-with-params-array).  
  
Element TypeName | ReplaceRepetitiveArgumentsWithParamsArray |  
| CheckId | CA1025 |  
| Kategoria | Microsoft.Design|  
| Zmiana powodująca niezgodność | Bez podziału |  
  
## <a name="cause"></a>Przyczyna  
 Metoda publiczna lub chroniona w typie publicznym ma więcej niż trzy parametry, a jego trzy ostatnie parametry są tego samego typu.  
  
## <a name="rule-description"></a>Opis reguły  
 Użyj tablicy parametrów zamiast powtarzających się argumentów, jeśli dokładna liczba argumentów jest nieznany i argumenty zmiennych są tego samego typu lub mogą być przekazywane jako tego samego typu. Na przykład <xref:System.Console.WriteLine%2A> metoda zapewnia ogólnego przeznaczenia przeciążenia, które używa tablicy parametrów, aby zaakceptować dowolną liczbę <xref:System.Object> argumentów.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, Zastąp powtarzające się argumenty tablicą parametrów.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest zawsze bezpieczne ostrzeżenia od tej reguły; Jednak ten projekt może spowodować problemy z użytecznością.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje typ, który narusza tę regułę.  
  
 [!code-csharp[FxCop.Design.RepeatArgs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RepeatArgs/cs/FxCop.Design.RepeatArgs.cs#1)]



