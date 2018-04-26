---
title: 'CA2223: Elementy członkowskie powinny różnić się bardziej, nie tylko zwracanym typem'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MembersShouldDifferByMoreThanReturnType
- CA2223
helpviewer_keywords:
- CA2223
- MembersShouldDifferByMoreThanReturnType
ms.assetid: eb326d9f-50d9-48cb-84be-d41c84a8fe09
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5aaa7671f1aa110edd42897111e746e62eab8048
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ca2223-members-should-differ-by-more-than-return-type"></a>CA2223: Elementy członkowskie powinny różnić się bardziej, nie tylko zwracanym typem
|||
|-|-|
|TypeName|MembersShouldDifferByMoreThanReturnType|
|CheckId|CA2223|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Dwa publiczne lub chronione elementy członkowskie mają podpisy, które są identyczne z wyjątkiem zwracanego typu.

## <a name="rule-description"></a>Opis reguły
 Mimo że środowisko uruchomieniowe języka wspólnego zezwala na używanie typy zwracane w celu rozróżnienia identyczną elementów członkowskich, ta funkcja nie jest w specyfikacja języka wspólnego, ani nie jest typową funkcją języków programowania .NET. Gdy elementy członkowskie różnią się tylko typem zwracanym, deweloperów i narzędzia deweloperskie może nie poprawnie rozróżnia je.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, zmienić projekt elementów członkowskich są unikatowe tylko na podstawie ich nazwy i typy parametrów lub nie ujawniaj elementów członkowskich.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład w języku pośrednim firmy Microsoft (MSIL) zawiera typ, który narusza tę regułę. Należy zauważyć, że ta zasada nie można oznaczać naruszenie przy użyciu języka C# lub Visual Basic.

```

.namespace UsageLibrary
{
  .class public auto ansi beforefieldinit ReturnTypeTest
         extends [mscorlib]System.Object
  {
    .method public hidebysig instance int32
            AMethod(int32 x) cil managed
    {
      // Code size       6 (0x6)
      .maxstack  1
      .locals init (int32 V_0)
      IL_0000:  ldc.i4.0
      IL_0001:  stloc.0
      IL_0002:  br.s       IL_0004

      IL_0004:  ldloc.0
      IL_0005:  ret
    } // end of method ReturnTypeTest::AMethod

    .method public hidebysig instance string
            AMethod(int32 x) cil managed
    {
      // Code size       10 (0xa)
      .maxstack  1
      .locals init (string V_0)
      IL_0000:  ldstr      "test"
      IL_0005:  stloc.0
      IL_0006:  br.s       IL_0008

      IL_0008:  ldloc.0
      IL_0009:  ret
    } // end of method ReturnTypeTest::AMethod

    .method public hidebysig specialname rtspecialname
            instance void  .ctor() cil managed
    {
      // Code size       7 (0x7)
      .maxstack  1
      IL_0000:  ldarg.0
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
      IL_0006:  ret
    } // end of method ReturnTypeTest::.ctor

  } // end of class ReturnTypeTest

} // end of namespace UsageLibrary

```