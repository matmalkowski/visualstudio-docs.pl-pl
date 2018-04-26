---
title: 'CA1016: Oznacz zestawy za pomocą AssemblyVersionAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3080b5a45f61010f322ed183a8b5a7c23390de33
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Oznacz zestawy za pomocą AssemblyVersionAttribute
|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Zestaw nie ma numeru wersji.

## <a name="rule-description"></a>Opis reguły
 Tożsamość zestawu składa się z następujących informacji:

-   Nazwa zestawu

-   Numer wersji

-   Kultury

-   Klucz publiczny (dla zestawów o silnej nazwie).

 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Używa numeru wersji do jednoznacznej identyfikacji zestawu i powiązanie typów w zestawach o silnej nazwie. Numer wersji jest używany razem z zasadami wersji i wydawcy. Domyślnie aplikacje są uruchamiane tylko z wersji zestawu, z którego zostały zbudowane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Dodaj numer wersji do zestawu przy użyciu <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> atrybutu. Zobacz poniższy przykład.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenia od tej reguły dla zestawów, które są używane przez osoby trzecie, lub w środowisku produkcyjnym.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono zestawu, który ma <xref:System.Reflection.AssemblyVersionAttribute> atrybut zastosowany.

 [!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]

## <a name="see-also"></a>Zobacz też
 [Przechowywanie wersji zestawu](/dotnet/framework/app-domains/assembly-versioning) [porady: Tworzenie zasad wydawcy](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)