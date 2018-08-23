---
title: 'CA2102: Przechwytuj wyjątki bez atrybutu CLSCompliant w ogólnych procedurach obsługi | Dokumentacja firmy Microsoft'
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
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 709afb1fbdada2f27377cb4531cbda8dba72237d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677452"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Przechwytuj wyjątki inne niż CLSCompliant w ogólnej obsłudze wyjątków
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA2102: Przechwytuj wyjątki bez atrybutu CLSCompliant w ogólnych procedurach obsługi](https://docs.microsoft.com/visualstudio/code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers).  
  
Element TypeName | CatchNonClsCompliantExceptionsInGeneralHandlers |  
| CheckId | CA2102 |  
| Kategoria | Microsoft.Security|  
| Zmiana powodująca niezgodność | Bez podziału |  
  
## <a name="cause"></a>Przyczyna  
 Element członkowski w zestawie, który nie jest oznaczony atrybutem <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> lub jest oznaczony jako `RuntimeCompatibility(WrapNonExceptionThrows = false)` zawiera blok catch obsługujący <xref:System.Exception?displayProperty=fullName> i nie zawiera bezpośrednio następującego ogólnego bloku catch. Ta zasada powoduje ignorowanie [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] zestawów.  
  
## <a name="rule-description"></a>Opis reguły  
 W bloku catch, który obsługuje <xref:System.Exception> przechwytuje wszystkie wyjątki zgodne Common Language Specification (CLS). Jednak nie przechwytuje wyjątków zgodne ze specyfikacją CLS. Niezgodny ze specyfikacją CLS zgodne wyjątki mogą zostać wygenerowane, z kodu macierzystego lub kodu zarządzanego, który został wygenerowany przez firmę Microsoft pośredniego (MSIL) języka asemblera. Należy zauważyć, że języka C# i [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kompilatory nie zezwalają na niezgodnych ze specyfikacją CLS zgodnych wyjątki zostanie wygenerowany i [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nie przechwytuje wyjątków zgodne ze specyfikacją CLS. Jeśli celem blok catch ma obsługiwać wszystkie wyjątki, należy użyć następującej składni bloku catch ogólne.  
  
-   C#: `catch {}`  
  
-   C++: `catch(...) {}` lub `catch(Object^) {}`  
  
 Wyjątek nieobsługiwany niezgodnych ze specyfikacją CLS staje się problem z zabezpieczeniami, usunięcie wcześniej dozwolone uprawnienia w bloku catch. Ponieważ wyjątki zgodne ze specyfikacją CLS nie są wychwytywane, złośliwy metodę, która zgłasza wyjątek niezgodny ze specyfikacją można uruchomić z podwyższonym poziomem uprawnień.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej zasady, gdy celem jest przechwytywać wszystkie wyjątki, Zastąp lub Dodaj ogólnego bloku catch lub oznaczyć zestaw `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Jeśli uprawnienia zostaną usunięte w bloku catch, zduplikowane funkcji w ogólne blok catch. Jeśli nie jest celem do obsługi wszystkich wyjątków, Zastąp blok catch, który obsługuje <xref:System.Exception> przy użyciu bloków catch, które obsługują typy określonego wyjątku.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli blok try nie zawiera żadnych instrukcji, które mogą generować wyjątek zgodne ze specyfikacją CLS. Ponieważ każdy kod macierzysty lub zarządzany może zgłosić wyjątek niezgodny ze specyfikacją, wymaga znajomości cały kod, który może być wykonywana w wszystkie ścieżki kodu wewnątrz bloku try. Zauważ, że wyjątki zgodne ze specyfikacją CLS nie zostaną zgłoszone przez środowisko uruchomieniowe języka wspólnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia klasę MSIL, które zgłasza wyjątek zgodne ze specyfikacją CLS.  
  
```  
.assembly ThrowNonClsCompliantException {}  
.class public auto ansi beforefieldinit ThrowsExceptions  
{  
   .method public hidebysig static void  
         ThrowNonClsException() cil managed  
   {  
      .maxstack  1  
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()  
      IL_0005:  throw  
   }  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia metodę, która zawiera blok catch ogólnego, który spełnia reguły.  
  
 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.CatchNonClsCompliantException/cs/FxCop.Security.CatchNonClsCompliantException.cs#1)]  
  
 Skompiluj następujący poprzednich przykładach.  
  
```  
ilasm /dll ThrowNonClsCompliantException.il  
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs  
```  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA1031: Nie przechwytuj ogólnych typów wyjątków](../code-quality/ca1031-do-not-catch-general-exception-types.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Wyjątki i obsługa wyjątków](http://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344)   
 [Ilasm.exe (asembler IL)](http://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f)   
 [Zastępowanie sprawdzania zabezpieczeń](http://msdn.microsoft.com/en-us/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [Niezależność od języka i składniki niezależne od języka](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



