---
title: 'CA1040: Unikaj pustych interfejsów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 26ba25038baf0d54c1705d4f4dd6c9b0cca9f856
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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