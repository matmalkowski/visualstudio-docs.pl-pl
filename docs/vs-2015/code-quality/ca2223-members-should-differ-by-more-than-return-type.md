---
title: 'CA2223: Składniki powinny różnić się tylko zwracanym typem | Dokumentacja firmy Microsoft'
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
- MembersShouldDifferByMoreThanReturnType
- CA2223
helpviewer_keywords:
- CA2223
- MembersShouldDifferByMoreThanReturnType
ms.assetid: eb326d9f-50d9-48cb-84be-d41c84a8fe09
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 37758f49e7dcaa7e41e873dd617e041a97c9e61e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42629618"
---
# <a name="ca2223-members-should-differ-by-more-than-return-type"></a>CA2223: Elementy członkowskie powinny różnić się bardziej, nie tylko zwracanym typem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2223: składniki powinny różnić się tylko zwracanym typem](https://docs.microsoft.com/visualstudio/code-quality/ca2223-members-should-differ-by-more-than-return-type).  
  
Element TypeName | MembersShouldDifferByMoreThanReturnType |  
| CheckId | CA2223 |  
| Kategoria | Microsoft.Usage|  
| Zmiana powodująca niezgodność | Przerwanie |  
  
## <a name="cause"></a>Przyczyna  
 Dwa publiczne lub chronione elementy członkowskie są opatrzone sygnaturami, które są identyczne, z wyjątkiem typu zwracanego.  
  
## <a name="rule-description"></a>Opis reguły  
 Chociaż środowisko uruchomieniowe języka wspólnego pozwala na używanie typów zwracanych do rozróżnienia między inaczej identycznymi członkami, funkcja ta nie jest specyfikacja Common Language Specification, ani nie jest wspólną cechą języków programowania .NET. Gdy członkowie różnią się tylko typem zwracanym, deweloperów i narzędzia programistyczne mogą nie poprawnie ich rozróżnienie.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, zmiany projektu elementów członkowskich, tak, że są unikatowe, tylko na podstawie jego nazwy i typy parametrów ani nie ujawniaj elementów członkowskich.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład w języka Microsoft intermediate language (MSIL), zawiera typ, który narusza tę regułę. Należy zauważyć, że ta zasada nie naruszył przy użyciu języka C# lub Visual Basic .NET.  
  
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



