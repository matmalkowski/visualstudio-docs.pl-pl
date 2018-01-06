---
title: "CA2208: Wystąpienia wyjątków argumentów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 78d510d966f2467123105ad777d61c99ad11e99a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Utwórz poprawne wystąpienia wyjątków argumentów
|||  
|-|-|  
|TypeName|InstantiateArgumentExceptionsCorrectly|  
|CheckId|CA2208|  
|Kategoria|Microsoft.Usage|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Możliwe przyczyny: w następujących sytuacjach:  
  
-   Wywołanie domyślnego (bezparametrowego) konstruktora typu wyjątku, który jest lub pochodzi z <xref:System.ArgumentException>.  
  
-   Argument niepoprawny ciąg jest przekazywany do konstruktora sparametryzowane typu wyjątku, który jest lub pochodzi z <xref:System.ArgumentException>.  
  
## <a name="rule-description"></a>Opis reguły  
 Zamiast wywoływania domyślnego konstruktora, wywoływanie jednego z przeciążeń konstruktora, które umożliwia bardziej zrozumiałej komunikat o wyjątku mają zostać podane. Komunikat o wyjątku powinien celem dewelopera i wyjaśniają warunek błędu i jak rozwiązać lub uniknąć wyjątek.  
  
 Podpisy jeden i dwa parametry konstruktorów <xref:System.ArgumentException> i jego typów pochodnych nie są spójne w odniesieniu do `message` i `paramName` parametrów. Upewnij się, że te konstruktory są nazywane z argumentami poprawny ciąg. Podpisy są następujące:  
  
 <xref:System.ArgumentException>(ciąg `message`)  
  
 <xref:System.ArgumentException>(ciąg `message`, ciąg `paramName`)  
  
 <xref:System.ArgumentNullException>(ciąg `paramName`)  
  
 <xref:System.ArgumentNullException>(ciąg `paramName`, ciąg `message`)  
  
 <xref:System.ArgumentOutOfRangeException>(ciąg `paramName`)  
  
 <xref:System.ArgumentOutOfRangeException>(ciąg `paramName`, ciąg `message`)  
  
 <xref:System.DuplicateWaitObjectException>(ciąg `parameterName`)  
  
 <xref:System.DuplicateWaitObjectException>(ciąg `parameterName`, ciąg `message`)  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Ustalenie naruszenie tej reguły, wywołać konstruktora, który pobiera komunikat i/lub nazwę parametru i upewnij się, że argumenty są odpowiednie dla typu <xref:System.ArgumentException> wywoływane.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej zasady tylko w przypadku, gdy sparametryzowanym konstruktorze została wywołana z argumentami poprawny ciąg.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono niepoprawnie tworzącym wystąpienie typu argumentnullexception — konstruktora.  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rozwiązuje powyżej naruszenie przełączając argumentów konstruktora.  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]