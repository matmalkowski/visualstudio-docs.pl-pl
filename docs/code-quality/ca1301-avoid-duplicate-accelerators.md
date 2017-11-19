---
title: "CA1301: Należy unikać duplikowania akceleratorów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 13d2f36014ab15aea3148ab4175a89b77deb4846
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Należy unikać duplikowania akceleratorów
|||  
|-|-|  
|TypeName|AvoidDuplicateAccelerators|  
|CheckId|CA1301|  
|Kategoria|Microsoft.Globalization|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Rozszerzenie typu <xref:System.Windows.Forms.Control?displayProperty=fullName> i zawiera co najmniej dwa formantami najwyższego poziomu, które mają identyczne dostępu do kluczy, które są przechowywane w pliku zasobów.  
  
## <a name="rule-description"></a>Opis reguły  
 Klucz dostępu, znany również jako akcelerator, umożliwia dostęp z klawiatury do formantu za pomocą klawisza ALT. Kiedy wiele formantów ma zduplikowany klucz dostępu, jego zachowanie nie jest dobrze zdefiniowane. Użytkownik może nie umożliwiać dostęp do danego formantu przy użyciu klucza dostępu i kontroli innego niż ten, który ma może być włączone.  
  
 Bieżąca implementacja tej reguły ignoruje elementów menu. Jednak elementów menu na tym samym podmenu nie powinna mieć klucze dostępu identyczne.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, zdefiniuj dostępu unikatowy kluczy dla wszystkich kontrolek.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia minimalny formularz, który zawiera dwa formantów, które mają klucze dostępu identyczne. Klucze są przechowywane w pliku zasobu nie jest wyświetlany; jednak ich wartości są wyświetlane w komentarze limit `checkBox.Text` wierszy. Zachowanie duplikowania akceleratorów można zbadać przez wymianę `checkBox.Text` wiersze z ich odpowiedniki komentarze wychodzących. Jednak w takim przypadku przykładzie nie wygeneruje ostrzeżenie z reguły.  
  
 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [Zasoby w aplikacjach klasycznych](/dotnet/framework/resources/index)