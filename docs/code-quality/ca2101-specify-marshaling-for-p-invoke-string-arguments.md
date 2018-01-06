---
title: "CA2101: Należy określić marshaling dla argumentów ciągu P Invoke | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 15191983d08bfc99848e4a16c0059c075b234bb3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: Należy określić marshaling dla argumentów typu string P/Invoke
|||  
|-|-|  
|TypeName|SpecifyMarshalingForPInvokeStringArguments|  
|CheckId|CA2101|  
|Kategoria|Microsoft.Globalization|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Wywołanie platformy elementu członkowskiego umożliwia częściowo zaufanych wywołań ma parametr typu string, a nie jawnie kierować ten ciąg.  
  
## <a name="rule-description"></a>Opis reguły  
 Podczas konwertowania z Unicode na ANSI, jest to możliwe, że nie wszystkie znaki Unicode może być reprezentowany w określonej strony kodowej ANSI. *Mapowanie najlepszego dopasowania* próbuje rozwiązać ten problem, zastępując znak znaku, który nie może być przedstawiony. Używanie tej funkcji może spowodować potencjalne luki w zabezpieczeniach, ponieważ nie można kontrolować znak, który zostanie wybrany. Na przykład złośliwy kod celowo można utworzyć ciągu Unicode, który zawiera znaki, które nie znajdują się na stronie określonego kodu, które są konwertowane na znaki specjalne systemu plików, takich jak ".." lub "/". Należy pamiętać, że kontrole zabezpieczeń dla znaków specjalnych często występują przed jest przekonwertowanie ciągu na ANSI.  
  
 Mapowanie najlepszego dopasowania jest ustawieniem domyślnym dla konwersji niezarządzanego, WChar do MBajtów. Chyba że jawnie wyłącz mapowanie najlepszego dopasowania, kod może zawierać luki w zabezpieczeniach kończona z powodu tego błędu.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, jawnie organizowania danych typu ciąg.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono metodę, która narusza tę regułę, a następnie pokazano, jak rozwiązać naruszenie.  
  
 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]