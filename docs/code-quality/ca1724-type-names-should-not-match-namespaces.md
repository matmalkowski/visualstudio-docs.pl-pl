---
title: "CA1724: Nazwy typów nie powinny odpowiadać nazwom | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f138958ce2dc83b7d258fbdb16986841e92d3484
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Nazwy typów nie powinny odpowiadać nazwom pól
|||  
|-|-|  
|TypeName|TypeNamesShouldNotMatchNamespaces|  
|CheckId|CA1724|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Nazwa typu odpowiada [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] nazwy przestrzeni nazw w porównania bez uwzględniania wielkości liter.  
  
## <a name="rule-description"></a>Opis reguły  
 Nazwy typów nie powinny odpowiadać nazwy przestrzeni nazw, które są zdefiniowane w [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] biblioteki klas. Naruszenie tej zasady może zmniejszyć użyteczność biblioteki.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Wybierz nazwę typu, który nie jest zgodna z nazwą elementu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] biblioteki klas w przestrzeni nazw.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 W nowych wdrożeniach, Brak znanego scenariusze wystąpić, gdy należy pominąć ostrzeżenie od tej reguły. Aby pominąć to ostrzeżenie, należy rozważyć, jak użytkownicy biblioteki mogą być pomylone przez tej nazwy. Dla wysyłania bibliotek, może być konieczne pominąć ostrzeżenie od tej reguły.