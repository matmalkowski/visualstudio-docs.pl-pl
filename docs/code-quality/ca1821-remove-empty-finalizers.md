---
title: "CA1821: Usuń puste finalizatory | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 98aebdcc889cdd3bd2bbe124b00a572e066b0e4a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Usuń puste finalizatory
|||  
|-|-|  
|TypeName|RemoveEmptyFinalizers|  
|CheckId|CA1821|  
|Kategoria|Microsoft.Performance|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Typ implementuje finalizator, który jest pusty, wymaga tylko finalizator typu podstawowego lub wywołuje tylko warunkowo emitowane metody.  
  
## <a name="rule-description"></a>Opis reguły  
 Jeśli to tylko możliwe, należy unikać finalizatorów ze względu na dodatkowe obciążenie, które bierze udział w śledzeniu okresu istnienia obiektu. Moduł zbierający elementy bezużyteczne uruchomi finalizatora przed zbiera obiektu. Oznacza to, że dwie kolekcje będzie wymagany do zbierania obiektu. Pusty finalizator wiąże się to dodany narzut bez żadnych korzyści.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Usuń finalizator puste. Jeśli finalizator jest wymagana do debugowania, ujmij całą finalizator w `#if DEBUG / #endif` dyrektywy.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj wiadomości z tej reguły. Nie można wstrzymać finalizację spadku wydajności i zapewnia nie korzyści.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono pusty finalizator, który powinien zostać usunięty, finalizatora, który powinien być ujęty w `#if DEBUG / #endif` dyrektywy i finalizatora, który używa `#if DEBUG / #endif` dyrektywy poprawnie.  
  
 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]