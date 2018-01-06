---
title: "CA1040: Unikaj pustych interfejsów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1b2dd61f70328ed4aa8ca08c518cebf8d6abbedb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Unikaj pustych interfejsów
|||  
|-|-|  
|TypeName|AvoidEmptyInterfaces|  
|CheckId|CA1040|  
|Kategoria|Microsoft.Design|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Interfejs nie deklaruje żadnych elementów członkowskich lub implementować co najmniej dwa interfejsy.  
  
## <a name="rule-description"></a>Opis reguły  
 Interfejsy definiują elementy członkowskie, które zapewniają zachowanie lub użycie kontraktu. Funkcjonalność opisana przez interfejs może zostać przyjęta przez dowolny typ, niezależnie od tego, gdzie ten typ się pojawia w hierarchii dziedziczenia. Typ implementuje interfejs, dostarczając implementacje dla jego elementów członkowskich. Pustego interfejsu nie definiuje żadnych elementów członkowskich. W związku z tym nie definiuje kontraktu, który może być zaimplementowany.  
  
 Jeśli projekt zawiera pusty powinny implementować interfejsów, które typy, prawdopodobnie używany jako znacznik lub do identyfikowania grupy typu interfejsu. Jeśli ten identyfikator będzie występować w czasie wykonywania, prawidłowy sposób, w tym celu jest użycie atrybutu niestandardowego. Użyj obecności lub braku atrybutu lub właściwości atrybutu, aby określić typy docelowej. Jeśli identyfikacji musi przypadać w czasie kompilacji, a następnie można użyć pustego interfejsu.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Usuń interfejs lub Dodaj do niej członków. Jeśli pustego interfejsu jest używana jako etykieta zestaw typów, Zastąp interfejs z atrybutem niestandardowym.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest to bezpieczne Pomiń ostrzeżenie od tej reguły, gdy ten interfejs jest używany do identyfikowania zestaw typów w czasie kompilacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono pustego interfejsu.  
  
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]