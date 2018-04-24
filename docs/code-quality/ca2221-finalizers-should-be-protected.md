---
title: 'CA2221: Finalizatory powinny być chronione'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2221
- FinalizersShouldBeProtected
helpviewer_keywords:
- FinalizersShouldBeProtected
- CA2221
ms.assetid: bda03aee-4cce-45d3-907d-17f4ee030acc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf4ee1aef9ef31dccad5a9728244aeaf79f9e6a4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="ca2221-finalizers-should-be-protected"></a>CA2221: Finalizatory powinny być chronione
|||
|-|-|
|TypeName|FinalizersShouldBeProtected|
|CheckId|CA2221|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Publiczny typ implementuje finalizator, która nie określa rodziny dostępu (chronione).

## <a name="rule-description"></a>Opis reguły
 Finalizatory muszą korzystać z modyfikatora dostępu „family”. Ta reguła jest wymuszone przez Kompilatory języka C#, Visual Basic i Visual C++.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby usunąć naruszenie tej reguły, zmienić finalizator była dostępna rodziny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Nie można oznaczać naruszenie tej reguły w dowolnym języku .NET wysokiego poziomu; można naruszone, jeśli piszesz język pośredni firmy Microsoft.

```
// =============== CLASS MEMBERS DECLARATION ===================
//   note that class flags, 'extends' and 'implements' clauses
//          are provided here for information only

.namespace UsageLibrary
{
  .class public auto ansi beforefieldinit FinalizeMethodNotProtected
         extends [mscorlib]System.Object
  {
    .method public hidebysig instance void
            Finalize() cil managed
    {

      // Code size       1 (0x1)
      .maxstack  0
      IL_0000:  ret
    } // end of method FinalizeMethodNotProtected::Finalize

    .method public hidebysig specialname rtspecialname
            instance void  .ctor() cil managed
    {
      // Code size       7 (0x7)
      .maxstack  1
      IL_0000:  ldarg.0
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
      IL_0006:  ret
    } // end of method FinalizeMethodNotProtected::.ctor

  } // end of class FinalizeMethodNotProtected
} // end of namespace
```

## <a name="see-also"></a>Zobacz też
 [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)