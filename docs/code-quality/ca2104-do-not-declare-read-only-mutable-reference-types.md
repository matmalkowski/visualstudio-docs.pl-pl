---
title: "CA2104: Nie deklaruj typów referencyjnych tylko do odczytu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bbd12d09c95f1ec93c7232901270cfbece311693
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Nie deklaruj zmiennych typów referencyjnych tylko do odczytu
|||  
|-|-|  
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|  
|CheckId|CA2104|  
|Kategoria|Microsoft.Security|  
|Zmiana kluczowa|Bez podziału|  
  
## <a name="cause"></a>Przyczyna  
 Typ widoczny z zewnątrz zawiera widoczne na zewnątrz pole tylko do odczytu, które jest typu referencji zmiennej.  
  
## <a name="rule-description"></a>Opis reguły  
 Typ zmienny to typ, którego dane wystąpienia mogą być modyfikowane. <xref:System.Text.StringBuilder?displayProperty=fullName> Klasy jest przykładem modyfikowalnego typu referencyjnego. Zawiera on elementy członkowskie, które można zmienić wartości wystąpienia klasy. Na przykład typ referencyjny niezmienne <xref:System.String?displayProperty=fullName> klasy. Po utworzeniu wystąpienia, jego wartość nigdy nie można zmienić.  
  
 Modyfikator tylko do odczytu ([tylko do odczytu](/dotnet/csharp/language-reference/keywords/readonly) w języku C# [tylko do odczytu](/dotnet/visual-basic/language-reference/modifiers/readonly) w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], i [const](/cpp/cpp/const-cpp) w języku C++) na typ referencyjny pola (wskaźnik w C++) uniemożliwia pola zastąpione przez inne wystąpienie typu referencyjnego. Jednak modyfikator nie zapobiega dane wystąpienia pola są modyfikowane za pomocą typu odwołania.  
  
 Pola tablicy tylko do odczytu są wyjątkiem od tej reguły, ale zamiast tego spowodować naruszenie [CA2105: pola tablicy nie można odczytać tylko](../code-quality/ca2105-array-fields-should-not-be-read-only.md) reguły.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby rozwiązać naruszenie tej reguły, Usuń modyfikator tylko do odczytu lub, jeśli istotne zmiany są dopuszczalne, Zastąp pole niezmiennego typu.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli typ pola nie można modyfikować.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono deklaracji pola, która powoduje naruszenie tej reguły.  
  
 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]