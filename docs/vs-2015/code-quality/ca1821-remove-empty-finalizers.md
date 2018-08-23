---
title: 'CA1821: Usuwaj puste finalizatory | Dokumentacja firmy Microsoft'
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
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: efd7a2675326780c8e66daf49390587a7f85db3a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42696752"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Usuń puste finalizatory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1821: usuwaj puste finalizatory](https://docs.microsoft.com/visualstudio/code-quality/ca1821-remove-empty-finalizers).  
  
Element TypeName | RemoveEmptyFinalizers |  
| CheckId | CA1821 |  
| Kategoria | Microsoft.Performance|  
| Zmiana powodująca niezgodność | Bez podziału |  
  
## <a name="cause"></a>Przyczyna  
 Typ implementuje finalizatora, który jest pusty, wywołuje tylko finalizator typu podstawowego lub wywołuje tylko warunkowo emitowane metody.  
  
## <a name="rule-description"></a>Opis reguły  
 Jeśli to tylko możliwe, należy unikać finalizatorów ze względu na dodatkowe obciążenie, które bierze udział w śledzeniu okresu istnienia obiektu. Gromadzi informacje o obiekcie, kiedy moduł odśmiecania pamięci uruchomi finalizatora. Oznacza to, czy dwie kolekcje będą wymagane do zbierania obiektu. Pusty finalizator powoduje to dodatkowe obciążenie, bez żadnych korzyści.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Usuń puste finalizatory. Jeśli finalizator jest wymagana do debugowania, ujmij całą finalizator w `#if DEBUG / #endif` dyrektywy.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj wiadomości od tej reguły. Nie można wstrzymać finalizację zmniejsza wydajność i oferuje nie korzyści.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano pusty finalizator, który powinien zostać usunięty, finalizator, powinien być sporządzony we `#if DEBUG / #endif` dyrektywy i finalizator, który używa `#if DEBUG / #endif` dyrektywy poprawnie.  
  
 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]



